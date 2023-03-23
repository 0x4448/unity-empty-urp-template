# Unity Empty URP Template

This is a minimal template for starting a URP Unity project.

## Features
* .gitignore for Unity projects
* .gitattributes with [Git LFS](https://git-lfs.github.com) support
* [EditorConfig](https://editorconfig.org) for consistent code style
* Run linter on pull request

## Requirements
* [.NET 6.0 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/6.0)
* [Git LFS](https://github.com/git-lfs/git-lfs#getting-started) (already included with [Git for Windows](https://github.com/git-for-windows/git/releases/latest))

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
5. Configure your [pre-commit git hook](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks#_committing_workflow_hooks) (`.git/hooks/pre-commit`):
```
#!/bin/sh

if git branch --show-current | grep -q 'main\|master\|trunk'; then
  echo "Cannot commit directly to the main branch."
  exit 1
fi

solution=$(find . -maxdepth 1 -name "*.sln" -type f | head -1)
if ! git diff --cached --diff-filter=ACM --name-only --quiet "*.cs"; then
  git diff --cached --diff-filter=ACM --name-only "*.cs" | dotnet format "$solution" --verify-no-changes --include -
  exit $?
fi
```
6. Replace the README and LICENSE with your own.
