# Using the Edge Apt repository

A simple guide to using this repository to install Edge nodes on your Linux based devices.

## Add the Edge repository to your sources

	$ echo "deb https://archive.edge.network/ /" > /etc/apt/sources.list.d/edge.list

### Import the public key for the repository

	$ wget -q -O - https://archive.edge.network/KEY.gpg | sudo apt-key add -

### Update Apt

	$ sudo apt update

### Install Edge packages

	$ sudo apt install helloworld
