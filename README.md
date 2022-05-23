## Workflows for building OpenWrt firmware

*This repository is improved based on **[P3TERX/Actions-OpenWrt](https://github.com/P3TERX/Actions-OpenWrt)**. Since the original repository has been archived and cannot submit PR, it is provided as a new repository.*

- - -

This project fixes some functional failures caused by the upgrade of GitHub permission system in the original project, and improves the function of automatic compilation of source code update. Workflows in this repository does not need additional tokens.

- - -

### Usage:

Fork this repository, generate your workflow file from *template.yaml*. You can rename the copy of *template.yaml* to any name you want, but remember that the file extension must be *.yaml* or *.yml*.

In your workflow file, modify the content according to the annotations.
Then you can startup the workflow manually or regularly. For run regularly, you need to uncomment:
```
  schedule:
    - cron: 0 */18 * * *
``` 
Each time this workflow runs, it will check whether the specified repository is updated. If the source code is updated, it will start compiling the new firmware.
Whether the workflow is started manually or regularly, the compilation will only be triggered when the source code is updated. However, during manual startup, you can force firmware compilation by entering true in ***Build new firmware anyway***.