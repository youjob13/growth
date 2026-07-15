## What are git submodule?
Git submodule allows us include one Git repository as sub catalog for another (parent) Git repository.
In the parent repository git stores **link** to the specific commit in external repository. (not submodule code itself, only link to **commit**).
It allows fix concrete code version to external repository.

## Why do we need submodule?
- when we need to split code into independent repos;
- when we have to use reusable library in different projects;
- strict versioning and reproducability are important.

**Examples:**
logger library, ui-kit library, infrastructure scripts

## When does submodules better than versioning via package manager (NPM):
- with npm we do not have an access to the library source code, we store version in package*.json files, with submodules we store gitlink to the specific commit to external repository, when clonning we receive submodule repo code as git tree part. We can use `git diff` to see changes, quickly switch between branches/commits of external library;
- when we want to connect some code that couldn't be packaged with package manager (e.g. configs files, templates, scripts, docs);
- better control over dependency via conrete **commit** not **tag/release**. NPM version is an abstraction over commits, submodule - direct link to the commit;
- better control on CI/CD over main repo and sub modules.

## When alternative approach is better than submodule:
- we can use package manager instead (it's simpler to support and develop) and we can just specify concrete dependency version;
- more complexity during support, CI/CD;
- git subtree - when we want to include external repo into current repo history.

## Main artifacts
- .gitmodules [submodule "submodule-name"]
  - **url** to the external repo or local path;
  - **path** to submodule in your main repository;
  - **branch** (optional) default branch to fetch changes with.
 In the main repo we must commit .gitmodules and submodule folder. We commit gitlink to external submodule commit. (submodule changes is not included into main repo history, only gitlink)

## How to use?
### Add new submodule into the main repo:
1. `git submodule add https://github.com/example/logger.git libs/logger` - add submodule
2. `git add .gitmodules libs/logger`
3. `git commit -m 'feat: add external submodule'`

### Clone repo with submodules:
1. `git clone https://github.com/example/app.git` - clone the repo itself
2. `git submodule init` - register submodules based on the .gitmodules file
3. `git submodule update` - update and clone submodules from the specific commit

`git submodule update --init --recursive` - if we have several submodules and they are recursive
or
`git clone --recurse-submodules https://github.com/example/app.git` - to make everything in one command

### Work with submodules (read):
1. `cd libs/logger` - go to the submodule
2. `git pull origin main` - pull the last changes from the main branch
3. `cd ../..` - return to the main repo
4. `git add libs/logger`
5. `git commit -m 'feat: update submodule version'`
or 
`git submodule update --remote` - update all submodules to the last commit (default or specified branch will be used)

### Work with submodules (write);
1. `cd libs/logger` - go to the submodule
2. make some changes...
3. `git add .`
4. `git commit -m 'feat: add verbose logging option'`
5. `git push origin main`
6. `cd ../..`
7. `git add libs/logger`
8. `git commit -m 'feat: update submodule version`
