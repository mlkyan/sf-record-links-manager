## Unlocked Packaging Commands

### 1 Create a Package
```sh
sf package create -n ebc-lib-template -t Unlocked -d "Framework for libraries" -r force-app/lib-template --no-namespace -v EBCLibs
```

### 2 View version list
````sh
sf package version list -p ebc-lib-template -v EBCLibs
````

### 3 Create new version
```sh
sf package version create -p ebc-lib-template -k DvE3GT0GuJd -w 10 -c -v EBCLibs
```

### 4 Promote version
```sh
sf package version promote -p ebc-lib-template@1.1.0-1 -v EBCLibs
```
