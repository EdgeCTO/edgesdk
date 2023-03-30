# Edgesdk
### Description
edgesdk is a complete suite that provides developers with all the features they need to enable mobile, TV, and tablet apps with the watch2earn service provided by EdgeVideo.com. This SDK includes all the necessary components to easily integrate watch2earn into your app.

### Installation
Instructions for how to setup the sdk in you project
#### Step 1 
Add it in your root build.gradle at the end of repositories:
`
	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
`
#### Step 2
Add the dependency
`
	dependencies {
	        implementation 'com.github.EdgeCTO:edgesdk:Tag'
	}
`  
### Usage
#### Step 1 [Initilize the sdk]
Initialize the sdk : `EdgeSdk edgeSdk = new EdgeSdk(this);`
#### Step 2 [set default values]
In this step you may need to place following snippets on onCreate() method .. or where the begining of app is pointed.
 `edgeSdk.getLocalStorageManager().storeBooleanValue(true, com.edgesdk.Utils.Constants.IS_TICKER_ALLOWED_TO_HIDE);`
 `edgeSdk.getLocalStorageManager().storeBooleanValue(false,com.edgesdk.Utils.Constants.IS_OPT_OUT_W2E_ENABLED);`
 `edgeSdk.getLocalStorageManager().storeBooleanValue(true,com.edgesdk.Utils.Constants.IS_VIEWER_WALLET_ADDRESS_FORWARDED);`
 `edgeSdk.getLocalStorageManager().storeStringValue("0x1CE5db82533E4Fec3e1D983D89070F8185fC163F",com.edgesdk.Utils.Constants.WALLET_ADDRESS);`

#### Step 3 [start sdk]
The you need to call start() method of sdk : `edgeSdk.start();` this will causing multiple operations started on backend
#### Step 4 [start staking]
For starting staking you need to call startStaking() of sdk : `edgeSdk.startStaking();`
#### Step 5 [importing and initizlizing sdk ticker]
For this firstly you need to create a ticker vairbale and initialize it : 
`Ticker ticker =  ticker = new Ticker(this,edgeSdk);`
and also following methods
`ticker.setBackpressed(false);`
`ticker.setPlaying(true);`
#### Step 6 [setting up sdk ticker on a view]
To setup ticker over any video you need to first a empty lineat layout and use that to set up sdk ticker over that
`LinearLayout layout = findViewById(R.id.main_layout);`
`layout.addView(ticker);`

#### Step 7 [calling activity cyvle methods]
you need to put following method in overiden method of activity in which you are calling them. For example to start things you need to call following method in onResume method of your activity
`ticker.onResume();`
#### Step 8 [updating base rate to strart earning EAT]
 `edgeSdk.getW2EarnManager().updateBaseRateOnServer(600)`
### Features
A list of key features of this project.

### API Documentation
Documentation for the API of this project.

### Troubleshooting
Common errors or issues that users might encounter and how to solve them.

### License
The license under which this project is released.

### Contact Information
How to contact the developers of this project.
