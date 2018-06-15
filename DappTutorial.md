Dapp Development Tutorial 1: bel Dapp Hello World


<h1><a id="1_Basic_Process_0"></a>1 Basic Process</h1>
<p>There are three types of networks in bel<br>
1. localnet,<br>
2. testnet,<br>
3. mainnet.</p>
<p>The later two, testnet and mainnet, are usually deployed online, which can be accessed by a public network.</p>
<p>Meanwhile the first type, localnet, as its name is running on local machine, which is actually a private chain with only one node.<br>
Localnet is designed to help developing and testing locally.</p>
<p>And the development of Dapp involves all of these types of network simultaneously, which is:<br>
step 1: developing and testing locally on the localnet<br>
step 2: testing on the testnet<br>
step 3: deploying officially on mainnet</p>
<h2><a id="11_System_requirements_17"></a>1.1 System requirements</h2>
<p>Node v8.x.x</p>
<h2><a id="2_Setup_belcli_20"></a>2 Setup bel-cli</h2>
<pre><code>npm install -g bel-cli
</code></pre>
<h2><a id="2_Setup_bel__clone_bel_25"></a>2 Setup bel # clone bel</h2>
<pre><code>git clone https://github.com/belplatform/bel.git bel &amp;&amp; cd bel &amp;&amp; npm install &amp;&amp; cd ..
</code></pre>
<h2><a id="4_Start_localnet_30"></a>4 Start localnet</h2>
<p>Run your own local bel node.</p>
<h1><a id="change_directory_33"></a>change directory</h1>
<pre><code>cd bel
</code></pre>
<h1><a id="start_the_localnet_default_on_localhost4096_38"></a>start the localnet (default on localhost:4096)</h1>
<pre><code>node app.js
</code></pre>
<h2><a id="4_Start_The_Frontend_Application_optional_43"></a>4 Start The Frontend Application (optional)</h2>
<p>To access the localnet via a graphical user interface (GUI) start the frontend application.<br>
Be sure to have the localnet up and running.</p>
<p>This step must be run from another console. The first console is already busy with running the localnet.</p>
<h1><a id="change_directory_49"></a>change directory</h1>
<pre><code>cd bel/public
</code></pre>
<p>Install the dependencies for the frontend application</p>
<pre><code>yarn install
</code></pre>
<p>Build the frontend application for the localnet.</p>
<pre><code>gulp build-local
</code></pre>
<p>Now you can access the frontend application on the address <code>localhost:4096</code>.</p>
<p><em>NOTE:</em> You don’t need to start a http-server. bel is already providing one for you.</p>
<h2><a id="5_Prepare_Account_For_Dapp_Registration_67"></a>5 Prepare Account For Dapp Registration</h2>
<p>First create a new local bel-account.</p>
<h1><a id="execute_in_root_folder_70"></a>execute (in root folder)</h1>
<pre><code>&gt; bel-cli -H 127.0.0.1 -P 4096 crypto --generate
</code></pre>
<h1><a id="_Enter_number_of_accounts_to_generate___1_74"></a>? Enter number of accounts to generate:   1</h1>
<p><strong>Our New Account</strong></p>
<pre><code>address: AHMCKebuL2nRYDgszf9J2KjVZzAw95WUyB
secret: sentence weasel match weather apple onion release keen lens deal fruit matrix
publicKey: a7cfd49d25ce247568d39b17fca221d9b2ff8402a9f6eb6346d2291a5c81374c
</code></pre>
<p><strong>Genesis Account</strong></p>
<pre><code>address: 14762548536863074694
secret: someone manual strong movie roof episode eight spatial brown soldier soup motor
publicKey: 8065a105c785a08757727fded3a06f8f312e73ad40f1f3502e0232ea42e67efd
</code></pre>
<p><strong>Our new Acccount</strong> will be our account for this tutorial.</p>
<p>We need <strong>100 BEL</strong> to register a dapp.<br>
Our new account has <strong>0 BEL</strong>. The <strong>genesis</strong> account has 100000000 BEL on it.<br>
Lets send some money to <strong>our</strong> account.</p>
<h1><a id="send_money_to_our_account_95"></a>send money to our account</h1>
<pre><code>&gt; bel-cli -H 127.0.0.1 -P 4096 sendmoney --secret &quot;someone manual strong movie roof episode eight spatial brown soldier soup motor&quot; --to
&quot;AHMCKebuL2nRYDgszf9J2KjVZzAw95WUyB&quot; --amount 100000000000
</code></pre>
<h1><a id="check_your_balance_101"></a>check your balance</h1>
<pre><code>&gt; bel-cli -H 127.0.0.1 -P 4096 openaccount &quot;sentence weasel match weather apple onion release keen lens deal fruit matrix&quot;
</code></pre>
<h2><a id="6_Create_A_Dapp_Metadata_File_105"></a>6 Create A Dapp Metadata File</h2>
<p>First we have to create 5 delegate accounts:</p>
<h1><a id="execute_in_root_you_dont_have_to_point_to_the_localhost_this_command_is_execute_only_in_belcli_108"></a>execute in root (you don’t have to point to the localhost, this command is execute only in bel-cli)</h1>
<pre><code>&gt; bel-cli crypto --generate
? Enter number of accounts to generate     5

