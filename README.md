## Workflows for building OpenWrt firmware

This repository is improved base on **[P3TERX/Actions-OpenWrt](https://github.com/P3TERX/Actions-OpenWrt)**. Since the original repository has been archived and cannot submit PR, it is provided as a new repository.

- - -

This project fixes some functional failures caused by the upgrade of GitHub permission system in the original project, and improves the function of automatic compilation of source code update. Workflows in this repository does not need additional tokens.

**2023/2/16:** Fully refactored, solve a lot of old problems, improve safety and reliability.

**2023/3/10:** Delete the feature of loading `feeds.conf.default`, because it is easy to inadvertently cause problems when compiling source code of non-default branch or hash. 
               Specifically, feeds that depend on the source code of a particular branch or hash also need to specify a branch or hash. At this point, if we still use file overwriting to introduce custom feeds, we must be careful that the branch or hash information of the original base feed is overwritten and lost. 
               Therefore, the alternative is to use `CUSTOM_SCRIPT_1` to modify the `feeds.conf.default`. Please check the comments in `example-custom-script-1.sh` for details.

- - -

### Usage:

1. Generate your workflow repo from this repository, and generate workflow file from `template.yaml`. You can rename the copy of `template.yaml` to any name you want, but remember that the file extension must be `.yaml` or `.yml`. 

2. In your workflow file, modify the content according to the annotations.  
3. Then you can startup the workflow manually or regularly. 
   + Select the workflow name on the Actions page to run it manually.
   + For run regularly, you need to uncomment:
     ```
     schedule:
       - cron: 0 */18 * * *
     ```
     There you can use your own cron expression to start the workflow as needed.

Each time this workflow runs, it will check whether the specified repository is updated. If the source code is updated, it will start compiling the new firmware.  
Whether the workflow is started manually or regularly, the compilation will only be triggered when the source code is updated. However, during manual startup, you can force firmware compilation by entering `true` in `Build new firmware anyway`.

- - -

### Copyright:
MIT Licence © 2022~2023 Curious <https://curious.host>  
