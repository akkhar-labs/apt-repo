# Akkhar-Labs APT repository

Debian/Ubuntu (amd64) packages for the [Nirdeshika SDK](https://github.com/Akkhar-Labs/nirdeshika-sdk).

```bash
echo "deb [trusted=yes] https://akkhar-labs.github.io/apt-repo/ stable main" | sudo tee /etc/apt/sources.list.d/nirdeshika.list
sudo apt-get update
sudo apt-get install nirdeshika-sdk
```

> This repository is not GPG-signed yet (hence `[trusted=yes]`).

Packages: `nirdeshika-sdk` 1.0.0.

## Regenerating indexes

```bash
dpkg-scanpackages --arch amd64 pool/ > dists/stable/main/binary-amd64/Packages
gzip -kf dists/stable/main/binary-amd64/Packages
apt-ftparchive -o APT::FTPArchive::Release::Suite=stable -o APT::FTPArchive::Release::Codename=stable \
  -o APT::FTPArchive::Release::Components=main -o APT::FTPArchive::Release::Architectures=amd64 \
  release dists/stable > dists/stable/Release
```
