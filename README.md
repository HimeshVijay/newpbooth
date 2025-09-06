?? Raspberry Pi Photobooth App

This is a DIY Photobooth project for Raspberry Pi 4 + Camera Module 3.
It provides:

? Live camera preview with natural colors

? Snapshot capture on click

? GUI (Tkinter) interface

? Optional Google Drive / Gmail integration

?? Requirements

Raspberry Pi OS Bookworm or later

Raspberry Pi 4 (recommended)

Raspberry Pi Camera Module 3 (tested)

?? Installation

Run the following commands on your Raspberry Pi:

1. Update system
sudo apt update && sudo apt full-upgrade -y

2. Install system dependencies
sudo apt install -y \
python3-picamera2 \
python3-numpy \
python3-pil.imagetk \
python3-tk \
libcamera-apps

3. Install Python packages

?? On Raspberry Pi OS Bookworm, use --break-system-packages when installing via pip.

pip install --break-system-packages Pillow opencv-python
pip install --break-system-packages google-api-python-client google-auth google-auth-oauthlib google-auth-httplib2


If you’re using legacy Google auth code:

pip install --break-system-packages oauth2client

?? Usage

Connect your Raspberry Pi Camera Module 3.

Stop PipeWire from grabbing /dev/video0 & /dev/video1:

systemctl --user stop pipewire wireplumber


Launch the photobooth:

bash photobooth.sh

?? Testing the Camera

Before running the app, test your camera works:

libcamera-hello -t 5000


If you see a preview, your camera is working correctly.

?? Notes

If the preview colors look washed out, ensure you’re using RGB888 format in cv2_camera.py.

Google Drive/Gmail features require a credentials JSON file from the Google Cloud Console.

If you just want local photos, comment out the Google API sections in user_interface.py.
