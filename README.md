# README

This simple application takes files from your HP scanner and puts them on the cloud via rclone.

# Intallation

## 1. Install rclone

Follow [this guide](https://rclone.org/downloads/).

If impatient: 

```
curl https://rclone.org/install.sh | sudo bash 
```

Then you need to configure your target (Google Drive, Amazon S3, ...). For that do: 

```
rclone config # name the remote 'drive' for convenience
```

If everything is correctly configured, you should be able to list files in your storage `drive` using: 


```
rclone ls drive:/
```

## 2. Install hp-scan

Download `hplip-x.y.z.run` from [here](https://developers.hp.com/hp-linux-imaging-and-printing/gethplip) (in my case for Debian) and install it (for example `hplip-3.22.6.run`).

This step should also setup your printer.

Then you will need to install `the` plugin (something like `hplip-3.22.6-plugin.run`). You can download it from the same page.

As reference, you can take a look at [this documentation](https://www.systutorials.com/docs/linux/man/1-hp-scan/).

## 2. Configure the app

All configuration can be found in the file `app.config`. It's filled with default values as reference. You can customize any variables in there. Below a quick guide on how to setup the most important / mandatory variables.

### Variable scanner_device

1. Run `scanimage -L`, you should see the name of your printer. 
2. Set it up in `app.config` under the variable `scanner_device`. See the default value in the default `app.config` file as reference.


### Variable google_dir_base

The format is `<rclone_drive_name>:<path>`. See the default value in the file as a reference.
