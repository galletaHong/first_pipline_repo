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
```yml
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


## Put `README.md`
Try to put the repository `README.md` file in below.
* First, install the usefull **mkdocs material**
```
# use pip
$　pip install mkdocs-material
```
* Set **material theme** in your `mkdocs.yml` 
```
theme:
  name: material
```
* Enable the **[Snippets](https://facelessuser.github.io/pymdown-extensions/extensions/snippets/) extension** in your `mkdocs.yml` 
```
markdown_extensions:
  - pymdownx.snippets
```
* Use the instruction in the `your_file.md` :
> --8<--  
> ./README.md  
> --8<--

It will shown as :