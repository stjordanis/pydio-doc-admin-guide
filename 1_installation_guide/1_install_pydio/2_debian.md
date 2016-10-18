## 2.1) Create an account to grab your API Credentials

Our Enterprise Repositories are password-protected via API Key and API Secret. These are provided by default when you have a valid Pydio Enterprise License. By simply registering at pydio.com you can claim your free 10 users Licence! You can find them in your dashboard and will be instantly provisioned, so it's just a matter of minutes. Once you have it, you can find the Api Key and Api Secret at the bottom of your license page in your Dashboard:

[:image-popup:1_installation_guide/install_pydio_api_keys.png]


## 2.2) Install Repositories

### Debian 7,8 and Ubuntu 14.0.4: install additional packages, public key and repositories

Don't forget to update and upgrade your packages before !!

Install apt-transport-https package:

> `sudo apt-get install apt-transport-https`

Install our public key (used to sign the packages) using the following command:

> `wget -qO - https://download.pydio.com/pub/linux/debian/key/pubkey | sudo apt-key add -`

Then edit /etc/apt/sources.list and add the following lines by replacing API_KEY and API_SECRET by corresponding values retrieved from your pydio.com dashboard as seen in previous step.

### Debian 8
> `deb https://download.pydio.com/pub/linux/debian/ jessie-backports main`

> `deb https://API_KEY:API_SECRET@download.pydio.com/auth/linux/debian/ jessie-backports main non-free`

### Debian 7

> Debian 7 system requires keyring package:

> `sudo apt-get install debian-keyring debian-archive-keyring`

> `deb https://download.pydio.com/pub/linux/debian/ wheezy-backports main`

> `deb https://API_KEY:API_SECRET@download.pydio.com/auth/linux/debian/ wheezy-backports main non-free`

### Ubuntu 14.0.4

> `deb https://download.pydio.com/pub/linux/debian/ trusty main`

> `deb https://API_KEY:API_SECRET@download.pydio.com/auth/linux/debian/ trusty non-free`

Now update your repositories list by running:

> `sudo apt-get update`

## 2.3) Install Pydio Enterprise Distribution

Now that the repositories are properly configured, you simply have to install pydio using either:
> `sudo apt-get update`

> `sudo apt-get install pydio-core` or `apt-get install pydio-all`

> `sudo apt-get install pydio-enterprise`

After that step, you should be able to access pydio through your browser: http://YOUR_IP_ADDRESS/pydio/