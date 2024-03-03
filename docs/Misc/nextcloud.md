---
tags:
    - nextcloud
    - trashbin
    - versions
---

# Nextcloud
## Show used space/storage from trashbin and versions (Local files)
**Trashbin**
```bash
for i in *; do du -sh $i/files_trashbin >> /tmp/trashbin.log; done
```
**Versions**
```bash
for i in *; do du -sh $i/files_versions >> /tmp/versions.log; done
```
