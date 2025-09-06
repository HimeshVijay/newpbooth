?? Raspberry Pi Photobooth App
==============================

A DIY Photobooth project for Raspberry Pi 4 + Camera Module 3.

? Features:
- ?? Live preview with natural colors
- ?? Snapshot capture on click
- ??? Tkinter GUI interface
- ?? Optional Google Drive / Gmail upload

------------------------------
?? Requirements
------------------------------
- Raspberry Pi OS Bookworm or later
- Raspberry Pi 4 (recommended)
- Raspberry Pi Camera Module 3 (tested)

------------------------------
?? Installation
------------------------------

1?? Update system
-----------------
sudo apt update && sudo apt full-upgrade -y

2?? Install system dependencies
-------------------------------
sudo apt install -y \
  python3-picamera2 \
  python3-numpy \
  python3-pil.imagetk \
  python3-tk \
  libcamera-apps

3?? Install Python dependencies
-------------------------------
?? On Raspberry Pi OS Bookworm, use --break-system-packages.

pip install --break-system-packages Pillow opencv-python
pip install --break-system-packages google-api-python-client google-auth google-auth-oauthlib google-auth-httplib2

?? If you’re still using legacy Google auth code:
pip install --break-system-packages oauth2client

------------------------------
?? Usage
------------------------------
1. Connect your Raspberry Pi Camera Module 3
2. Stop PipeWire from grabbing /dev/video0 & /dev/video1:
   systemctl --user stop pipewire wireplumber
3. Run the photobooth app:
   bash photobooth.sh

------------------------------
?? Testing the Camera
------------------------------
Before running the app, test your camera:
libcamera-hello -t 5000

? If you see a preview ? your camera works correctly.

------------------------------
?? Notes
------------------------------
- ?? Use RGB888 format in cv2_camera.py for natural colors
- ?? Google Drive / Gmail features need a credentials.json from Google Cloud Console
- ?? If you only want local photos, just comment out Google API code in user_interface.py

------------------------------
?? Pro Tips
------------------------------
- Add a countdown overlay before snapshots for a real photobooth vibe ??
- Save images with timestamps for easy sorting
- Integrate a GPIO push button to trigger captures

?? With this setup, your photobooth app runs reliably without dependency errors.
