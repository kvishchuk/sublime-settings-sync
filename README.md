# Sublime Text setting [sync]

by [Andreas Müller](https://medium.com/@devmount/using-git-to-sync-sublime-text-settings-f70b8dc7a40d#.yvv8bpola)

## Usage

1. Create GitHub repo
2. Go to:
- For Windows: ~\AppData\Roaming\Sublime Text 3\Packages\User
- For Linux:   ~/.config/sublime-text-3/Packages/User
3. Create .gitignore file:
```
# Ignore everything...
*
# ... except preferences and packages
!.gitignore
!Preferences.sublime-settings
!Package Control.sublime-settings
```
4. Create git repo:
```
git init
git remote add origin <repository url>
```
5. Fetch settings from repo:
```
git fetch
git reset --hard origin/master
```

>With the last line, the existing setting files will be overwritten by those from the repository. If you want your >local files to be committed, just make a backup before and copy the files back to the created repository to
>commit the changes. Or remove the “hard” flag of the reset instruction and merge all changes manually.

6. Sync:
- For Win:
```
git -C ~/AppData/Roaming/Sublime\ Text\ 3/Packages/User/ pull
```

- For Linux:
```
git -C ~/.config/sublime-text-3/Packages/User pull
```

>It occurs, that the settings files differ right after pulling the current versions from the repository (especially when Package Control loads missing packages) e.g. because of a different order of entries in the packages list or the settings elements. In that case you can just use the hard-reset instruction to overwrite your unwanted local changes.