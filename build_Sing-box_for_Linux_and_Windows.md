 Here's how you can use the `make` command to build Sing-box for Linux and Windows using the specified build tags and the `dev-next` branch:
```
sudo apt update
sudo apt install git make
```

Preparing the environment:
```
curl -sLo go.tar.gz https://go.dev/dl/$(curl -sL https://golang.org/VERSION?m=text|head -1).linux-amd64.tar.gz
rm -rf /usr/local/go
tar -C /usr/local/ -xzf go.tar.gz
rm go.tar.gz
echo -e "export PATH=$PATH:/usr/local/go/bin" > /etc/profile.d/go.sh
source /etc/profile.d/go.sh
go version
```
These commands download and install the latest version of Go in `/usr/local/go`, set up the Go environment variables, and verify the Go version.

Building for linux-amd64:
```
git clone https://github.com/SagerNet/sing-box.git
cd sing-box
git checkout dev-next
TAGS="with_wireguard with_quic with_ech with_reality_server" CGO_ENABLED=0 GOOS=linux GOARCH=amd64 GOAMD64=v2 make
```
This command clones the Sing-box repository, switches to the `dev-next` branch, sets the build tags and Go environment variables for building a static binary for Linux with AMD64 architecture and AMD64 version 2, and then runs the `make` command to build the binary.

Building for windows-amd64:
```
git clone https://github.com/SagerNet/sing-box.git
cd sing-box
git checkout dev-next
TAGS="with_gvisor with_clash_api with_quic with_utls with_ech with_reality_server" CGO_ENABLED=0 GOOS=windows GOARCH=amd64 GOAMD64=v3 make
```
This command clones the Sing-box repository, switches to the `dev-next` branch, sets the build tags and Go environment variables for building a static binary for Windows with AMD64 architecture and AMD64 version 3, and then runs the `make` command to build the binary.

Copying the binary:

For linux-amd64:
```
cp -f sing-box /usr/local/bin/
chmod +x /usr/local/bin/sing-box
```
This command copies the built Sing-box binary to `/usr/local/bin/` and makes it executable.

For windows-amd64:
```
cp -f sing-box.exe /path/to/destination/
```
This command copies the built Sing-box binary for Windows to the desired destination directory.

By using the `make` command with the specified build tags and Go environment variables, you can build Sing-box for Linux and Windows using the `dev-next` branch.

Note: Make sure you have `git` and `make` installed on your system before running these commands.

Remember to replace `/path/to/destination/` with the actual directory where you want to copy the Windows binary.
