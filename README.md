# Steps to setup new belrium mining node:

1. Register and create wallet on app.belrium.io

2. Verify your email and activate your wallet.This information is purely confidential. Please do not disclose this with anyone.

3. You can now upload documents based on your geography and get your wallet compliance checked.Once your wallet is compliant you can start transacting on the belrium network.

4. Get the source code hosted at - https://bitbucket.org/belfricscore/belriumnode

5. Run the following commands to install the required software dependencies.
   System Dependency
   nodejs v6.3+,npm 3.10+ (not cnpm),node-gyp v3.6.2+ (suggested),sqlite v3.8.2+,g++,libssl,
# Installation dependencies for ubuntu 14.04.x or higher using bash script.

   sudo ./belrium_manager.bash install

# Installation dependencies for ubuntu 14.04.x or higher manually.

# Install dependency package
   sudo apt-get install curl sqlite3 ntp wget git libssl-dev openssl make gcc g++ autoconf automake python build-essential -y

# libsodium for ubuntu 14.04
   sudo apt-get install libtool -y

# libsodium for ubuntu 16.04
   sudo apt-get install libtool libtool-bin -y

# Install nvm
   curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash

# This loads nvm
   export NVM_DIR="$HOME/.nvm"

   [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" 

   [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion" 

   This loads nvm bash_completion

# Install node and npm for current user
   nvm install v8

# Install node packages
   npm install

6. To connect with the Belrium blockchain, new node need to change the setting file (Belrium->config.json) with following information.
{
	"port": 4096,
	"address": "0.0.0.0",
	"publicIp": "",
	"logLevel": "debug",
	"magic": "594fe0f3",
	"api": {
		"access": {
			"whiteList": []
		}
	},
	"peers": {
		"list": [{
			"ip": "52.66.157.170",
			"port": 4200
		}],
		"blackList": [],
		"options": {
			"timeout": 4000
		}
	},
	"forging": {
		"secret": [],
		"access": {
			"whiteList": ["127.0.0.1"]
		}
	},
	"loading": {
		"verifyOnLoading": false,
		"loadPerIteration": 5000
	},
	"ssl": {
		"enabled": false,
		"options": {
			"port": 443,
			"address": "0.0.0.0",
			"key": "./ssl/server.key",
			"cert": "./ssl/server.crt"
		}
	},
	"dapp": {
		"masterpassword": "ytfACAMegjrK",
		"params": {}
	},
	"url": {
		"kycUrl": ""
	}
}


7. Run the following script to start the node

./belrium_manager.bash start


8. Run the following command to stop the node

./belrium_manager.bash stop


9. Run the following script to know the status

./belrium_manager.bash status
