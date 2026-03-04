# Space Pixel Shooter - OTA Update Server

This repository is strictly used as an **Over-The-Air (OTA) Update Manifest** for the Android game *Space Pixel Shooter*. 
It does not contain the game source code or any binary files (APKs).

## How it works

When the Android application starts, it performs a secure, background `fetch` to the `version.json` file hosted on GitHub Pages derived from this repository. 

If the `"latest_version"` inside the JSON is greater than the app's internal Hardcoded Version, the app prompts the user to download an update.

### Security
To prevent unauthorized downloads of the closed-beta APK from external users inspecting this repository, the `"update_url_encrypted"` field is AES-256 encrypted.
The private AES decryption key is embedded in the minified offline source code of the Android application. Only legitimate installations can decrypt the string back into the usable Google Drive download link.

## Maintainer Instructions

When a new version is built and uploaded to Google Drive:

1. Copy the public Google Drive Share link.
2. Open the local tool `crea_link_criptato.html` on your PC.
3. Paste the URL into the generator to compute the encrypted AES string.
4. Modify `version.json` in this repository:
   - Update `"latest_version"` to the new version (e.g., `"1.3.5"`)
   - Update `"update_url_encrypted"` with the new string.
5. Commit and push the changes. The game clients will now see the update automatically.
