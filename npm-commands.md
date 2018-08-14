# 1. npm -v
Check the version of npm itself.
```shell
npm -v
```

# 2. npm view
Show all details of a package on the registry.
```shell
#show cordova details
npm view cordova
#show cordova 7.1.0 details
npm view cordova@7.1.0
#show latest version available
npm view cordova version
```

# 3. npm list
Check package list
```shell
#List all packages installed your current workspace
npm list
#List all packages installed global
npm list -g
npm list -g --depth=0 
```
