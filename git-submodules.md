# Git submodules cheatsheet

Checking status of submodules in project (hash, path, branch)

`
git submodule status --recursive
`

Adding submodule to project with specific branch

`
git submodule add -b develop https://github.com/nexpaq/extended-webview.git
`

Initialising all submodules in repo for first time after clone

`
git submodule update --init --recursive
`

Updating all submodules in repo (they should be initialized already)

`
git submodule update --recursive --remote
`
