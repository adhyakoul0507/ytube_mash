# Quick Start Guide - YouTube Mashup Creator

## 🚀 Quick Setup (5 Minutes)

### Step 1: Install FFmpeg
```bash
# Ubuntu/Debian
sudo apt update && sudo apt install ffmpeg -y

# macOS
brew install ffmpeg
```

### Step 2: Install Python Packages
```bash
# Using installation script (recommended)
bash install.sh

# Or manually
pip3 install yt-dlp pydub flask flask-mail --break-system-packages
```

### Step 3: Test Command Line Program
```bash
# Quick test with 11 videos and 21 seconds
python3 101556.py "Arijit Singh" 11 21 test-output.mp3
```

## 📝 Command Line Examples

### Example 1: Simple Mashup
```bash
python3 101556.py "Sharry Maan" 15 25 sharry-mashup.mp3
```
Creates a mashup with:
- 15 videos
- 25 seconds from each video
- Output: sharry-mashup.mp3

### Example 2: Long Mashup
```bash
python3 101556.py "Taylor Swift" 30 30 taylor-long-mix.mp3
```
Creates a mashup with:
- 30 videos
- 30 seconds from each video
- Total duration: ~15 minutes

### Example 3: Short Clips
```bash
python3 101556.py "Ed Sheeran" 20 21 ed-short-clips.mp3
```
Creates a mashup with:
- 20 videos
- 21 seconds from each video
- Total duration: ~7 minutes

## 🌐 Web Service Setup

### Step 1: Configure Email
Edit `app.py` and update these lines:

```python
app.config['MAIL_USERNAME'] = 'your-email@gmail.com'
app.config['MAIL_PASSWORD'] = 'your-app-password'
app.config['MAIL_DEFAULT_SENDER'] = 'your-email@gmail.com'
```

### Step 2: Get Gmail App Password
1. Go to Google Account Settings
2. Security → 2-Step Verification
3. App Passwords
4. Generate new password for "Mail"
5. Use this password in app.py

### Step 3: Start Web Service
```bash
python3 app.py
```

### Step 4: Open Browser
```
http://localhost:5000
```

## 🎯 Usage Tips

### For Testing
- Use 11 videos and 21 seconds (minimum values)
- Choose popular singers for better results
- Test internet connection first

### For Best Results
- Use 20-30 videos
- Duration: 25-35 seconds per clip
- Popular singers have more videos
- Ensure stable internet connection

### Common Singer Names to Try
- "Sharry Maan"
- "Arijit Singh"
- "Atif Aslam"
- "Ed Sheeran"
- "Taylor Swift"
- "The Weeknd"
- "Dua Lipa"

## ⚡ Troubleshooting

### Error: "Number of videos must be greater than 10"
✅ Solution: Use at least 11 videos
```bash
python3 101556.py "Singer" 11 21 output.mp3  # ✓ Correct
python3 101556.py "Singer" 10 21 output.mp3  # ✗ Wrong
```

### Error: "Audio duration must be greater than 20"
✅ Solution: Use at least 21 seconds
```bash
python3 101556.py "Singer" 15 21 output.mp3  # ✓ Correct
python3 101556.py "Singer" 15 20 output.mp3  # ✗ Wrong
```

### Error: "FFmpeg not found"
✅ Solution: Install FFmpeg
```bash
# Ubuntu
sudo apt install ffmpeg

# macOS
brew install ffmpeg

# Verify installation
ffmpeg -version
```

### Error: "No videos downloaded"
✅ Solutions:
- Check internet connection
- Try a different singer name
- Use popular/well-known artists
- Reduce number of videos

### Web Service: Email not sending
✅ Solutions:
- Check SMTP settings in app.py
- Verify app password is correct
- Check Gmail security settings
- Allow "less secure apps" if needed
- Check firewall settings

## 📊 Expected Output

### Command Line Success:
```
============================================================
               YOUTUBE MASHUP CREATOR
============================================================

Configuration:
  Singer: Sharry Maan
  Number of videos: 15
  Audio duration: 25 seconds
  Output file: output.mp3

✓ Successfully downloaded 15 audio files!
✓ Successfully cut 15 audio files!
✓ MASHUP CREATED SUCCESSFULLY!

Output file: output.mp3
File size: 9.38 MB
Duration: 375 seconds (6.2 minutes)
============================================================
```

### Web Service Success:
```
Your mashup is being created! 
You will receive an email at your@email.com when it's ready.
```

## 🎬 Creating Demo Video

### What to Show:
1. **Installation** (1 minute)
   - Show FFmpeg installation
   - Show pip install command
   - Show successful installation

2. **Command Line Demo** (2 minutes)
   - Run the program with example
   - Show progress output
   - Play the output file

3. **Web Service Demo** (2 minutes)
   - Start the server
   - Fill the web form
   - Show email received
   - Play the mashup

4. **Code Walkthrough** (2 minutes)
   - Show main functions
   - Explain error handling
   - Show validation logic

### Recording Tips:
- Use screen recording software (OBS, QuickTime, etc.)
- Keep video under 10 minutes
- Show actual functionality working
- Explain what you're doing
- Show both success and error cases

## 📋 Assignment Checklist

### Program 1 (Command Line):
- ✅ File named as rollnumber.py (e.g., 101556.py)
- ✅ Downloads N videos (N > 10)
- ✅ Converts videos to audio
- ✅ Cuts Y seconds (Y > 20)
- ✅ Merges into single file
- ✅ Command line arguments
- ✅ Parameter validation
- ✅ Error handling

### Program 2 (Web Service):
- ✅ Web interface
- ✅ Singer name input
- ✅ Number of videos input
- ✅ Duration input
- ✅ Email input
- ✅ Email delivery
- ✅ Validation
- ✅ Error handling

## 🎓 Understanding the Code

### Key Components:

1. **Video Download** (yt-dlp)
   - Searches YouTube
   - Downloads best audio quality
   - Converts to MP3

2. **Audio Processing** (pydub)
   - Loads audio files
   - Cuts to specified duration
   - Merges multiple files

3. **Web Framework** (Flask)
   - Handles HTTP requests
   - Serves HTML template
   - Processes form data

4. **Email Service** (Flask-Mail)
   - Sends emails with attachments
   - Uses SMTP protocol
   - Background processing

### File Flow:
```
YouTube → Download → Convert to MP3 → Cut Duration → Merge → Output File
```

## 💾 Disk Space Requirements

- Each video: ~5-10 MB
- For 20 videos: ~100-200 MB temporary space
- Final mashup: ~10-15 MB
- Recommendation: Have at least 500 MB free space

## ⏱️ Time Estimates

- Downloading 15 videos: 2-5 minutes
- Processing audio: 30-60 seconds
- Total time: 3-6 minutes

Depends on:
- Internet speed
- Number of videos
- Audio duration
- Computer performance

## 🔐 Security Notes

### Email Passwords:
- Never commit app passwords to Git
- Use environment variables in production
- Keep app.py configuration private

### Web Service:
- Run on localhost for testing
- Use HTTPS in production
- Validate all user inputs

---

Need help? Check README.md for detailed documentation!
