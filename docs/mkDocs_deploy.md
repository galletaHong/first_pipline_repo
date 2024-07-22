# mkDocs
## Install
1. The [Installation of mkDocs](https://www.mkdocs.org/getting-started/)
```
$ pip install mkdocs
```
After installation, you can [getting Started with MkDocs](https://www.mkdocs.org/getting-started/) :
```
mkdocs new my-project
cd my-project
```
## Deploy on Github pages
1. Add `.github/workflows/docs.yml` with below code in your repository :

```yaml title="docs.yml"
name: docs 
on:
  push:
    branches:
    - main
  pull_request:
    branches:
    - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:

      # # https://github.com/marketplace/actions/deploy-mkdocs
      # - uses: actions/checkout@v1
      # - uses: mhausenblas/mkdocs-deploy-gh-pages@master
      #   env:
      #     GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

      # https://squidfunk.github.io/mkdocs-material/publishing-your-site/?h=github#with-github-actions
      - uses: actions/checkout@v2
      - uses: actions/setup-python@v2
        with:
          python-version: 3.x
      - run: pip install -U git+https://github.com/mkdocs/mkdocs.git#egg=mkdocs
      - run: pip install mkdocs-material
      - run: mkdocs gh-deploy --force
      - run: mkdocs --version
```

2. Push all your documentation on Github
3. Create the `site\` foldfer

```
$ mkdocs build
```

4. Site files get [deployed](https://www.mkdocs.org/user-guide/deploying-your-docs/) to a branch
Use the following command :

```
$ mkdocs gh-deploy
```

MkDocs will build your docs and use the **ghp-import** tool to commit them to the `gh-pages` branch and push the `gh-pages` branch to GitHub.
5. Enable Github Pages 
Go your repository Github website, and enable Repo by `Settings > Pages`.
In the section `Build and deployment`, set **Source** to `Deploy from the brance`.
In the next section `Branch`, set `gh-pages` `/root` and click `save`.

> If you want to modify your file, only use the **step 2**, **3** and **4**.

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