This manifest tests the LinkFile modifications I implemented
for repo here: https://gerrit-review.googlesource.com/#/c/68241/
and then did the following to sync the repoository:

```
mkdir helloworld-test-linkfiles-2
cd helloworld-test-linkfiles-2/
repo init -u https://github.com/winksaville/sel4-helloworld-test-linkfiles-manifest
cd .repo/repo
git pull origin master
git checkout master
git checkout -b test-linkfiles 
git fetch https://gerrit.googlesource.com/git-repo refs/changes/41/68241/3 && git cherry-pick FETCH_HEAD
repo sync
../../test_LinkFile.py ../../
```
This should result in:
```
Success
```
For subsequent tests reset the environment back so you can reexecute "repo sync"
```
rm -rf ../../* ../../.build ../project.list ../project-objects ../projects ../.repo_fetchtimes.json
repo sync
../../test_LinkFile.py ../../

```
