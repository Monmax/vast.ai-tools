## GPU Profile switcher

This script monitors docker container start events and applies GPU settings based on the docker image being used, or applying default settings you define.

To install it run
```bash
wget -O - https://raw.githubusercontent.com/Monmax/vast.ai-tools/master/gpu-profile/setup.sh | sudo bash
```

To uninstall it run
```bash
wget -O - https://raw.githubusercontent.com/Monmax/vast.ai-tools/master/gpu-profile/setup.sh | sudo bash -s uninstall
```

Set the default config. Run the command again to update certain values.
```bash
gpu-profile default
```

Create config for a specific docker image
```bash
gpu-profile nxie/aio-miner
```

After setting config the daemon gets restarted and it will apply to your running containers without any downtime. I recommend doing clock and memory changes while unlisted though.

When you first install, it is recommended to reboot and then check the logs at `/var/log/gpu-profile.log` to ensure it can run properly on boot.

## Issues

If you are power limiting, your listed dlperf will be reduced while background jobs are running. 3090 for example will drop from 36 to around 32 dlperf if power limited to 280w.
