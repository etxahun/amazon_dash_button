# amazon_dash_button
[Node-dash-button](https://www.npmjs.com/package/node-dash-button) module based IoT button example for scripts execution.

## Installation Instructions
The following commands installs [libcap](http://www.tcpdump.org/) and [Node-dash-button](https://www.npmjs.com/package/node-dash-button) module:
```
# dependancy on libpcap for reading packets 
$ sudo apt-get install libpcap-dev
$ npm install node-dash-button
```

## Find Your Dash Buttons
[Node-dash-button](https://www.npmjs.com/package/node-dash-button) includes a "findbutton" function for Dash-Buttons discovery.

```
  >cd node_modules/node-dash-button
  >node bin/findbutton
```
Other option is to include the following line in "package.json":

```json
    {
      "scripts": {
         "searchbutton": "node node_modules/node-dash-button/bin/findbutton"
      }
    }
```

And execute the following command:

```
sudo npm run searchbutton
```

## Dash Button triggered script execution
The following code shows the way that a remote script can be executed once a specific Amazon Dash Button (based on its MAC address) is pressed:

```javascript
var dash_button = require('node-dash-button'),
    dash = dash_button('xx:xx:xx:xx:xx:xx'), // replace xx:xx:xx:xx:xx:xx with your Dash Button's one
    exec = require('child_process').exec;

dash.on('detected', function() {
    exec('sh <ruta_script_sh>', function(error, stdout, stderr) {
        console.log('stdout: ' + stdout);
        console.log('stderr: ' + stderr);
        if (error !== null) {
            console.log('exec error: ' + error);
        }
    });
});ng 
```

Once the corresponding Dash Button's MAC address and the path of the script are configured, the following command is used to star it up:

```
sudo node index.js
```