[{
        address: 'AN1yKK47P3MtD5ZgHYoncGQ1gCn4p2vGAC',
        secret: 'flame bottom dragon rely endorse garage supply urge turtle team demand put',
        publicKey: 'db18d5799944030f76b6ce0879b1ca4b0c2c1cee51f53ce9b43f78259950c2fd'
    },
    {
        address: 'AGeeCmSVLDNbtMqqpJchQZakchwzpuje1P',
        secret: 'thrive veteran child enforce puzzle buzz valley crew genuine basket start top',
        publicKey: '590e28d2964b0aa4d7c7b98faee4676d467606c6761f7f41f99c52bb4813b5e4'
    },
    {
        address: 'A7NWaYUkpa543hdTsfw57AoZAgCBr2NFY6',
        secret: 'black tool gift useless bring nothing huge vendor asset mix chimney weird',
        publicKey: 'bfe511158d674c3a1e21111223a49770bee93611d998e88a5d2ea3145de2b68b'
    },
    {
        address: 'ABU1G2pQFMGa7c1GiAPYCQuUhiPHdvCSB2',
        secret: 'ribbon crumble loud chief turn maid neglect move day churn share fabric',
        publicKey: '7bbf62931cf3c596591a580212631aff51d6bc0577c54769953caadb23f6ab00'
    },
    {
        address: 'AG1A3ojeLAMZySaZWTkg49jcoVCV7FCKXF',
        secret: 'scan prevent agent close human pair aerobic sad forest wave toe dust',
        publicKey: '452df9213aedb3b9fed6db3e2ea9f49d3db226e2dac01828bc3dcd73b7a953b4'
    }
]
</code></pre>
<p>After that enter your bel source code folder and make sure the localnet is running.</p>
<h1><a id="this_must_be_executed_in_a_new_console_142"></a>this must be executed in a new console</h1>
<pre><code>&gt; mkdir bel-test-dapp &amp;&amp; cd bel-test-dapp
&gt; bel-cli dapps -a

# enter dapp name?
codehello

# enter dapp description?
[empty]

# enter dapp tags?
[empty]

# choose dapp category
1

# enter dapp link
https://github.com/belPlatform/bel-dapp-helloworld/archive/master.zip

# enter dapp icon url
http://o7dyh3w0x.bkt.clouddn.com/hello.png

# enter public keys of dapp delegates - hex array, use ',' for separator (at least 5 delegates, max 101):
db18d5799944030f76b6ce0879b1ca4b0c2c1cee51f53ce9b43f78259950c2fd,590e28d2964b0aa4d7c7b98faee4676d467606c6761f7f41f99c52bb4813b5e4,bfe511158d674c3a1e21111223a49770bee93611d998e88a5d2ea3145de2b68b,7bbf62931cf3c596591a580212631aff51d6bc0577c54769953caadb23f6ab00,452df9213aedb3b9fed6db3e2ea9f49d3db226e2dac01828bc3dcd73b7a953b4

# how many delegates are needed to unlock asset of a dapp?
3

# Enter master secret of your genesis account
[hidden]

# Do you want publish a inbuilt asset in this dapp?
No
This step created the `bel-test-dapp/dapp.json` file.

