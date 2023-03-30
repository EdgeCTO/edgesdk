# Edgesdk
### Description
edgesdk is a complete suite that provides developers with all the features they need to enable mobile, TV, and tablet apps with the watch2earn service provided by EdgeVideo.com. This SDK includes all the necessary components to easily integrate watch2earn into your app.

### Installation
Instructions for how to setup the sdk in you project
#### Step 1 
Add it in your root build.gradle at the end of repositories:
```groovy
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
``` 

#### Step 2
Add the dependency
```groovy
dependencies {
    implementation 'com.github.EdgeCTO:edgesdk:Tag'
}
```
<button class="btn" data-clipboard-text="dependencies {
    implementation 'com.github.EdgeCTO:edgesdk:Tag'
}">Copy</button>

### Usage
#### Step 1 [Initilize the sdk]
Initialize the sdk
```groovy
EdgeSdk edgeSdk = new EdgeSdk(this);
```
<button class="btn" data-clipboard-text="dependencies {
    EdgeSdk edgeSdk = new EdgeSdk(this);
}">Copy</button>

#### Step 2 [set default values]
In this step you may need to place following snippets on onCreate() method .. or where the begining of app is pointed.
```groovy
edgeSdk.getLocalStorageManager().storeBooleanValue(true, com.edgesdk.Utils.Constants.IS_TICKER_ALLOWED_TO_HIDE);
edgeSdk.getLocalStorageManager().storeBooleanValue(false,com.edgesdk.Utils.Constants.IS_OPT_OUT_W2E_ENABLED);
edgeSdk.getLocalStorageManager().storeBooleanValue(true,com.edgesdk.Utils.Constants.IS_VIEWER_WALLET_ADDRESS_FORWARDED);
edgeSdk.getLocalStorageManager().storeStringValue("WALLET_ADDRESS",com.edgesdk.Utils.Constants.WALLET_ADDRESS);
```


#### Step 3 [start sdk]
The you need to call start() method of sdk : `edgeSdk.start();` this will causing multiple operations started on backend
```groovy
edgeSdk.start();
```

#### Step 4 [start staking]
For starting staking you need to call startStaking() of sdk : `edgeSdk.startStaking();`
```groovy
edgeSdk.startStaking();
```

#### Step 5 [importing and initizlizing sdk ticker]
For this firstly you need to create a ticker vairbale and initialize it : 

```groovy
Ticker ticker =  ticker = new Ticker(this,edgeSdk);
ticker.setBackpressed(false);
ticker.setPlaying(true);
```

#### Step 6 [setting up sdk ticker on a view]
To setup ticker over any video you need to first a empty lineat layout and use that to set up sdk ticker over that

```groovy
LinearLayout layout = findViewById(R.id.main_layout);
layout.addView(ticker);
```

#### Step 7 [calling activity cyvle methods]
you need to put following method in overiden method of activity in which you are calling them. For example to start things you need to call following method in onResume method of your activity

```groovy
ticker.onResume();
```


#### Step 8 [updating base rate to strart earning EAT]

 ```groovy
edgeSdk.getW2EarnManager().updateBaseRateOnServer(600)
```
### Features [Key features]
1. The EdgeSdk provides socket connection methods for efficient communication.
2. Thread controlling methods such as start(), close(), startStaking(), stopStaking(), and pauseW2E() allow for effective management of processes.
3. The SDK offers various result-fetching methods, including getStakingValueFetchingManager() to retrieve staking values and getW2EarnManager() for earning statistics. Additionally, the SDK includes getMarketPriceManager() to fetch current market prices.
4. The GamifiedTvSocketManager provides access to features such as getIS_BOOST_ENABLED() and getCURRENT_PRESSED_REMOTE_BUTTON() for enhancing the user experience.
### API Documentation
Documentation for the API of sdk.
# EdgeSdk API Documentation

## Initialization

### Java

```java
EdgeSdk edgeSdk = new EdgeSdk(this);
```

### Kotlin

Define a variable in the companion object:
```kotlin
companion object {
    lateinit var edgeSdk: EdgeSdk
}
```

Initialize it in the `onCreate()` method of your main activity (e.g., `HomeActivity`):
```kotlin
HomeActivity.edgeSdk = EdgeSdk(this)
```

## Socket connection and threads controlling methods

### Start the SDK
```kotlin
HomeActivity.edgeSdk.start()
```

### Close the SDK
```kotlin
HomeActivity.edgeSdk.close()
```

### Start staking
```kotlin
HomeActivity.edgeSdk.startStaking()
```

### Stop staking
```kotlin
HomeActivity.edgeSdk.stopStaking()
```

### Pause watch2earn
```kotlin
HomeActivity.edgeSdk.pauseW2E()
```

## Result fetching methods

### Staking value fetching methods
```kotlin
HomeActivity.edgeSdk.getStakingValueFetchingManager().getStkResults().[METHOD]
    getResumingStakingIn()
    getStakingPercentage()
    getEstimatedApyPercentage()
```

### Watch2earn result fetching methods
```kotlin
HomeActivity.edgeSdk.getW2EarnManager().getResults().[METHOD]
    getEstimateEatsPerHour()
    getBalance()
    getEstimatedEarnedEatsInUSD()
    getEstimateEatsPerHour()
```

### Market price fetching methods
```kotlin
HomeActivity.edgeSdk.getMarketPriceManager().[METHOD]
    getChange()
    getPrice()
```

### Gamified TV socket fetching methods
```kotlin
HomeActivity.edgeSdk.getGamifiedTvSocketManager().[METHOD]
    getIS_BOOST_ENABLED()
    getCURRENT_PRESSED_REMOTE_BUTTON()
```


### Further Information
for futher information visit : http://edgevideo.com/ 
