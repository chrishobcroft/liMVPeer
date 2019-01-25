# liMVPeer

This repository contains information about creating a Minimum Viable Product for livestreaming.

These instructions explain how to set up liMVPeer to stream from your local computer.

Here are the pre-requisites:

- Computer running Ubuntu 18.04
- Connection to the internet with at least 120 kbps upstream bandwidth

The instructions will guide you through installing and configuring the following software packages:

- ngrok
- livepeer
- OBS
- VLC

### Getting started

1. Create a folder on your desktop called liMVPeer.

The easiest way to do this is as follows:

- Open `Terminal` (press the "Start" button and type `Terminal` in the box at the top).
- Copy the following command to your clipboard:
```
mkdir ~/Desktop/liMVPeer
```
- Paste it in to your `Terminal`, then press return.

### Download all the software

1. ngrok

- Open https://dashboard.ngrok.com/get-started
- Right-click the button marked "Download for Linux", and select "Save link as"
- Save link in the folder you created above: `Desktop/liMVPeer`
  - Select "Desktop" from the folder menu
  - Double-click "liMVPeer" from the folder browser
  - Click "Save"

2. livepeer

- Open https://github.com/livepeer/go-livepeer/releases/tag/0.3.1
- Right-click the link marked "livepeer_linux.tar.gz", and select "Save link as"
- Save link in the folder you created above: `Desktop/liMVPeer`
  - Select "Desktop" from the folder menu
  - Double-click "liMVPeer" from the folder browser
  - Click "Save"

3. OBS

- Open `Terminal` (press the "Start" button and type `Terminal` in the box at the top).
- Copy the following command to your clipboard:
```
sudo echo
```
- Paste it in to your `Terminal`, then press return.
- Enter the password you use to log in to Ubuntu (no characters will appear on the screen)
- Press return
- Copy the following command to your clipboard:
```
sudo add-apt-repository ppa:obsproject/obs-studio
```
- Paste it in to your `Terminal`, then press return.
- Copy the following command to your clipboard:
```
sudo apt-get update
```
- Paste it in to your `Terminal`, then press return.
- Copy the following command to your clipboard:
```
sudo apt-get install obs-studio
```
- Paste it in to your `Terminal`, then press return.

4. VLC

- Copy the following command to your clipboard:
```
sudo snap install vlc
```
- Paste it in to your `Terminal`, then press return.

### Unpack the software

- Open `Terminal` (press the "Start" button and type `Terminal` in the box at the top).
  - Or if `Terminal` is still open from before, use that one :)
- Copy the following command to your clipboard:
```
cd ~/Desktop/liMVPeer
```
- Paste it in to your `Terminal`, then press return.
- Copy the following command to your clipboard:
```
unzip ngrok-stable-linux-amd64.zip
```
- Paste it in to your `Terminal`, then press return.
- Copy the following command to your clipboard:
```
tar xvf livepeer_linux.tar.gz
```
- Paste it in to your `Terminal`, then press return.

### Configure ngrok

- Open `Terminal` (press the "Start" button and type `Terminal` in the box at the top).
  - Or if `Terminal` is still open from before, use that one :)
- Copy the following command to your clipboard:
```
cd ~/Desktop/liMVPeer
```
- Paste it in to your `Terminal`, then press return.
- Copy the following command to your clipboard:
```
./ngrok authtoken 
```
- Paste it in to your `Terminal`, but *don't press return yet*.

- Open https://dashboard.ngrok.com/user/signup in a web browser
- Fill in the form, or alternatively sign up using Github or Google.
- Once you've signed up, go to the section in the dashboard called "Auth"
- Click the button "Copy", under where it says "Your Tunnel Authtoken"
- Go back to `Terminal`, and copy the authtoken
  - It should now look like this, where the authtoken is your own:
```
./ngrok authtoken 7zz5wwF5X3YBjKs9oRtuq_6gzbMSr9WYDUbj7QLK89w
```

### Run ngrok

- Open `Terminal` (press the "Start" button and type `Terminal` in the box at the top).
  - Or if `Terminal` is still open from before, use that one :)
- Copy the following command to your clipboard:
```
./ngrok tcp 8935
```
- Paste it in to your `Terminal`, then press return.

### Run livepeer

### Run and Configure OBS

### Start streaming

### Test your stream
