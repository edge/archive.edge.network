# Building the Edge Apt repository

Instructions for building the `archive.edge.network` apt repository.

## Storing your `.deb` files

Add Edge deb files to the public Git repository at [https://github.com/edge/archive.edge.network](https://github.com/edge/archive.edge.network) under the appropriate architechture folder (e.g. `amd64`).

## Building the repository on `archive.edge.network`

### Move to the repo folder

	$ cd /edge/archive/

### Pull the latest build of the repository

	$ git pull origin master

### Update the Packages files (setting `-m` for multiversion)

	$ sudo dpkg-scanpackages -m . > Packages

### gZip the updated Packages file

	$ gzip -k -f Packages

### Update the `Release` file

	$ apt-ftparchive release . > Release

### Refresh the `Release.gpg` file

	$ rm -fr Release.gpg; gpg --default-key ${KEYNAME} -abs -o Release.gpg Release

Note: you will need the password for the public key.

### Update the `InRelease` file

	$ rm -fr InRelease; gpg --default-key ${KEYNAME} --clearsign -o InRelease Release
