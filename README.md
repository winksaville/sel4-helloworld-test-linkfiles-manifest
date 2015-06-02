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
git fetch https://gerrit.googlesource.com/git-repo refs/changes/41/68241/2 && git cherry-pick FETCH_HEAD
repo sync
```
This results in the following in <root>/srcs or <root>configs:
```
helloworld-test-linkfiles-2$ ls -al srcs
total 12
drwxrwxr-x  2 wink wink 4096 Jun  1 11:43 .
drwxrwxr-x 10 wink wink 4096 Jun  1 11:43 ..
lrwxrwxrwx  1 wink wink   32 Jun  1 11:43 bootinfo.c -> ../kernel/libsel4/src/bootinfo.c
lrwxrwxrwx  1 wink wink   43 Jun  1 11:43 bootstrap.c -> ../libs/libsel4utils/src/vspace/bootstrap.c
lrwxrwxrwx  1 wink wink   54 Jun  1 11:43 client_server_vspace.c -> ../libs/libsel4utils/src/vspace/client_server_vspace.c
lrwxrwxrwx  1 wink wink   61 Jun  1 11:43 client_server_vspace.h -> ../libs/libsel4utils/include/sel4utils/client_server_vspace.h
lrwxrwxrwx  1 wink wink   30 Jun  1 11:43 elf.c -> ../libs/libsel4utils/src/elf.c
lrwxrwxrwx  1 wink wink   44 Jun  1 11:43 elf.h -> ../libs/libsel4utils/include/sel4utils/elf.h
lrwxrwxrwx  1 wink wink   34 Jun  1 11:43 helpers.h -> ../libs/libsel4utils/src/helpers.h
lrwxrwxrwx  1 wink wink   36 Jun  1 11:43 iommu_dma.c -> ../libs/libsel4utils/src/iommu_dma.c
lrwxrwxrwx  1 wink wink   50 Jun  1 11:43 iommu_dma.h -> ../libs/libsel4utils/include/sel4utils/iommu_dma.h
lrwxrwxrwx  1 wink wink   48 Jun  1 11:43 irq_server.c -> ../libs/libsel4utils/src/irq_server/irq_server.c
lrwxrwxrwx  1 wink wink   51 Jun  1 11:43 irq_server.h -> ../libs/libsel4utils/include/sel4utils/irq_server.h
lrwxrwxrwx  1 wink wink   34 Jun  1 11:43 mapping.c -> ../libs/libsel4utils/src/mapping.c
lrwxrwxrwx  1 wink wink   48 Jun  1 11:43 mapping.h -> ../libs/libsel4utils/include/sel4utils/mapping.h
lrwxrwxrwx  1 wink wink   35 Jun  1 11:43 page_dma.c -> ../libs/libsel4utils/src/page_dma.c
lrwxrwxrwx  1 wink wink   49 Jun  1 11:43 page_dma.h -> ../libs/libsel4utils/include/sel4utils/page_dma.h
lrwxrwxrwx  1 wink wink   34 Jun  1 11:43 process.c -> ../libs/libsel4utils/src/process.c
lrwxrwxrwx  1 wink wink   48 Jun  1 11:43 process.h -> ../libs/libsel4utils/include/sel4utils/process.h
lrwxrwxrwx  1 wink wink   34 Jun  1 11:43 profile.c -> ../libs/libsel4utils/src/profile.c
lrwxrwxrwx  1 wink wink   48 Jun  1 11:43 profile.h -> ../libs/libsel4utils/include/sel4utils/profile.h
lrwxrwxrwx  1 wink wink   37 Jun  1 11:43 sel4_debug.c -> ../libs/libsel4utils/src/sel4_debug.c
lrwxrwxrwx  1 wink wink   51 Jun  1 11:43 sel4_debug.h -> ../libs/libsel4utils/include/sel4utils/sel4_debug.h
lrwxrwxrwx  1 wink wink   32 Jun  1 11:43 stack.c -> ../libs/libsel4utils/src/stack.c
lrwxrwxrwx  1 wink wink   46 Jun  1 11:43 stack.h -> ../libs/libsel4utils/include/sel4utils/stack.h
lrwxrwxrwx  1 wink wink   33 Jun  1 11:43 thread.c -> ../libs/libsel4utils/src/thread.c
lrwxrwxrwx  1 wink wink   47 Jun  1 11:43 thread.h -> ../libs/libsel4utils/include/sel4utils/thread.h
lrwxrwxrwx  1 wink wink   45 Jun  1 11:43 util.h -> ../libs/libsel4utils/include/sel4utils/util.h
lrwxrwxrwx  1 wink wink   40 Jun  1 11:43 vspace.c -> ../libs/libsel4utils/src/vspace/vspace.c
lrwxrwxrwx  1 wink wink   47 Jun  1 11:43 vspace.h -> ../libs/libsel4utils/include/sel4utils/vspace.h
lrwxrwxrwx  1 wink wink   56 Jun  1 11:43 vspace_internal.h -> ../libs/libsel4utils/include/sel4utils/vspace_internal.h



helloworld-test-linkfiles$ ls -al configs
total 12
drwxrwxr-x  2 wink wink 4096 Jun  1 11:43 .
drwxrwxr-x 10 wink wink 4096 Jun  1 11:43 ..
lrwxrwxrwx  1 wink wink   70 Jun  1 11:43 ia32_simulation_helloworld_defconfig -> ../apps/helloworld/master-configs/ia32_simulation_helloworld_defconfig
```
