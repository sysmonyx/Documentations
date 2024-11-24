# Best practices & settings for Hardware Acceleration & Media support for Intel Graphics on Fedora Workstations.

## 1. Install RPMFusion repos

```
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm

sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

## 2. Install multimedia packages & Intel tools

```
sudo dnf groupinstall multimedia

sudo dnf install intel-media-driver libva libva-utils gstreamer1-vaapi ffmpeg intel-gpu-tools mesa-dri-drivers mpv
```

## 3. Add environment variable for Libva
Add the following line to your `.bashrc` (if using bash):

`export LIBVA_DRIVER_NAME=iHD`

## 4. Enable Intel GuC and HuC and Framebuffer compression
GuC and HuC are features built into [newer-gen](https://01.org/linuxgraphics/downloads/firmware) Intel graphics and apparently have power usage and performance benefits.

Add kernel parameters to load GuC and HuC (contrary to popular belief, [they are not enabled by default except on Intel gen12+ platforms](https://wiki.archlinux.org/title/Intel_graphics#Enable_GuC_/_HuC_firmware_loading) in the kernel) by entering the following:

`sudo nano /etc/modprobe.d/i915.conf`

and paste the following:

```
options i915 enable_guc=3
options i915 enable_fbc=1
```

Then rebuild your intramfs with the following:

`sudo dracut --force`

**Then reboot (important)**

## 5. Test to make sure everything is enabled and working properly

1. Test VA-API support with `vainfo` and compare against this [ArchWiki section](https://wiki.archlinux.org/title/Hardware_video_acceleration#Verifying_VA-API).
2. Check to make sure GuC and HuC are enabled:

    A. For GuC:
    ```
    sudo dmesg | grep guc
    ```

    Should return something like
    `GuC firmware i915/tgl_guc_62.0.0.bin version 62.0 submission:enabled`

    B. For HuC:
    ```
    sudo dmesg | grep huc
    ```
    Should Return something like
    `HuC firmware i915/tgl_huc_7.9.3.bin version 7.9 authenticated:yes`

3. Test VA-API support:

    A. Download a test video file.

    B. Open a new terminal window and run `sudo intel_gpu_top` (keep this window open).

    C. In a separate terminal window, run `mpv --hwdec=auto <video file>`.

    D. Go back to the `intel_gpu_top` terminal window and check to make sure the **“Video”** bar shows activity, this indicates that video is being accelerated properly.

**Source**
> https://discussion.fedoraproject.org/t/intel-graphics-best-practices-and-settings-for-hardware-acceleration/69944
