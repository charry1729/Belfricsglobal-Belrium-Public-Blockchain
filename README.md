<h1><a id="Steps_to_setup_new_belrium_mining_node_0"></a>Steps to setup new belrium mining node:</h1>
<ol>
<li>Register and create wallet on <a href="http://app.belrium.io">app.belrium.io</a></li>
<li>Verify your email and activate your wallet.This information is purely confidential. Please do not disclose this with anyone.</li>
<li>You can now upload documents based on your geography and get your wallet compliance checked.Once your wallet is compliant you can start transacting on the belrium network.</li>
<li>Get the source code hosted at -</li>
</ol>
<pre><code>https://bitbucket.org/belfricscore/belriumnode
</code></pre>
<ol start="5">
<li>Run the following commands to install the required software dependencies.<br>
System Dependency<br>
nodejs v6.3+,npm 3.10+ (not cnpm),node-gyp v3.6.2+ (suggested),sqlite v3.8.2+,g++,libssl,</li>
</ol>
<h1><a id="Installation_dependencies_for_ubuntu_1404x_or_higher_using_bash_script_12"></a>Installation dependencies for ubuntu 14.04.x or higher using bash script.</h1>
<pre><code>   sudo ./belrium_manager.bash install
</code></pre>
<h1><a id="Installation_dependencies_for_ubuntu_1404x_or_higher_manually_16"></a>Installation dependencies for ubuntu 14.04.x or higher manually.</h1>
<h1><a id="Install_dependency_package_18"></a>Install dependency package</h1>
<pre><code>   sudo apt-get install curl sqlite3 ntp wget git libssl-dev openssl make gcc g++ autoconf automake python build-essential -y
</code></pre>
<h1><a id="libsodium_for_ubuntu_1404_22"></a>libsodium for ubuntu 14.04</h1>
<pre><code>   sudo apt-get install libtool -y
</code></pre>
<h1><a id="libsodium_for_ubuntu_1604_26"></a>libsodium for ubuntu 16.04</h1>
<pre><code>   sudo apt-get install libtool libtool-bin -y
</code></pre>
<h1><a id="Install_nvm_30"></a>Install nvm</h1>
<pre><code>   curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash
</code></pre>
<h1><a id="This_loads_nvm_34"></a>This loads nvm</h1>
<pre><code>export NVM_DIR=&quot;$HOME/.nvm&quot;
[ -s &quot;$NVM_DIR/nvm.sh&quot; ] &amp;&amp; \. &quot;$NVM_DIR/nvm.sh&quot; 
[ -s &quot;$NVM_DIR/bash_completion&quot; ] &amp;&amp; \. &quot;$NVM_DIR/bash_completion&quot; 
</code></pre>
<p>This loads nvm bash_completion</p>
<h1><a id="Install_node_and_npm_for_current_user_42"></a>Install node and npm for current user</h1>
<pre><code>   nvm install v8
</code></pre>
<h1><a id="Install_node_packages_46"></a>Install node packages</h1>
<pre><code>  npm install
</code></pre>
<ol start="6">
<li>To connect with the Belrium blockchain, new node need to change the setting file (Belrium-&gt;config.json) with following information.</li>
</ol>
<pre><code>{
    &quot;port&quot;: 4096,
    &quot;address&quot;: &quot;0.0.0.0&quot;,
    &quot;publicIp&quot;: &quot;&quot;,
    &quot;logLevel&quot;: &quot;debug&quot;,
    &quot;magic&quot;: &quot;594fe0f3&quot;,
    &quot;api&quot;: {
        &quot;access&quot;: {
            &quot;whiteList&quot;: []
        }
    },
    &quot;peers&quot;: {
        &quot;list&quot;: [{
            &quot;ip&quot;: &quot;52.66.157.170&quot;,
            &quot;port&quot;: 4200
        }],
        &quot;blackList&quot;: [],
        &quot;options&quot;: {
            &quot;timeout&quot;: 4000
        }
    },
    &quot;forging&quot;: {
        &quot;secret&quot;: [],
        &quot;access&quot;: {
            &quot;whiteList&quot;: [&quot;127.0.0.1&quot;]
        }
    },
    &quot;loading&quot;: {
        &quot;verifyOnLoading&quot;: false,
        &quot;loadPerIteration&quot;: 5000
    },
    &quot;ssl&quot;: {
        &quot;enabled&quot;: false,
        &quot;options&quot;: {
            &quot;port&quot;: 443,
            &quot;address&quot;: &quot;0.0.0.0&quot;,
            &quot;key&quot;: &quot;./ssl/server.key&quot;,
            &quot;cert&quot;: &quot;./ssl/server.crt&quot;
        }
    },
    &quot;dapp&quot;: {
        &quot;masterpassword&quot;: &quot;ytfACAMegjrK&quot;,
        &quot;params&quot;: {}
    },
    &quot;url&quot;: {
        &quot;kycUrl&quot;: &quot;&quot;
    }
}

</code></pre>
<ol start="7">
<li>Run the following script to start the node</li>
</ol>
<pre><code>./belrium_manager.bash start
</code></pre>
<ol start="8">
<li>Run the following command to stop the node</li>
</ol>
<pre><code>./belrium_manager.bash stop
</code></pre>
<ol start="9">
<li>Run the following script to know the status</li>
</ol>
<pre><code>./belrium_manager.bash status
</code></pre>
