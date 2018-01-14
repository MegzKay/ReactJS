# Installation instructions for ReactJS on Ubuntu
These are installation instructions on how to setup ReactJS for a test setup on Ubuntu. 

## Update Linux before installing anything
Get updates into repository: sudo apt-get update
Get upgrades from repository: sudo apt-get upgrade

## Install Atom
sudo add-apt-repository ppa:webupd8team/atom
sudo apt-get update
sudo apt-get install atom
apm install language-babel

## Install NodeJS and NPM
sudo apt-get install nodejs
sudo apt-get install npm

## Create ReactJS Project
mkdir FOLDER_NAME
cd FOLDER_NAME

npm init 
npm install --save react react-dom 
npm install --save-dev babel-core babel-loader babel-preset-env babel-preset-react css-loader style-loader html-webpack-plugin webpack webpack-dev-server 


### Set up Folders
mkdir FOLDER_NAME/App 
touch FOLDER_NAME/App/{index.html,main.css,index.js} 
mkdir FOLDER_NAME/App/Components 



### Edit Package.json
To package.json add add: 
"babel": { 
	"presets": ["env", "react"] 
}, 
And change scripts to: 
"scripts": { 
    "create": "webpack" 
  }, 

### Create webpack.config.js 
touch FOLDER_NAME/webpack.config.js 
var path = require('path'); 
var HtmlWebpackPlugin = require('html-webpack-plugin');  

module.exports = { 
   entry: './app/index.js', 
   output: { 
     path: path.resolve(__dirname, 'dist'), 
     filename: 'index_bundle.js' 
   }, 
   module: { 
     rules: [ 
       { test: /\.(js)$/, use: 'babel-loader' }, 
       { test: /\.css$/, use: [ 'style-loader', 'css-loader' ]} 
     ] 
   }, 
   plugins: [
     new HtmlWebpackPlugin({
       template: 'app/index.html'
     })
   ]
 }; 
 
 
### Create .gitignore
touch FOLDER_Name/.gitignore
Include dist and node_modules as these two larger folders do not need to be uploaded to github 


### Final setup steps
npm run create 

Go back into package.json and change scripts to: 

"scripts": {
	"start": "webpack-dev-server --open"
}, 

### And now to begin
This will start running the server. Also because web added the above script, whenever you save a file, it will automatically refresh the webpage

npm run start 

 * NOTE: With V4 you need to install react router dom   
 
### Bootstrap and jQuery
npm install --no-optional jquery
npm install --no-optional bootstrap@3
 * Both will be located in node_modules/jquery and node_modules/bootstrap respectively 
 
* If you get an error regarding fsevents, that is because these files are for MACs only. These are optional files so to not include them, use the --no-optional parameter like so: npm install --no-optional PACKAGE. I found after I did an update, I no longer had to do this  
