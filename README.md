# geodatafr.github.io


## Setup

```bash
python3 -m venv venv-mkdocs
source venv-mkdocs/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

## Deploy new version

Build the site and push it to the branch `gh-pages`:
```bash
mkdocs gh-deploy
```

Wait a bit until github [action](https://github.com/geodatafr/geodatafr.github.io/actions) completes.