{
    &quot;name&quot;: &quot;hello&quot;,
    &quot;link&quot;: &quot;https://bitbucket.org/belfricscorebel-hello-dapp/archive/master.zip&quot;,
    &quot;category&quot;: 1,
    &quot;description&quot;: &quot;&quot;,
    &quot;tags&quot;: &quot;&quot;,
    &quot;icon&quot;: &quot;http://o7dyh3w0x.bkt.clouddn.com/hello.png&quot;,
    &quot;delegates&quot;: [
        &quot;db18d5799944030f76b6ce0879b1ca4b0c2c1cee51f53ce9b43f78259950c2fd&quot;,
        &quot;590e28d2964b0aa4d7c7b98faee4676d467606c6761f7f41f99c52bb4813b5e4&quot;,
        &quot;bfe511158d674c3a1e21111223a49770bee93611d998e88a5d2ea3145de2b68b&quot;,
        &quot;7bbf62931cf3c596591a580212631aff51d6bc0577c54769953caadb23f6ab00&quot;,
        &quot;452df9213aedb3b9fed6db3e2ea9f49d3db226e2dac01828bc3dcd73b7a953b4&quot;
    ],
    &quot;unlockDelegates&quot;: 3,
    &quot;type&quot;: 0
}
</code></pre>
<h2><a id="6_Register_The_Dapp_On_The_Localnet_196"></a>6 Register The Dapp On The Localnet</h2>
<p>Until now we only have generated file (<code>bel-test-dapp/dapp.json</code>). Now we want to register this dapp metadata file on the localnet. We register the dapp with <strong>our</strong> newly generated address.</p>
<h1><a id="execute_in_beldapps_200"></a>execute (in bel/dapps)</h1>
<pre><code>bel-cli -H 127.0.0.1 -P 4096 registerdapp --metafile dapp.json --secret &quot;sentence weasel match weather apple onion release keen lens deal fruit matrix&quot;
</code></pre>
<p><strong>Result</strong></p>
<h1><a id="This_returns_the_new_DappID_206"></a>This returns the new Dapp-ID</h1>
<p>Now navigate in your browser to <code>localhost:4096</code>. Login with <strong>our</strong> new created account. Under dapps you should see the register dapps.</p>
<p>Use browser access <code>http://localhost:4096/api/dapps/get?id=</code>,<br>
you can query the dapp, the following is the return information:</p>
<pre><code>{
    &quot;success&quot;: true,
    &quot;dapp&quot;: {
        &quot;name&quot;: &quot;bel-dapp-helloworld&quot;,
        &quot;description&quot;: &quot;A hello world demo for bel dapp&quot;,
        &quot;tags&quot;: &quot;bel,dapp,demo&quot;,
        &quot;link&quot;: &quot;https://bitbucket.org/belfricscore/bel-dapp-helloworld/archive/master.zip&quot;,
        &quot;type&quot;: 0,
        &quot;category&quot;: 1,
        &quot;icon&quot;: &quot;http://o7dyh3w0x.bkt.clouddn.com/hello.png&quot;,
        &quot;delegates&quot;: [
            &quot;a518e4390512e43d71503a02c9912413db6a9ffac4cbefdcd25b8fa2a1d5ca27&quot;,
            &quot;c7dee266d5c85bf19da8fab1efc93204fed7b35538a3618d7f6a12d022498cab&quot;,
            &quot;9cac187d70713b33cc4a9bf3ff4c004bfca94802aed4a32e2f23ed662161ea50&quot;,
            &quot;01944ce58570592250f509214d29171a84f0f9c15129dbea070251512a08f5cc&quot;,
            &quot;f31d61066c902bebc80155fed318200ffbcfc97792511ed18d85bd5af666639f&quot;
        ],
        &quot;unlockDelegates&quot;: 3,
        &quot;transactionId&quot;: &quot;0599a6100280df0d296653e89177b9011304d971fb98aba3edcc5b937c4183fb&quot;
    }
}
</code></pre>
<h2><a id="7_Install_the_dapp_on_the_localnet_234"></a>7 Install the dapp on the localnet</h2>
<p>Finally it is time to install the dapp on the localnet.</p>
<p>First we copy the files created in previous step to the dapp subdirectory<br>
under the bel installation directory and rename it to dapp’s id:</p>
<pre><code>&gt; cp -r bel-test-dapp path/to/bel/dapps/0599a6100280df0d296653e89177b9011304d971fb98aba3edcc5b937c4183fb
</code></pre>
<p>then:</p>
<h1><a id="execute_244"></a>execute</h1>
<pre><code>bel-cli -H 127.0.0.1 -P 4096 dapps --install
# ? Enter dapp id
# (input your dapp Id)
# ? Host and port (localhost:4096)
# [Enter]
# ? What is your dapp master password
#
</code></pre>
<p>The dapp masterpassword is located in <code>bel/config.json</code>.</p>
<p>“dapp”: {<br>
“masterpassword”: “ytfACAMegjrK”,<br>
“params”: {<br>
“”: []<br>
}</p>
<p>Then write the passwords of the 5 delegates into the dapp configuration file <code>bel/dapps/ /config.json</code>.</p>
<h1><a id="configjson_264"></a>config.json</h1>
<p>{<br>
“secrets”: [<br>
“flame bottom dragon rely endorse garage supply urge turtle team demand put”,<br>
“thrive veteran child enforce puzzle buzz valley crew genuine basket start top”,<br>
“black tool gift useless bring nothing huge vendor asset mix chimney weird”,<br>
“ribbon crumble loud chief turn maid neglect move day churn share fabric”,<br>
“scan prevent agent close human pair aerobic sad forest wave toe dust”<br>
]<br>
}</p>
<p><strong>After the installation restart the node</strong></p>
<h1><a id="stop_the_localnet_with_Ctrl__C_278"></a>stop the localnet with Ctrl + C</h1>
<h1><a id="restart_the_localnet_279"></a>restart the localnet</h1>
<blockquote>
<p>node app.js</p>
</blockquote>
<h2><a id="8_Access_The_Dapp_In_Your_Browser_282"></a>8 Access The Dapp In Your Browser</h2>
<p>Now you can access the dapp like a website <code>localhost:4096/dapps/ /</code> in your browser.</p>
<h2><a id="9_Set_Dapp_Genesis_Password_285"></a>9 Set Dapp Genesis Password</h2>
<p>Under <code>bel/config.json</code> set the genesis password for your dapp. Input your <code></code> and the secret of your<br>
<strong>before</strong></p>
<p>“dapp”: {<br>
“masterpassword”: “ytfACAMegjrK”,<br>
“params”: {}<br>
}</p>
<p><strong>after</strong></p>
<p>“dapp”: {<br>
“masterpassword”: “ytfACAMegjrK”,<br>
“params”: {<br>
&quot; &quot;: [<br>
“sentence weasel match weather apple onion release keen lens deal fruit matrix”<br>
]<br>
}<br>
}</p>
<p>In the future when the DApp is published in testnet or mainnet,<br>
it still needs a machine that configures the primary password. NOTE: Only one machine is required.</p>
<h2><a id="10_The_folder_structure_308"></a>10 The folder structure</h2>
<p>Now we can see that there is a new folder added under <code>bel/dapps</code>, named as the DApp ID just created.</p>
<blockquote>
<p>ls -la dapps/<br>
dapps<br>
└─── dapp id<br>
└─── blockchain.json # the database description of DApp</p>
</blockquote>
<pre><code>└─── config.json # the configuration file of DApp, which mainly contains the list of seed nodes. Developers can also add other configurations in it.

└─── dapp.json # the meta information of DApp, including name, description, source code package, and etc. This file can also be used when registering the app to other networks.

└─── genesis.json # indicate the genesis blcok. This file is generated by CLI automatically, but also can be written by yourself, by which the assets of genesis account can be distributed with more flexibility.

└─── index.js # this file contains the entry of DApp

└─── init.js # this file contains the initial code of each module.

└─── LICENSE # this file describes the permit license of source code
└─── .
</code></pre>
<p>modules # main code</p>
<pre><code>└─── modules.full.json # this file indicates all the modules need to be loaded. You can add other necessary modules here.
</code></pre>
<p>modules.genesis.json # (the simplified version of modules.full.json, currently not need)<br>
node_modules #<br>
public # this folders contains all front-end files<br>
routes.json # this file contains the configuration of http route. If you want to add new interface, you need to revise this file.<br>
Don’t worry about the complexity of the file structure. For now a first look is enough.</p>
<p>All the essential files for developers can be found in <code>modules/contracts/</code><br>
There are 4 build-in contract types in this folder:</p>
<blockquote>
<p>ls -1 dapps/ /modules/contracts/<br>
dapps</p>
</blockquote>
<p>└─── dapp id</p>
<p>└───modules</p>
<p>└───contracts</p>
<p>delegates.js # registering delegate contract<br>
insidetransfer.js # in-chain transfer contract<br>
outsidetransfer.js # BEL deposit contract<br>
withdrawaltransfer.js # BEL withdraw contract<br>
Developers need to create a new contact to run business logic. That’s all.</p>
<h2><a id="11_Dapp_Deposit_355"></a>11 Dapp Deposit</h2>
<p>In this project, we are able to conduct multiple tasks such as deposit, in-chain transfer, and withdraw. Currently deposit can only be executed via command line (this feature will be built into the main wallet in the future).</p>
<blockquote>
<p>bel-cli dapps --deposit<br>
? Enter secret *******************************************************************************</p>
</blockquote>
<p>? Enter amount 100</p>
<p>? DApp Id 6299140990391157236</p>
<p>? Enter secondary secret (if defined)</p>
<p>? Host and port localhost:4096</p>
<p>null { success: true, transactionId: ‘10589988261732949004’ }</p>
<p>10589988261732949004</p>
<p>In the web wallet (<code>localhost:4096</code>) we can see (after approximately 30 seconds) that the balance was updated.e are three types of networks in bel, localnet, testnet, and mainnet. The later two, testnet and mainnet, are usually deployed online, which can be accessed by a public network. Meanwhile the first type, localnet, as its name is running on local machine, which is actually a private chain with only one node. Localnet is designed to help developing and testing locally.</p>
<p>And the development of Dapp involves all of these types of network simultaneously, which is:<br>
step 1: developing and testing locally on the localnet<br>
step 2: testing on the testnet<br>
step 3: deploying officially on mainnet</p>
<h3><a id="11_System_requirements_379"></a>1.1 System requirements</h3>
<ul>
<li>Node v8.x.x</li>
</ul>
<h2><a id="2_Setup_belcli_381"></a>2 Setup bel-cli</h2>
<p>npm install -g bel-cli</p>
<h2><a id="2_Setup_bel_383"></a>2 Setup bel</h2>
<h1><a id="clone_bel_384"></a>clone bel</h1>
<p>git clone <a href="https://github.com/belplatform/bel.git">https://github.com/belplatform/bel.git</a> bel &amp;&amp; cd bel &amp;&amp; npm install &amp;&amp; cd …</p>
<h2><a id="4_Start_localnet_386"></a>4 Start localnet</h2>
<p>Run your own local bel node.</p>
<h1><a id="change_directory_389"></a>change directory</h1>
<p>cd bel</p>
<h1><a id="start_the_localnet_default_on_localhost4096_391"></a>start the localnet (default on localhost:4096)</h1>
<p>node app.js</p>
<h2><a id="4_Start_The_Frontend_Application_optional_393"></a>4 Start The Frontend Application (optional)</h2>
<p>To access the localnet via a graphical user interface (GUI) start the frontend application. Be sure to have the localnet up and running.</p>
<p>This step must be run from another console. The first console is already busy with running the localnet.</p>
<h1><a id="change_directory_398"></a>change directory</h1>
<p>cd bel/public<br>
Install the dependencies for the frontend application</p>
<p>yarn install<br>
Build the frontend application for the localnet.</p>
<p>gulp build-local<br>
Now you can access the frontend application on the address <code>localhost:4096</code>.</p>
<p><em>NOTE:</em> You don’t need to start a http-server. bel is already providing one for you.</p>
<h2><a id="5_Prepare_Account_For_Dapp_Registration_410"></a>5 Prepare Account For Dapp Registration</h2>
<p>First create a new local bel-account.</p>
<h1><a id="execute_in_root_folder_413"></a>execute (in root folder)</h1>
<blockquote>
<p>bel-cli -H 127.0.0.1 -P 4096 crypto --generate</p>
</blockquote>
<h1><a id="_Enter_number_of_accounts_to_generate_415"></a>? Enter number of accounts to generate:</h1>
<p>1<br>
<strong>Our New Account</strong></p>
<p>address: AHMCKebuL2nRYDgszf9J2KjVZzAw95WUyB<br>
secret: sentence weasel match weather apple onion release keen lens deal fruit matrix<br>
publicKey: a7cfd49d25ce247568d39b17fca221d9b2ff8402a9f6eb6346d2291a5c81374c<br>
<strong>Genesis Account</strong></p>
<p>address: 14762548536863074694<br>
secret: someone manual strong movie roof episode eight spatial brown soldier soup motor<br>
publicKey: 8065a105c785a08757727fded3a06f8f312e73ad40f1f3502e0232ea42e67efd<br>
<strong>Our new Acccount</strong> will be our account for this tutorial.</p>
<p>We need <strong>100 BEL</strong> to register a dapp. Our new account has <strong>0 BEL</strong>. The <strong>genesis</strong> account has 100000000 BEL on it. Lets send some money to <strong>our</strong> account.</p>
<h1><a id="send_money_to_our_account_431"></a>send money to our account</h1>
<blockquote>
<p>bel-cli -H 127.0.0.1 -P 4096 sendmoney --secret “someone manual strong movie roof episode eight spatial brown soldier soup motor” --to<br>
“AHMCKebuL2nRYDgszf9J2KjVZzAw95WUyB” --amount 100000000000</p>
</blockquote>
<h1><a id="check_your_balance_434"></a>check your balance</h1>
<blockquote>
<p>bel-cli -H 127.0.0.1 -P 4096 openaccount “sentence weasel match weather apple onion release keen lens deal fruit matrix”</p>
</blockquote>
<h2><a id="6_Create_A_Dapp_Metadata_File_436"></a>6 Create A Dapp Metadata File</h2>
<p>First we have to create 5 delegate accounts:</p>
<h1><a id="execute_in_root_you_dont_have_to_point_to_the_localhost_this_command_is_execute_only_in_belcli_439"></a>execute in root (you don’t have to point to the localhost, this command is execute only in bel-cli)</h1>
<blockquote>
<p>bel-cli crypto --generate<br>
? Enter number of accounts to generate<br>
5<br>
[<br>
{<br>
address: ‘AN1yKK47P3MtD5ZgHYoncGQ1gCn4p2vGAC’,<br>
secret: ‘flame bottom dragon rely endorse garage supply urge turtle team demand put’,<br>
publicKey: ‘db18d5799944030f76b6ce0879b1ca4b0c2c1cee51f53ce9b43f78259950c2fd’<br>
},<br>
{<br>
address: ‘AGeeCmSVLDNbtMqqpJchQZakchwzpuje1P’,<br>
secret: ‘thrive veteran child enforce puzzle buzz valley crew genuine basket start top’,<br>
publicKey: ‘590e28d2964b0aa4d7c7b98faee4676d467606c6761f7f41f99c52bb4813b5e4’<br>
},<br>
{<br>
address: ‘A7NWaYUkpa543hdTsfw57AoZAgCBr2NFY6’,<br>
secret: ‘black tool gift useless bring nothing huge vendor asset mix chimney weird’,<br>
publicKey: ‘bfe511158d674c3a1e21111223a49770bee93611d998e88a5d2ea3145de2b68b’<br>
},<br>
{<br>
address: ‘ABU1G2pQFMGa7c1GiAPYCQuUhiPHdvCSB2’,<br>
secret: ‘ribbon crumble loud chief turn maid neglect move day churn share fabric’,<br>
publicKey: ‘7bbf62931cf3c596591a580212631aff51d6bc0577c54769953caadb23f6ab00’<br>
},<br>
{<br>
address: ‘AG1A3ojeLAMZySaZWTkg49jcoVCV7FCKXF’,<br>
secret: ‘scan prevent agent close human pair aerobic sad forest wave toe dust’,<br>
publicKey: ‘452df9213aedb3b9fed6db3e2ea9f49d3db226e2dac01828bc3dcd73b7a953b4’<br>
}<br>
]<br>
After that enter your bel source code folder and make sure the localnet is running.</p>
</blockquote>
<h1><a id="this_must_be_executed_in_a_new_console_472"></a>this must be executed in a new console</h1>
<blockquote>
<p>mkdir bel-test-dapp &amp;&amp; cd bel-test-dapp<br>
bel-cli dapps -a</p>
</blockquote>
<h1><a id="enter_dapp_name_475"></a>enter dapp name?</h1>
<p>codehello</p>
<h1><a id="enter_dapp_description_477"></a>enter dapp description?</h1>
<p>[empty]</p>
<h1><a id="enter_dapp_tags_479"></a>enter dapp tags?</h1>
<p>[empty]</p>
<h1><a id="choose_dapp_category_481"></a>choose dapp category</h1>
<p>1</p>
<h1><a id="enter_dapp_link_483"></a>enter dapp link</h1>
<p><a href="https://github.com/belPlatform/bel-dapp-helloworld/archive/master.zip">https://github.com/belPlatform/bel-dapp-helloworld/archive/master.zip</a></p>
<h1><a id="enter_dapp_icon_url_485"></a>enter dapp icon url</h1>
<p><a href="http://o7dyh3w0x.bkt.clouddn.com/hello.png">http://o7dyh3w0x.bkt.clouddn.com/hello.png</a></p>
<h1><a id="enter_public_keys_of_dapp_delegates__hex_array_use__for_separator_at_least_5_delegates_max_101_487"></a>enter public keys of dapp delegates - hex array, use ‘,’ for separator (at least 5 delegates, max 101):</h1>
<p>db18d5799944030f76b6ce0879b1ca4b0c2c1cee51f53ce9b43f78259950c2fd,590e28d2964b0aa4d7c7b98faee4676d467606c6761f7f41f99c52bb4813b5e4,bfe511158d674c3a1e21111223a49770bee93611d998e88a5d2ea3145de2b68b,7bbf62931cf3c596591a580212631aff51d6bc0577c54769953caadb23f6ab00,452df9213aedb3b9fed6db3e2ea9f49d3db226e2dac01828bc3dcd73b7a953b4</p>
<h1><a id="how_many_delegates_are_needed_to_unlock_asset_of_a_dapp_489"></a>how many delegates are needed to unlock asset of a dapp?</h1>
<p>3</p>
<h1><a id="Enter_master_secret_of_your_genesis_account_491"></a>Enter master secret of your genesis account</h1>
<p>[hidden]</p>
<h1><a id="Do_you_want_publish_a_inbuilt_asset_in_this_dapp_493"></a>Do you want publish a inbuilt asset in this dapp?</h1>
<p>No<br>
This step created the <code>bel-test-dapp/dapp.json</code> file.<br>
{<br>
“name”: “hello”,<br>
“link”: &quot;<a href="https://bitbucket.org/belfricscorebel-hello-dapp/archive/master.zip">https://bitbucket.org/belfricscorebel-hello-dapp/archive/master.zip</a><br>
“category”: 1,<br>
“description”: “”,<br>
“tags”: “”,<br>
“icon”: &quot;<a href="http://o7dyh3w0x.bkt.clouddn.com/hello.png">http://o7dyh3w0x.bkt.clouddn.com/hello.png</a>&quot;,<br>
“delegates”: [<br>
“db18d5799944030f76b6ce0879b1ca4b0c2c1cee51f53ce9b43f78259950c2fd”,<br>
“590e28d2964b0aa4d7c7b98faee4676d467606c6761f7f41f99c52bb4813b5e4”,<br>
“bfe511158d674c3a1e21111223a49770bee93611d998e88a5d2ea3145de2b68b”,<br>
“7bbf62931cf3c596591a580212631aff51d6bc0577c54769953caadb23f6ab00”,<br>
“452df9213aedb3b9fed6db3e2ea9f49d3db226e2dac01828bc3dcd73b7a953b4”<br>
],<br>
“unlockDelegates”: 3,<br>
“type”: 0<br>
}</p>
<h2><a id="6_Register_The_Dapp_On_The_Localnet_513"></a>6 Register The Dapp On The Localnet</h2>
<p>Until now we only have generated file (<code>bel-test-dapp/dapp.json</code>). Now we want to register this dapp metadata file on the localnet. We register the dapp with <strong>our</strong> newly generated address.</p>
<h1><a id="execute_in_beldapps_515"></a>execute (in bel/dapps)</h1>
<blockquote>
<p>bel-cli -H 127.0.0.1 -P 4096 registerdapp --metafile dapp.json --secret “sentence weasel match weather apple onion release keen lens deal fruit matrix”<br>
<strong>Result</strong></p>
</blockquote>
<h1><a id="This_returns_the_new_DappID_519"></a>This returns the new Dapp-ID</h1>
<p>Now navigate in your browser to <code>localhost:4096</code>. Login with <strong>our</strong> new created account. Under dapps you should see the register dapps.</p>
<p>Use browser access <code>http://localhost:4096/api/dapps/get?id=</code>, you can query the dapp, the following is the return information:</p>
<p>{<br>
“success”: true,<br>
“dapp”: {<br>
“name”: “bel-dapp-helloworld”,<br>
“description”: “A hello world demo for bel dapp”,<br>
“tags”: “bel,dapp,demo”,<br>
“link”: &quot;<a href="https://bitbucket.org/belfricscore/bel-dapp-helloworld/archive/master.zip">https://bitbucket.org/belfricscore/bel-dapp-helloworld/archive/master.zip</a>&quot;,<br>
“type”: 0,<br>
“category”: 1,<br>
“icon”: &quot;<a href="http://o7dyh3w0x.bkt.clouddn.com/hello.png">http://o7dyh3w0x.bkt.clouddn.com/hello.png</a>&quot;,<br>
“delegates”: [<br>
“a518e4390512e43d71503a02c9912413db6a9ffac4cbefdcd25b8fa2a1d5ca27”,<br>
“c7dee266d5c85bf19da8fab1efc93204fed7b35538a3618d7f6a12d022498cab”,<br>
“9cac187d70713b33cc4a9bf3ff4c004bfca94802aed4a32e2f23ed662161ea50”,<br>
“01944ce58570592250f509214d29171a84f0f9c15129dbea070251512a08f5cc”,<br>
“f31d61066c902bebc80155fed318200ffbcfc97792511ed18d85bd5af666639f”<br>
],<br>
“unlockDelegates”: 3,<br>
“transactionId”: “0599a6100280df0d296653e89177b9011304d971fb98aba3edcc5b937c4183fb”<br>
}<br>
}</p>
<h2><a id="7_Install_the_dapp_on_the_localnet_545"></a>7 Install the dapp on the localnet</h2>
<p>Finally it is time to install the dapp on the localnet.</p>
<p>First we copy the files created in previous step to the dapp subdirectory under the bel installation directory and rename it to dapp’s id:</p>
<blockquote>
<p>cp -r bel-test-dapp path/to/bel/dapps/0599a6100280df0d296653e89177b9011304d971fb98aba3edcc5b937c4183fb<br>
then:</p>
</blockquote>
<h1><a id="execute_551"></a>execute</h1>
<p>bel-cli -H 127.0.0.1 -P 4096 dapps --install</p>
<h1><a id="_Enter_dapp_id_553"></a>? Enter dapp id</h1>
<h1><a id="input_your_dapp_Id_554"></a>(input your dapp Id)</h1>
<h1><a id="_Host_and_port_localhost4096_555"></a>? Host and port (localhost:4096)</h1>
<h1><a id="Enter_556"></a>[Enter]</h1>
<h1><a id="_What_is_your_dapp_master_password_557"></a>? What is your dapp master password</h1>
<h1><a id="_558"></a></h1>
<p>The dapp masterpassword is located in <code>bel/config.json</code>.<br>
“dapp”: {<br>
“masterpassword”: “ytfACAMegjrK”,<br>
“params”: {<br>
“”: [<br>
]<br>
}<br>
Then write the passwords of the 5 delegates into the dapp configuration file <code>bel/dapps/ /config.json</code>.</p>
<h1><a id="configjson_567"></a>config.json</h1>
<p>{<br>
“secrets”: [<br>
“flame bottom dragon rely endorse garage supply urge turtle team demand put”,<br>
“thrive veteran child enforce puzzle buzz valley crew genuine basket start top”,<br>
“black tool gift useless bring nothing huge vendor asset mix chimney weird”,<br>
“ribbon crumble loud chief turn maid neglect move day churn share fabric”,<br>
“scan prevent agent close human pair aerobic sad forest wave toe dust”<br>
]<br>
}<br>
<strong>After the installation restart the node</strong></p>
<h1><a id="stop_the_localnet_with_Ctrl__C_579"></a>stop the localnet with Ctrl + C</h1>
<h1><a id="restart_the_localnet_580"></a>restart the localnet</h1>
<blockquote>
<p>node app.js</p>
</blockquote>
<h2><a id="8_Access_The_Dapp_In_Your_Browser_582"></a>8 Access The Dapp In Your Browser</h2>
<p>Now you can access the dapp like a website <code>localhost:4096/dapps/ /</code> in your browser.</p>
<h2><a id="9_Set_Dapp_Genesis_Password_584"></a>9 Set Dapp Genesis Password</h2>
<p>Under <code>bel/config.json</code> set the genesis password for your dapp. Input your <code></code> and the secret of your<br>
<strong>before</strong></p>
<p>“dapp”: {<br>
“masterpassword”: “ytfACAMegjrK”,<br>
“params”: {}<br>
}<br>
<strong>after</strong></p>
<p>“dapp”: {<br>
“masterpassword”: “ytfACAMegjrK”,<br>
“params”: {<br>
&quot; &quot;: [<br>
“sentence weasel match weather apple onion release keen lens deal fruit matrix”<br>
]<br>
}<br>
}<br>
In the future when the DApp is published in testnet or mainnet, it still needs a machine that configures the primary password. NOTE: Only one machine is required.</p>
<h2><a id="10_The_folder_structure_604"></a>10 The folder structure</h2>
<p>Now we can see that there is a new folder added under <code>bel/dapps</code>, named as the DApp ID just created.</p>
<blockquote>
<p>ls -la dapps/<br>
dapps</p>
</blockquote>
<p>└─── dapp id</p>
<p>blockchain.json # the database description of DApp<br>
config.json # the configuration file of DApp, which mainly contains the list of seed nodes. Developers can also add other configurations in it.<br>
dapp.json # the meta information of DApp, including name, description, source code package, and etc. This file can also be used when registering the app to other networks.<br>
genesis.json # indicate the genesis blcok. This file is generated by CLI automatically, but also can be written by yourself, by which the assets of genesis account can be distributed with more flexibility.<br>
index.js # this file contains the entry of DApp<br>
init.js # this file contains the initial code of each module.<br>
LICENSE # this file describes the permit license of source code.<br>
modules # main code<br>
modules.full.json # this file indicates all the modules need to be loaded. You can add other necessary modules here.<br>
modules.genesis.json # (the simplified version of modules.full.json, currently not need)<br>
node_modules #<br>
public # this folders contains all front-end files<br>
routes.json # this file contains the configuration of http route. If you want to add new interface, you need to revise this file.<br>
Don’t worry about the complexity of the file structure. For now a first look is enough.</p>
<p>All the essential files for developers can be found in <code>modules/contracts/</code><br>
There are 4 build-in contract types in this folder:</p>
<blockquote>
<p>ls -1 dapps/ /modules/contracts/<br>
dapps</p>
</blockquote>
<p>└─── dapp id</p>
<p>└───modules</p>
<p>└───contracts</p>
<p>delegates.js # registering delegate contract<br>
insidetransfer.js # in-chain transfer contract<br>
outsidetransfer.js # BEL deposit contract<br>
withdrawaltransfer.js # BEL withdraw contract<br>
Developers need to create a new contact to run business logic. That’s all.</p>
<h2><a id="11_Dapp_Deposit_645"></a>11 Dapp Deposit</h2>
<p>In this project, we are able to conduct multiple tasks such as deposit, in-chain transfer, and withdraw. Currently deposit can only be executed via command line (this feature will be built into the main wallet in the future).</p>
<blockquote>
<p>bel-cli dapps --deposit<br>
? Enter secret *******************************************************************************</p>
</blockquote>
<p>? Enter amount 100</p>
<p>? DApp Id 6299140990391157236</p>
<p>? Enter secondary secret (if defined)</p>
<p>? Host and port localhost:4096</p>
<p>null { success: true, transactionId: ‘10589988261732949004’ }</p>
<p>10589988261732949004</p>
<p>In the web wallet (<code>localhost:4096</code>) we can see (after approximately 30 seconds) that the balance was updated.</p>
