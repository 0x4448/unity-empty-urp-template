# Unity Empty URP Template

This is a minimal template for starting a URP Unity project.

## Features
* .gitignore for Unity projects
* .gitattributes with [Git LFS](https://git-lfs.github.com) support

## How To Use
1. [Create a new repository](https://github.com/0x4448/unity-empty-urp-template/generate) from this template.
2. Clone your repository.
3. `cd` into your local repository and run `git lfs install`.
4. Configure Unity's merge tool in your local repository's git config file (`.git\config`):
```
[merge]
	tool = unityyamlmerge
[mergetool "unityyamlmerge"]
	trustExitCode = false
	# Replace with your editor's installation path
	cmd = 'C:\\Program Files\\Unity\\Hub\\Editor\\UNITY_VERSION\\Editor\\Data\\Tools\\UnityYAMLMerge.exe' merge -p "$BASE" "$REMOTE" "$LOCAL" "$MERGED"
```
5. Replace the README and LICENSE with your own.
