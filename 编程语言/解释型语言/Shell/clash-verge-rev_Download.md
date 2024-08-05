
> [!NOTE] clash-verge-rev 版本批量下载

```sh
#!/bin/bash

# Function to download files
download_files() {
    local version=$1
    base_url="https://github.com/clash-verge-rev/clash-verge-rev/releases/download/v$version"
    files=(
        "Clash.Verge_"$version"_x64-setup.exe"
        "Clash.Verge_"$version"_x86-setup.exe"
        "Clash.Verge_"$version"_x64.dmg"
        "clash-verge_"$version"_amd64.deb"
        "clash-verge-"$version"-1.x86_64.rpm"
    )

    mkdir -p downloads/v"$version"

    for file in "${files[@]}"; do
        url="$base_url/$file"
        echo "Downloading $file..."
        curl -L -o "downloads/v$version/$file" "$url"
        # shellcheck disable=SC2181
        if [[ $? -eq 0 ]]; then
            echo "Downloaded $file successfully."
            echo ""
            echo ""
            echo ""
        else
            echo "Failed to download $file."
        fi
    done
}

# Prompt the user to enter the version number
# shellcheck disable=SC2162
read -p "Enter the version number (e.g., 1.7.5): " version

# Validate input
if [[ ! $version =~ ^1\.7\.[0-9]+$ ]]; then
    echo "Invalid version format. Please enter a version like 1.7.xx"
    exit 1
fi

# Call the function to download files
download_files "$version"

```