# AM Browser Document Online Help

Build AM Browser document by mkdocs

### Prerequisite

- Install git
- Install mkdocs from `http://www.mkdocs.org/`

### Build

Mkdocs can generate static html pages in `site` folder: 

```
mkdocs build
```
Or overwrite existing `site` folder
```
mkdocs build --clean
```

### Test

Mkdocs supports start local web server to preview document pages:

```
mkdocs serve
```

### Deploy

Mkdocs supports build static html pages then deploy/push github pages automatically in origin **gh-pages** branch.

```
mkdocs gh-deploy
```

> Need **manually** delete remote branch `gh-pages` if exist