
### Device Connection and IP Setup:
```bash
adb devices
adb shell
adb shell ip addr show wlan0
adb tcpip 5555
adb connect <device_ip_address>:5555
```

### File Transfer:
```bash
adb push local/path remote/path
adb pull remote/path local/path
```
**Example:**
```bash
adb pull /sdcard/Download/example_file.txt /Users/yourusername/Desktop/
```

### Opening Apps via ADB:
```bash
adb shell am start -a android.media.action.IMAGE_CAPTURE                    # Open Camera
adb shell am start -a android.intent.action.VIEW -d https://www.youtube.com  # Open YouTube
adb shell am start -n com.whatsapp/.HomeActivity                             # Open WhatsApp
adb shell am start -a android.intent.action.VIEW -d http://www.google.com    # Open Web Browser
adb shell am start -a android.intent.action.VIEW -d "geo:0,0?q=1600+Amphitheatre+Parkway,+Mountain+View,+California"  # Open Google Maps
adb shell am start -a android.intent.action.VIEW -d "market://details?id=com.example.package"  # Open Google Play Store
adb shell am start -n com.facebook.katana/.LoginActivity                     # Open Facebook
adb shell am start -n com.instagram.android/.activity.MainTabActivity        # Open Instagram
adb shell am start -n com.twitter.android/.StartActivity                     # Open Twitter (X)
adb shell am start -n com.spotify.music/.MainActivity                        # Open Spotify
adb shell am start -n com.google.android.gm/.ConversationListActivityGmail   # Open Gmail
adb shell am start -a android.settings.SETTINGS                              # Open Settings
adb shell am start -a android.intent.action.DIAL                             # Open Phone Dialer
adb shell am start -a android.intent.action.VIEW -d sms:                     # Open SMS App
adb shell am start -a android.intent.action.VIEW -d content://contacts/people/  # Open Contacts App
adb shell am start -n com.android.calculator2/.Calculator                    # Open Calculator
adb shell am start -n com.google.android.calendar/.LaunchActivity            # Open Calendar
adb shell am start -n com.google.android.apps.youtube.music/.activities.MainActivity  # Open YouTube Music
```

### Capture Screenshot:
```bash
adb shell screencap /sdcard/screenshot.png
adb pull /sdcard/screenshot.png /path/to/save/on/your/computer/
adb shell rm /sdcard/screenshot.png    # Optional: Delete the screenshot
```

### Check Device Logs:
```bash
adb logcat
adb logcat -d > /path/to/save/logfile.txt
adb logcat *:E    # Filter by error logs only
adb logcat | grep com.example.myapp    # Filter logs by a specific app
```

### Call Logs Download (Requires Root Access):
```bash
adb pull /data/data/com.android.providers.contacts/databases/calllog.db /path/to/save/on/your/computer/
```

### Disconnect:
```bash
adb disconnect <device_ip_address>:5555
adb disconnect    # Disconnect all devices
```

