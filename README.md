# Space Pixel Shooter - OTA Update Server

This repository is strictly used as an **Over-The-Air (OTA) Update Manifest** for the Android game *Space Pixel Shooter*. 
It does not contain the game source code or any binary files (APKs).

## How it works

When the Android application starts, it performs a secure, background `fetch` to the `version.json` file hosted on GitHub Pages derived from this repository. 

If the `"latest_version"` inside the JSON is greater than the app's internal Hardcoded Version, the app prompts the user to download an update.

### Security
To prevent unauthorized downloads of the closed-beta APK from external users inspecting this repository, the `"update_url_encrypted"` field is AES-256 encrypted.
The private AES decryption key is embedded in the minified offline source code of the Android application. Only legitimate installations can decrypt the string back into the usable Google Drive download link.
