# Super Cool AnVIL Analysis

## Setup

### Git LFS

1. Install Git LFS binary
2. `git lfs install --skip-smudge`


### Git DRS

1. Install Go: https://go.dev/doc/install
2. install Git DRS from source branch
    ```
    git clone https://github.com/bmeg/git-drs.git --recurse-submodules
    cd git-drs
    git checkout feature/anvil
    go build
    ```
(in the future this will be a Go binary)

### Cloning this repo

```
git clone https://github.com/quinnwai/super-cool-anvil-analysis.git
git drs init --anvil
```

## Quickstart

### Pulling files

after clone...

```
git drs create-cache /path/to/manifest
git lfs pull -I /path/to/file       # pull a single file
git lfs pull -I /path/to/dir        # everything in a directory
git lfs pull -I /path/to/dir/*.tsv  # only tsvs in a dir
```

### Pushing files

```
git drs create-cache /path/to/manifest
git add-ref <drs-id>
git status          # check that both a `.gitattributes` and your file is commited
cat /path/to/file   # if you want to double check only the reference is being added to the repo

git commit -m "add important file"
git push
```
