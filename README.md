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

### Data Explorer

 1. Open https://explore.anvilproject.org/
 2. select the "Files" tab -> Use filters to get the files you want
 3. Download the file manifest: select "Export" -> "Request File Manifest"

### Generate SHA256 hashes for Files

Open the file manifest downloaded from the Data Explorer. Do a quick check if there are any sha codes (CMD+F for "sha256"). If not, you will need to generate them and add them to the manifest:
 1. Create a sha code
 2. Make use of the [sha256 workflow](https://dockstore.org/workflows/github.com/data-metrics/sha256/wdl:master?tab=info) on Dockstore to create sha codes
 3. Add those codes to the original manifest

### Cloning this repo

```
git clone https://github.com/quinnwai/super-cool-anvil-analysis.git
git drs init --anvil
# in the config file, change project to a Google project you have billing access to
# typically a Terra project found via workspace homepage
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
