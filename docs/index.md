# My First MkDocs
This repository is form [Github](https://github.com/galletaHong/first_pipline_repo)

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

---
# **↓ `README.md`**
--8<--
./README.md
--8<--