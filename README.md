🎵 Music Player App

A simple and intuitive music player app built using Android that allows users to play their saved audio files. The app requests user permission to access all saved audio on the device and provides a seamless music experience.

📋 Features
🎶 Browse and Play Music: Automatically detects and lists all audio files on the device.
🔍 Search Audio Files: Find your favorite tracks easily.
⏯️ Basic Controls: Play, pause, next, and previous.
📁 Folder Support: Displays music files by folders for easy access.
🎨 User-Friendly UI: Minimalistic and responsive design.
📱 Permissions
The app requires the following permissions to function properly:->

READ_MEDIA_AUDIO (For Android 13+): To access and list audio files.
READ_EXTERNAL_STORAGE (For Android 12 and below): To access audio files stored on the device.
🚀 How It Works
Upon launching the app, the user will be prompted to grant the necessary permissions.
Once permissions are granted:
The app scans the device for all saved audio files.
It organizes and lists them in a user-friendly interface.
The user can browse, select, and play any audio file from the list.
📂 Installation
Clone the repository:
bash
Copy
Edit
git clone https://github.com/yourusername/music-player-app.git
Open the project in Android Studio.
Sync Gradle and build the project.
Run the app on an emulator or physical device.
🛠️ Tech Stack
Language: Java/Kotlin
Framework: Android SDK
Libraries:
MediaPlayer: For playing audio files.
RecyclerView: For displaying the list of audio files.
Runtime Permissions: For managing permissions dynamically.
📝 Code Snippets
Requesting Permissions
java
Copy
Edit
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.TIRAMISU) {
    if (checkSelfPermission(Manifest.permission.READ_MEDIA_AUDIO) != PackageManager.PERMISSION_GRANTED) {
        requestPermissions(new String[]{Manifest.permission.READ_MEDIA_AUDIO}, PERMISSION_REQUEST_CODE);
    }
} else {
    if (checkSelfPermission(Manifest.permission.READ_EXTERNAL_STORAGE) != PackageManager.PERMISSION_GRANTED) {
        requestPermissions(new String[]{Manifest.permission.READ_EXTERNAL_STORAGE}, PERMISSION_REQUEST_CODE);
    }
}
Listing Audio Files
java
Copy
Edit
private void listAudioFiles() {
    Uri collection = MediaStore.Audio.Media.EXTERNAL_CONTENT_URI;
    String[] projection = {
        MediaStore.Audio.Media._ID,
        MediaStore.Audio.Media.DISPLAY_NAME,
        MediaStore.Audio.Media.DATA
    };
    Cursor cursor = getContentResolver().query(collection, projection, null, null, null);

    if (cursor != null) {
        while (cursor.moveToNext()) {
            String name = cursor.getString(cursor.getColumnIndexOrThrow(MediaStore.Audio.Media.DISPLAY_NAME));
            String path = cursor.getString(cursor.getColumnIndexOrThrow(MediaStore.Audio.Media.DATA));
            // Add the audio details to your list
        }
        cursor.close();
    }
}
🎯 Future Improvements
Add support for playlists.
Include an equalizer for audio customization.
Introduce themes for a personalized experience.
Add support for streaming online music.
🧑‍💻 Contributing
Contributions are welcome! Please follow these steps:

Fork the repository.
Create a new branch (git checkout -b feature-branch).
Commit your changes (git commit -m "Add a feature").
Push to the branch (git push origin feature-branch).
Open a Pull Request.
📄 License
This project is licensed under the MIT License. See the LICENSE file for details.

