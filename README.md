# docker-rclone-mount
Mount a rclone remote inside a docker container.  This fork is for personal learning purposes only. Please check out danielheene's for original stuff.

### Start
```bash
docker run \
  --cap-add SYS_ADMIN \
  --device /dev/fuse \
  -v ${HOST_CONF_DIR}:/config \
  -v ${HOST_MOUNT_DIR}:/mount \
  danielheene/rclone-mount
```

### Environment variables

```
CONFIG_DIR      /config         # directory where config file is stored
CONFIG_FILE     rclone.conf     # name of the stored rclone config file
MOUNT_DIR       /mount          # directory where the volume is mounted
MOUNT_REMOTE    mount           # rclone volume name which will be mounted
CACHE_DIR       /cache          # directory which rclone uses for caching
```

### Example config file
```
[remote]
type = drive
...

[cache]
type = cache
remote = remote:
tmp_upload_path = /cache
...

[mount]
type = alias
remote = cache:
...
```

----
## License
[MIT](https://github.com/danielheene/docker-rclone-mount/blob/develop/LICENSE)
