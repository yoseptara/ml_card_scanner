# ml_ card_scanner

The ml_card_scanner plugin allows you to scan bank cards.
## Features


- Can scan expiration date, card type and card number 
- Work with horizontal and vertical cards
- Powered by Google's Machine Learning models
- Great performance and accuracy
- Fully offline scan makes it a completely secure scanner.

## Prepare

###Android

1. Add these to `android/grade.properties` file:

```
android.useAndroidX=true
android.enableJetifier=true
```

2. In `android/app/build.gradle` file:

```
android {
  compileSdkVersion 31 // Set this to at least 31
  minSdkVersion 21 // at least 21
  ...
}
```
3. Add the permission to `android/app/src/main/AndroidManifest.xml` file

```
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
  <uses-permission android:name="android.permission.CAMERA"/> 
  ...
 </manifest>
```


###iOS

Add to `ios/Runner/Info.plist` file:


```
<key>NSCameraUsageDescription</key>
<string>Your Description</string>
```


Add this lines to the top of your `Podfile`:

```
# Uncomment this line to define a global platform for your project
 platform :ios, '10.0'
```

And add the following to end of your `Podfile` file:

```
post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      ... # Here are some configurations automatically generated by flutter

      # You can enable the permissions needed here. For example to enable camera
      # permission, just remove the `#` character in front so it looks like this:
      #
      # ## dart: PermissionGroup.camera
      # 'PERMISSION_CAMERA=1'
      #
      #  Preprocessor definitions can be found in: https://github.com/Baseflow/flutter-permission-handler/blob/master/permission_handler/ios/Classes/PermissionHandlerEnums.h
      config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] ||= [
        '$(inherited)',

       
        ## dart: PermissionGroup.camera
         'PERMISSION_CAMERA=1',

        ]

    end
  end
end
```

## Usage

Just import the package and call `ml_card_scanner` an use `ScannerWidget` in your code:

```
ScannerWidget(controller: _controller)
```

Also `ScannerWidget` have another parameter you can specify:

 - `overlay` - set your overlay widget or specify null to use the default;
 - `overlayText` - set your text widget or specify null to use the default;
 - `scannerDelay` - set the scan delay or not set to use the default 400 (interval between card scannings in millisecconds);
 - `oneShotScanning` - set to `false` -  the scan will run continuously, `true` -scaninng will stop after card detected;
 - `overlayOrientation` - set the default overlay orientation, by default `portrait`;
 - `controller` - `ScannerWidgetController` widget controller to get scanned card details or error;

For `ScannerWidgetController` have functionality:

 - enable or disable scanning;
 - enable or disable camera preview;
 - set `onCardScanned` callback;
 - set `onError` callback;


Example Output :

```
Number card: 5173949390587465
Type: Master Card
Expiry: 10/24
```
 


