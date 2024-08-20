# [mkDocs](https://www.mkdocs.org/)
## Install
1. The [Installation of mkDocs](https://www.mkdocs.org/getting-started/)
```
$ pip install mkdocs
```
After installation, check the version you installed :
```
$ mkdocs --version
```
Next you can [getting Started with MkDocs](https://www.mkdocs.org/getting-started/) :
```
$ mkdocs new my-project
$ cd my-project
```
Following command can be used to preview documentation on localhost.
```
$ mkdocs serve
```
Open up [***http://127.0.0.1:8000/***](http://127.0.0.1:8000/) in your browser.
After this, while you save your changes.
The browser will auto-reload and updated documentation immediately.

## Deploy on Github pages
1. Push all your documentation on Github
2. Create the `site\` foldfer
    ```
    $ mkdocs build
    ```

     > If you're using source code control such as `git`, you can add `"site/"` into the `.gitignore`, it will let the `site\` folder be ignored from repository.

     > ```yaml title=".gitignore"
     > "site/"
     > ```

     > Or use the following instruction 
     > ```
     > $ echo "site/" >> .gitignore
     > ```

3. Site files get [deployed](https://www.mkdocs.org/user-guide/deploying-your-docs/) to a branch
Use the following command :
    ```
    $ mkdocs gh-deploy
    ```
    MkDocs will build your docs and use the **ghp-import** tool to commit them to the `gh-pages` branch and push the `gh-pages` branch to GitHub.

4. Enable Github Pages 
    1. Go your repository Github website.
    2. Enable Repo by `Settings > Pages`.
    3. In the section `Build and deployment`, set **Source** to `Deploy from the brance`.
    4. In the next section `Branch`, set `gh-pages` `/root` and click `save`.

> After the first deploy, if you just want to modify your file, only use the **step 1**, **2** and **3**.

# [mkdocs material](https://squidfunk.github.io/mkdocs-material/)
## [Installation](https://squidfunk.github.io/mkdocs-material/getting-started/)
* Use pip
```
$　pip install mkdocs-material
```
* Set **material theme** in your `mkdocs.yml` 
```yaml title="mkdocs.yml"
theme:
  name: material
```

## Put `README.md` in page directly
Try to put the repository `README.md` file in below.

* Enable the **[Snippets](https://facelessuser.github.io/pymdown-extensions/extensions/snippets/) extension** in your `mkdocs.yml` 
```yaml title="mkdocs.yml"
markdown_extensions:
  - pymdownx.snippets
```
* Use the instruction in the `your_file.md` :
> --8<--  
> ./README.md  
> --8<--

## [Codeblock](https://squidfunk.github.io/mkdocs-material/reference/code-blocks/) 
### Configuration
Add the following lines to `mkdocs.yml`: <br>

```yaml title="mkdocs.yml"
markdown_extensions:
  - pymdownx.highlight:
      anchor_linenums: true
      line_spans: __span
      pygments_lang_class: true
  - pymdownx.inlinehilite
  - pymdownx.snippets
  - pymdownx.superfences
```
### Code copy button
* Add the following to `mkdocs.yml` to enable them globally :

```yaml title="mkdocs.yml"
theme:
  features:
    - content.code.copy
    - content.code.annotate 
```
## Other [Design implementation](https://squidfunk.github.io/mkdocs-material/setup/changing-the-colors/)
Also you can use Material to design some style.<br>
like some colors, fonts, logo and so on.