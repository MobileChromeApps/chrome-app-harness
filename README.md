cordova-app-harness
===================

An App harness for Cordova that can download and run Cordova apps as well as Chrome packaged apps. This enables an edit &amp; refresh workflow. Also enables local development of apps without needing the Android / iOS SDK.

##Setting up environment

*   Clone the the cordova-app-harness, cordova-android, cordova-ios, cordova-js, plugman, cordova-cli, zip(https://github.com/MobileChromeApps/zip) and AppBundle(https://github.com/MobileChromeApps/AppBundle) repos into folders of the same name in a common directory - eg 'Repo'.
*   Use the future branch of plugman and cordova-cli
*   Link these plugman and cordova-cli of this branch as the globally symlinked plugman and cordova-cli commands. (You may want to see 'npm link')
*   Build the cordova-js repo and grab the cordova.android.js and cordova.ios.js
*   Note this project uses a slightly modified version of cordova.android.js and cordova.ios.js
*   Replace the cordova-cli/lib/cordova-android/framework/assets/js/cordova.android.js and the cordova-cli/lib/cordova-ios/CordovaLib/cordova.ios.js files with the ones above
*   Build the cordova-android repository and generate new cordova.jar
*   Run the following commands

        cordova create CordovaAppHarness
        cd CordovaAppHarness
        cordova platform add android
        cordova platform add ios
        cordova plugin add ../Repo/AppBundle
        cordova plugin add ../Repo/zip/
        cp -rf ../Repo/cordova-app-harness/www app/www
        cordova prepare

*   Put the cordova.jar in the CordovaAppHarness/platforms/android/libs folder. (Note you may want to link the cordova-android project directly instead of adding a built jar so you can easily make changes to cordova-android and test the app harness)
*   Replace the contents of CordovaAppHarness/platforms/ios/CordovaLib with /Repo/cordova-ios/CordovaLib
*   Go to eclipse and got to new, other, android, android project from existing code. Navigate to CordovaAppHarness/platforms/android and then add the project
*   Double click the  .xcodeproj file in CordovaAppHarnessNew/platforms/ios/
*   You can now build the app harness from the ides or with cordova compile

##Using the app

*   Run the packapp script and point it to a cordova project. This will package the app into a cdvh file. (Note: it is expected that you add all relevant platforms. For example, if you want to test on the iphone, you need to have added the ios platform to the project)
        Repo/cordova-app-harness/packapp -p ./TestApp TestApp.cdvh
*   Upload the the cdvh onto any hosting site.
*   Run the app harness
*   Click add new app
*   Give a name and the url to the zip.
*   Go back to the main screen after you see the prompt "successfully installed"
*   Click launch on the newly installed app
*   See if the app looks as expected
*   Use the 3 finger tap to access the app menu while testing your app
*   Press Back to Main Menu to return to the main screen
