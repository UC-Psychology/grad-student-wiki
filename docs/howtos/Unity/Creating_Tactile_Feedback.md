
# Creating Tactile Feedback in VR

When you're creating an embodied task in VR, sometimes it is useful to be able to have a participant experience feedback from their actions. At times, unity has built in haptic responses to contact between *colliders*, but other times you may want to trigger this response for yourself. 

Perhaps a participant makes an error and you want to initiate a pulse of vibration in response. Here is some steps to how you may go about this!

## Creating the script:

This demo ***assumes you already have*** the controllers integrated into the environment. If you have trouble with this, please look to the other tutorial for adding hands.

----Add details towards adding the script to the objects----

## Initialising the script:

Basic *packages* will need to be input for this script. Most of these should appear regularly on creating a script in unity. 

    using System.Collections;
    using.System.Collections.Generic;
    using UnityEngine;
    using Valve.VR;

the line `using Valve.VR` is not one of the automatic *packages* that are set up, rather it is a package that lets you access code functions that are specific to valve hardware, including the **Vive** headsets, controllers, and the ***Valve Index Controllers***. This code will be built for ***Valve Index Controllers*** but should be cross functional with other Valve products. 

## Setting up the environment

After initialising the packages you will be using, you will want to title your script and bring in any relevant objects, variables, or features that may be relevant to the code you are executing.

### Titling

The title of your script will ***need*** to match the title of the document. 

    public class ControllerVibration : MonoBehavior 
    {

In this case, as I have labelled this Behavior script as "ControllerVibration", the document should also be named "ControllerVibration.cs"

***NOTE***: While I am separating the code, there will be open sections using the {} parenthicals. These will need to be closed further in. 

### Relevant features

here you will need to grant the code access to any features that you may be trying to access or build. I tend to create these as *public* objects so that they are accessible to other scripts and/or visible in the Unity Editor. If there is a variable you will not need to edit frequently or access in another location, you may instead want to create these as *private*.

    public SteamVR_Action_Vibration hapticAction;
    public float freq;
    public float amp;

Here, you are gaining access to steamVRs inbuilt haptics package as well as setting values that you may use to control the intensity of vibrations. 

## Triggering a Vibration

### Continuous Vibration

Use of `void Update()` allows you to create behaviors that are triggered on each frame the enviornment is live. In Unity, this will typically trigger about 60 times per second depending on the complexity of the scene. (if you are intent on standardising this,look into `void FixedUpdate()` ).

If we just want the controller to vibrate continuously, we can add our call to vibrate here. For this, we can use the `Pulse()` function. 

    void Update()
    {
        Pulse(1, freq, amp, SteamVR_Input_Sources.LeftHand);
    }

This code will take the your values for the fequency (`freq`) and amplitude (`amp`), and tell the controller to vibrate for 1 frame at those specifications. As this is called in an `Update()`, this will then repeat every frame. This provides the `Pulse()` fucntion the information it needs to operate, but we have not yet set up what this function does. We will come back to this later.

### Vibration on an Event

If we instead want our controller to vibrate under specific circumstances, we can specify when exactly this `Pulse()` function is called. Consider a situation where I want to vibrate the controller every time the hand touches an object tagged as an *errorObject*. (NOTE: Tags can be applied to objects in the unity editor.)

Instead of using the `Update()` function, I will use a `OnCollisionEnter()` function to look for instances of this contact, and then use that to trigger the `Pulse()`. For this I will need to make use of an `if` statement 

    void OnCollisionEnter(Collision coll)
    {
        if (coll.gameObject.tag == "errorObject")
        {
            Pulse(1, freq, amp, SteamVR_Input_Sources.LeftHand);
        }
    }

As you can see, we are still calling the same function, but instead of using every frame to call the `Pulse` function, we are calling it in any instance that the object this script is attached to (the hands) make contact with a `gameObject` with the `tag`: `errorObject`. 


## Setting up the Pulse()

Finally, we need to tell the `Pulse()` function what to do when it is called for. For this, we can set up a `private` fucntion, as we should not really try to access this externally to the code. This function should take all of the relevant inputs that we have specified above in our pulse function (how long, what frequency, what strength, what object) and how to execute it. Thankfully, the `SteamVR_Action_Vibration` set that we brought in earlier has tools we can levarage.

    private void Pulse(float duration, float frequency, float amplitude, SteamVR_Input_Sources source)
    {
        hapticAction.Execute(0, duration, frequency, amplitide, source)
    }

Here, we are now telling unity that, when the `Pulse()` function is called, to `Execute` a vibration at the `duration`, `frequency`, and `amplitude` specified in the call, and to execute this on the `source` or object specified. 

## Finalising

Whichever way that you have called the function, be sure to close out your code from the titling section by including a final closing parenthetical, to ensure the whole behavior is contained. 

    }

 This is a basic way to create a haptic response, and you have freedom to controll the structure and duration of vibrations. 




-------------------------------------------------------
*Contributed by Dalton Cooper*