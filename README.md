# freetube-armhf-builds
Source code and arm64 builds available at https://github.com/FreeTubeApp/FreeTube

Finished armhf builds are available on the [Releases](https://github.com/Jai-JAP/freetube-armhf-builds/releases) page.

## To Compile FreeTube on armv7l
```
sudo apt inatall -y curl
#Install Node.js 16
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt install -y nodejs libarchive-tools ruby jq ruby build-essentials git
sudo gem install fpm --no-document

git clone https://github.com/FreeTubeApp/FreeTube -b $(curl "https://api.github.com/repos/FreeTubeApp/FreeTube/releases" | jq -r 'map(select(.prerelease)) | first | .tag_name' ) --single-branch
npm install
USE_SYSTEM_FPM=true npm run build:arm32

# Build artifacts will be in build subfolder```
