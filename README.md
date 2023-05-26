# BeatInfoKits for Android 
[BeatInfoKits Reference for Android](https://docs.google.com/document/d/1vwwf_BozLqUMlHiJKB1dM_wFujWCokbj3tPj9Ibzfnc/edit#heading=h.k3zai6kg2wsb)
## Requirements
- Java or Koltin
- Android 8.0+
- Bluetooth
- Network
## How to Start
1. Install `BeatInfoKits.aar` (in app/libs)  
  a. Copy `BeatInfoKits.aar` to the folder of app/libs in your project.  
  b. App implementation files in the dependencies section of `build.gradle`, example:
    ```Java
      implementation files('libs/BeatInfoKits.aar')
    ```
    c. Implementation the required libraries, example:  
    ```Java
      implementation 'com.squareup.retrofit2:retrofit:version'  
      implementation 'com.squareup.retrofit2:converter-gson:version'  
      implementation 'com.squareup.okhttp3:okhttp:version'  
      implementation 'androidx.security:security-crypto:version'  
    ```

2. Use the BeatInfoKits, please refer the `MainActivity.java`  
  - Init beatInfoSDKManager:   
    - create a beatInfoSDKManager instance, example:  
    ```Java
      beatInfoSDKManager = new BeatInfoSDKManager(context, token, new BeatInfoSDKManagerCallback() {
          @Override
          public void onMessage(String message) {
          }
      });
    ```
  - Get scan device list, example:
    ```Java
      list = beatInfoSDKManager.getScanDeviceList();
    ```

  - Connect device  
    - create a device data found callback(`BeatInfoDeviceCallback`), please refer the `DeviceDataProcess.java`
    - connect device, example:
    ```Java
      beatInfoSDKManager.connect(mac ,type , deviceDataCallback);
    ```
  - Disconnect device, example:  
    ```Java
      beatInfoSDKManager.disconnect(mac);
    ```


3. Use this SDK, detail please refer `DeviceDataProcess.java`
   once connected to a device, will start receiving device data, and use the BeatInfoDeviceCallback to get value, example:
  ```Java
    @Override
    public void onECG(String deviceMac, int[] oriECGValues, int[] ecgValues, int[] hrs, int[] irrFlags, int[] ecgQualityFlags, int[] rris,
                        int oriRespValue, int breathRate, int breathQualityFlag, boolean isLeadOff) {

    } 
  ```

4. Run this demo app  
  - Compile and run this demo app.  
  - Click the play button to show the scan device list dialog.  
  - Click the scan device list item to connect device, and will show HEART RATE, BREATH RATE and TEMPERATURE on screen.  
  - Click the red cross button or long press device button to disconnect device.