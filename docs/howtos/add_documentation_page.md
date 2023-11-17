# Add a Page to the Wiki

To create a new page on the wiki, follow these steps:

1. Open the `docs` folder in the VS Code (or your preferred IDE).
2. Think about where you want your new page to be located in the wiki. For example, if you want to add a page about how to use Git, you might want to add it to the `docs/howtos` folder.
3. Create a new Markdown file in the appropriate folder.
4. Add content to your new page using Markdown syntax.
5. Add a link to your new page in the `mkdocs.yml` file, this will be found in the `nav` section of the file. The navigation section might look like this:
```yaml

nav: 
  - Home: 
    - index.md
    - Get Started Contributing: contributing.md
  - How To's: 
    - howtos/index.md
```

    To add your page to the How To's section, you would add a single line of code the the `mkdocs.yml` file, like this:
```yaml
    - Home:
        - index.md
        - Get Started Contributing: contributing.md
    - How To's:
        - howtos/index.md
        - Use Git: howtos/git.md
```

6. Save your changes and commit them to the repository.
7. Push your changes to GitHub. 
8. When the page is ready to be added to the Wiki, create a pull request (PR) to merge your changes into the main branch! Your PR will be reviewed by a member of the Wiki team and merged into the main branch if it meets the Wiki's standards.