# amazon_dash_button
[Node-dash-button](https://www.npmjs.com/package/node-dash-button) based IoT button example for remote script execution.

## Find Your Dash Buttons
In order to find your Dash Button's MAC address you will have to execute the following command:

```
sudo npm run busca
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
