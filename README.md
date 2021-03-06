# Resolving-GVfs
```
MakeRecipe "GVFS" "1.48.1" "https://gitlab.gnome.org/GNOME/gvfs/-/archive/master/gvfs-master.tar.bz2"

MakeRecipe "GSettings-Desktop-Schemas" "41" "https://gitlab.gnome.org/GNOME/gsettings-desktop-schemas/-/archive/master/gsettings-desktop-schemas-master.tar.bz2"
Compile GSettings-Desktop-Schemas "41"
Compile "GVFS" "1.48.1"
```

https://github.com/gobolinux/Recipes/blob/effe66610cad8f33b66634a9e3656a278a567e0b/VTE/0.60.3/Recipe#L10

https://gitlab.gnome.org/GNOME/gvfs/-/blob/master/meson_options.txt#L1

https://github.com/GNOME/gvfs/blob/master/meson.build#L273



```
#Compile Gcr "3.12.0"
#CreatePackage Gcr
InstallPackage "https://github.com/vaido-world/Resolving-GVfs/raw/main/Gcr/Gcr--3.12.0--x86_64.tar.bz2"
InstallPackage "https://gobolinux.org/packages/016/Python--2.7.12-r1--x86_64.tar.bz2"
Compile Polkit
```

# Next day Revision
```
Compile "anything"
InstallPackage --same "remove" "https://github.com/vaido-world/resolving-util-linux/raw/main/Util-Linux--2.35.1--x86_64.tar.bz2"

InstallPackage "https://gobolinux.org/packages/017/Fuse--2.9.7--x86_64.tar.bz2"
InstallPackage "https://gobolinux.org/packages/017/UnionFS-Fuse--2.1--x86_64.tar.bz2"

InstallPackage "https://github.com/vaido-world/Resolving-GLib/raw/main/GLib--2.68.4--x86_64.tar.bz2"

## GVfs Dependencies
#MakeRecipe "GSettings-Desktop-Schemas" "41" "https://gitlab.gnome.org/GNOME/gsettings-desktop-schemas/-/archive/master/gsettings-desktop-schemas-master.tar.bz2"
#Compile GSettings-Desktop-Schemas "41"
InstallPackage "https://github.com/vaido-world/Resolving-GLib/raw/main/GSettings-Desktop-Schemas/GSettings-Desktop-Schemas--41--x86_64.tar.bz2"

Compile Gcr "3.12.0"
InstallPackage "https://gobolinux.org/packages/016/Python--2.7.12-r1--x86_64.tar.bz2"
InstallPackage "https://gobolinux.org/packages/016/MozJS--17.0.0-r2--x86_64.tar.bz2"
#InstallPackage "https://gobolinux.org/packages/016/Polkit--0.112-r3--x86_64.tar.bz2"
Compile Polkit
CA
```

```

PrepareProgram: Preparing...
PrepareProgram: configure failed.
Compile: MozJS 59.0a1.0 - Configuration failed.

```

## MozJS
https://github.com/gobolinux/Recipes/tree/master/MozJS  
After Making a recipe, it is needed to add the `/js/src` to the dir 
```
add dir='mozjs17.0.0/js/src'
```


## MozJS 
https://archive.mozilla.org/pub/spidermonkey/releases/



```


InstallPackage "https://gobolinux.org/packages/016/Python--2.7.12-r1--x86_64.tar.bz2"
echo '\n' | MakeRecipe "MozJS" "24.2.0" "http://ftp.mozilla.org/pub/js/mozjs-24.2.0.tar.bz2"
Compile "MozJS" "24.2.0"
```


More versions: https://ftp.osuosl.org/pub/blfs/conglomeration/mozjs/


https://blog.actorsfit.com/a?ID=00600-aee2ad8b-cb98-4e73-a6bc-8c5ff6ef78dc

http://134.100.28.207/files/src/spidermonkey/

https://www.wenjiangs.com/wiki/en-US/docs/Mozilla/Projects/SpiderMonkey/Getting_SpiderMonkey_source_code


https://bugzilla.mozilla.org/show_bug.cgi?id=1588340

