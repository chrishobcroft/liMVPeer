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

- Open `Terminal` (press the "Start" button and type `Terminal` in the box at the top, and press return).
- Copy the following command to your clipboard:
```
mkdir ~/Desktop/liMVPeer
```
- Paste it in to your `Terminal` (right click, select Paste), then press return.

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

- Open `Terminal` (press the "Start" button and type `Terminal` in the box at the top, and press return).
- Copy the following command to your clipboard:
```
sudo echo
```
- Paste it in to your `Terminal` (right click, select Paste), then press return.
- Enter the password you use to log in to Ubuntu (no characters will appear on the screen)
- Press return
- Copy the following command to your clipboard:
```
sudo add-apt-repository ppa:obsproject/obs-studio
```
- Paste it in to your `Terminal` (right click, select Paste), then press return.
- Copy the following command to your clipboard:
```
sudo apt-get update
```
- Paste it in to your `Terminal` (right click, select Paste), then press return.
- Copy the following command to your clipboard:
```
sudo apt-get install obs-studio
```
- Paste it in to your `Terminal` (right click, select Paste), then press return.

4. VLC

- Copy the following command to your clipboard:
```
sudo snap install vlc
```
- Paste it in to your `Terminal` (right click, select Paste), then press return.

### Unpack the software

- Open `Terminal` (press the "Start" button and type `Terminal` in the box at the top, and press return).
  - Or if `Terminal` is still open from before, use that one :)
- Copy the following command to your clipboard:
```
cd ~/Desktop/liMVPeer
```
- Paste it in to your `Terminal` (right click, select Paste), then press return.
- Copy the following command to your clipboard:
```
unzip ngrok-stable-linux-amd64.zip
```
- Paste it in to your `Terminal` (right click, select Paste), then press return.
- Copy the following command to your clipboard:
```
tar xvf livepeer_linux.tar.gz
```
- Paste it in to your `Terminal` (right click, select Paste), then press return.

### Configure ngrok

- Open `Terminal` (press the "Start" button and type `Terminal` in the box at the top, and press return).
  - Or if `Terminal` is still open from before, use that one :)
- Copy the following command to your clipboard:
```
cd ~/Desktop/liMVPeer
```
- Paste it in to your `Terminal` (right click, select Paste), then press return.
- Copy the following command to your clipboard:
```
./ngrok authtoken 
```
- Paste it in to your `Terminal` (right click, select Paste), but *don't press return yet*.

- Open https://dashboard.ngrok.com/user/signup in a web browser
- Fill in the form, or alternatively sign up using Github or Google.
- Once you've signed up, go to the section in the dashboard called "Auth"
- Click the button "Copy", under where it says "Your Tunnel Authtoken"
- Go back to `Terminal`, and paste the authtoken at the end of the line (right click, select Paste)
  - It should now look like this, where the authtoken is your own:
```
./ngrok authtoken 7zz5wwF5X3YBjKs9oRtuq_6gzbMSr9WYDUbj7QLK89w
```

### Run ngrok

- Open `Terminal` (press the "Start" button and type `Terminal` in the box at the top, and press return).
  - Or if `Terminal` is still open from before, use that window :)
- Copy the following command to your clipboard:
```
./ngrok tcp 8935
```
- Paste it in to your `Terminal` (right click, select Paste), then press return.

This should display a line which looks similar to this, but likely with different settings:
```
Forwarding                    tcp://0.tcp.ngrok.io:14605 -> localhost:8935
```
You should make a note of your settings which correspond to `0.tcp.ngrok.io:14605` in the example as you will be needing this soon.

### Run livepeer

- Open `Terminal` (press the "Start" button and type `Terminal` in the box at the top, and press return).
- Copy the following command to your clipboard:
```
./livepeer_linux/livepeer -offchain
```
- Paste it in to your `Terminal` (right click, select Paste), then press return.
- This should display some information, and should include the following:
```
Video Ingest Endpoint - rtmp:/127.0.0.1:1935
```

Once you see this appear on the screen, you are ready to livestream.

### Run and Configure OBS

- Open `Terminal` (press the "Start" button and type `Terminal` in the box at the top, and press return).
- Copy the following command to your clipboard:
```
obs-studio
```
- Paste it in to your `Terminal` (right click, select Paste), then press return.
- If you are running OBS for the first time, you will be asked to complete an Auto-Configuration Wizard. Cancel this.
- In the bottom right, click on "Settings"
- On the left of the new window, click "Stream"
- For "Stream Type", select "Custom Streaming Server"
- For URL, copy and paste the following
```
rtmp://127.0.0.1:1935
```
- Click OK

### Start streaming

- In OBS, in the bottom right, click "Start Streaming"
- Go to the `Terminal` window where livepeer is running
- You will see that a video has begun with a ManifestID, similar to what you see below:
```
Video Created With ManifestID: b58f903ebd3e7bbeb20fd88f11d203ab3fa4acb8e215df8c5873489b85650729
```

### Construct your streaming URL

- Open `Text Editor` (press the "Start" button and type `Text Editor` in the box at the top, and press return).
- Type `http://`
- Go to the `Terminal` window where you are running ngrok
- Select the text which is your equivalent of `0.tcp.ngrok.io:14605`
- Copy this selected text (right click, select Copy)
- Go to `Text Editor`
- Paste the ngrok text after the `http://` so that it looks something like this:
```
http://0.tcp.ngrok.io:14605
```
- Type `/stream/` at the end of the line, so that it looks something like this:
```
http://0.tcp.ngrok.io:14605/stream/
```
- Go to the `Terminal` window where you are running livepeer
- Select the ManifestID text, which should be a long string of characters
- Copy this selected text (right click, select Copy)
- Go to `Text Editor`
- Paste the ManifestID at the end of the line
- Type `.m3u8` at the end of the line, so that it looks something like this:
```
http://0.tcp.ngrok.io:14605/stream/b58f903ebd3e7bbeb20fd88f11d203ab3fa4acb8e215df8c5873489b85650729.m3u8
```

This is the URL for your stream. Copy it to your clipboard.

### Test your stream

- Open `Terminal` (press the "Start" button and type `Terminal` in the box at the top, and press return).
- Type the following command to your clipboard, then press return:
```
vlc
```
- Select "Media" from the top menu
- Select "Open Network Stream"
- Paste the URL for your stream into the field marked "Please enter a network URL"

