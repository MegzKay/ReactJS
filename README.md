## Installation instructions for ReactJS
These are installation instructions on how to setup ReactJS for a test setup. Majority of the instructions come from tutorialspoint. 
Other instructions came from me searching through Github and Stack Overflow

### Install Atom
sudo add-apt-repository ppa:webupd8team/atom
sudo apt-get update
sudo apt-get install atom
apm install language-babel

### Install NodeJS and NPM
Go to tutorialspoint and follow their instructions:  
https://www.tutorialspoint.com/nodejs/nodejs_environment_setup.htm  
And then use:  
 * sudo apt-install npm  
### Install Babel, Webpack and ReactJS  
Go to tutorialspoint link below and follow the instructions but you need to make a few tweaks for it to work properly. 
https://www.tutorialspoint.com/reactjs/reactjs_environment_setup.htm  
NOTE make the following changes
 * If using Ubuntu 16.04, installing the packages above will cause an error because the packages include fsevents which is for MACs only. These are optional files so to not include them, use the --no-optional parameter like so: npm install --no-optional PACKAGE  
 * When you get to Step 5 (Set Compiler, Server and Loaders), you need to set an absolute entry and output path. 
   * Entry would be:  __dirname + '/main.js'
   * Output would be: __dirname
 * Also on step 5 look for loader:'babel' and replace with loader:'babel-loader'.

If this is still not working try:
 * You may be using port 8080 for something else. Check using sudo lsof -i :8080 | grep LISTEN. If so change to another port  
 * You may need to install legacy nodejs, if so use command sudo apt-get install nodejs-legacy  
### Install ReactRouter and ReactRouterDom
npm install --no-optional react-router
npm install --no-optional react-router-dom
 * NOTE: With V4 you need to install react router dom  
 
### Bootstrap and jQuery
npm install --no-optional jquery
npm install --no-optional bootstrap@3
 * Both will be located in node_modules/jquery and node_modules/bootstrap respectively 