```
Compile "nothin"
InstallPackage https://gobolinux.org/packages/017/Fuse--2.9.7--x86_64.tar.bz2
InstallPackage https://gobolinux.org/packages/017/UnionFS-Fuse--2.1--x86_64.tar.bz2
InstallPackage "https://gobolinux.org/packages/016/Python--2.7.12-r1--x86_64.tar.bz2"
Compile Zip 3.0
echo '\n' | MakeRecipe MozJS "59.0a1.0" "http://ftp.mozilla.org/pub/spidermonkey/prereleases/59/pre1/mozjs-59.0a1.0.tar.bz2"
## Needs adding '-' symbol in the dir 
nano /Data/Compile/Recipes/MozJS/59.0a1.0/Recipe
Compile "MozJS" "59.0a1.0"      
```



## PolKit
https://github.com/gobolinux/Recipes/tree/master/Polkit

```
echo '\n' | MakeRecipe "Polkit" "0.114" http://www.freedesktop.org/software/polkit/releases/polkit-0.114.tar.gz
Compile "Polkit" "0.114"
```



# GVfs
Gvfs depends on PolKit that depends on MozJS, that depends on Python

```
echo '\n' | MakeRecipe "GVFS" "1.48.1" "https://gitlab.gnome.org/GNOME/gvfs/-/archive/master/gvfs-master.tar.bz2"
```


## Add meson_variables to disable Systemd for GVfs 

```
InstallPackage "https://github.com/vaido-world/Resolving-GVfs/raw/main/Gcr/Gcr--3.12.0--x86_64.tar.bz2"
nano /Data/Compile/Recipes/GVFS/1.48.1/Recipe
Compile "GVFS" "1.48.1"
```

```
meson.build:306:2: ERROR: Invalid version of dependency, need 'polkit-gobject-1' ['>= 0.114'] found '0.112'.

```

```
echo '\n' | MakeRecipe "Polkit" "0.114" http://www.freedesktop.org/software/polkit/releases/polkit-0.114.tar.gz
Compile "Polkit" "0.114"
```

```
No package 'mozjs-52' found

```

```
echo '\n' | MakeRecipe MozJS 52.2.1 https://ftp.osuosl.org/pub/blfs/conglomeration/mozjs/mozjs-52.2.1gnome1.tar.gz
```

```
nano /Data/Compile/Recipes/MozJS/52.2.1/Recipe
```

https://github.com/vaido-world/Resolving-GVfs/blob/main/README.md#mozjs


```
python2.7 not found, or it's not a program.
```

```
InstallPackage "https://gobolinux.org/packages/016/Python--2.7.12-r1--x86_64.tar.bz2"
```

```
PrepareProgram: Preparing...
PrepareProgram: configure failed.
Compile: MozJS 52.2.1 - Configuration failed.

```


```
cd /Data/Compile/Sources/mozjs-52.2.1
python2.7  configure.py

illegal instruction
```
https://superuser.com/a/1618761

> https://www.google.com/search?q=ERROR%3Aroot%3Acode+for+hash+md5+was+not+found.+2.7&client=firefox-b-d&ei=sKEvYb2mKfKB9u8Pm_-0iAw&oq=ERROR%3Aroot%3Acode+for+hash+md5+was+not+found.+2.7&gs_lcp=Cgdnd3Mtd2l6EAM6BwgAEEcQsANKBAhBGABQqStY2TBg3DRoAXACeACAAUuIAZMCkgEBNJgBAKABAcgBCMABAQ&sclient=gws-wiz&ved=0ahUKEwi9vsjnkN7yAhXygP0HHZs_DcEQ4dUDCBg&uact=5


> https://stackoverflow.com/questions/60213767/how-to-install-openssl-1-1-1-for-python-2-7


https://github.com/wingo/polkit/blob/master/NEWS


```
compile_version=017-GIT
url="https://gitlab.gnome.org/GNOME/gvfs/-/archive/master/gvfs-master.tar.bz2"
file_size=1419548
file_md5=63b79a71337b6b76c6d82b4b136d55e9
dir='gvfs-master'
recipe_type=meson
meson_variables=(
        "-Dsystemduserunitdir=no"
        "-Dtmpfilesdir=no"
 )


```




