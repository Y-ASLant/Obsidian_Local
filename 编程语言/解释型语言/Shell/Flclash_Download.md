# 摘要

> [!NOTE] 批量下载 Flclash 的软件包
# 源码
```sh
#!/bin/bash  
  
# Function to download files  
download_files() {  
    local version=$1  
    base_url="https://github.com/chen08209/FlClash/releases/download/v$version"  
    files=(  
        "FlClash-$version-android-arm64-v8a.apk"  
        "FlClash-$version-android-armv7.apk"  
        "FlClash-$version-android-x86_64.apk"  
        "FlClash-$version-linux-amd64.deb"  
        "FlClash-$version-linux-amd64.rpm"  
        "FlClash-$version-macos-arm64.dmg"  
        "FlClash-$version-windows-amd64-setup.exe"  
        "FlClash-$version-macos-amd64.dmg"  
        "FlClash-$version-linux-amd64.AppImage"  
    )  
  
    mkdir -p downloads/v"$version"  
  
    for file in "${files[@]}"; do  
        url="$base_url/$file"  
        echo "Downloading $file..."  
        curl -L -o "downloads/v$version/$file" "$url"  
        # shellcheck disable=SC2181  
        if [[ $? -eq 0 ]]; then  
            echo "Downloaded $file successfully."        else  
            echo "Failed to download $file."  
        fi  
    done}  
  
# Prompt the user to enter the version number  
# shellcheck disable=SC2162  
read -p "Enter the version number (e.g., 0.8.50): " version  
  
# Validate input  
if [[ ! $version =~ ^0\.8\.[0-9]+$ ]]; then  
    echo "Invalid version format. Please enter a version like 0.8.xx"  
    exit 1  
fi  
  
# Call the function to download files  
download_files "$version"

```