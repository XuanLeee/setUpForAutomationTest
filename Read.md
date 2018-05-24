# Canimmunize-IOS-automation-QA

# Set up steps for IOS:
1 Install ruby and calabash-cucumber in the root folder of project

    gem install calabash-cucumber
    
2 Using calabash-ios command to download the latest version of calabash.framework

    calabash-ios download
    
3 Linke the app with calabash.framework:

    (1) git clone target-repo
    (2) cd repo and do pod install ( need cocoapad install first)
    (3) if there is swift socket-io issues, change the socket-io version to "11.1.3"
    (4) run pod update
    (5) open with xcode and go to target, link the calabash in debug config  
        trouble shooting: In other linker flags, don`t change the origin framework, just add this command at the end
        
            -ObjC -force_load "$(SOURCE_ROOT)/calabash.framework/calabash" -framework CFNetwork
4 Setup test: run calabash-ios gen  to see if there is dir called features created, run test with cucumber

5 Now you can start app with simulator in calabash console by : calabash-ios console run

# Set up steps for physical target device:

1 Find if device has enable for development: xcrun instruments -s devices, also enable Developer->UI Automation in setting

2 Run on Xcode and get app on the phone

3 Start with target device
     Create a .sh file:
   
       #!/bin/sh

      export BUNDLE_ID=ca.ohri.immunizenu
      export CODE_SIGN_IDENTITY="iOS Developer:"
      export DEVICE_ENDPOINT=http://192.168.128.119:37265
      export DEVICE_TARGET=f9f66342ad6225ef481eb3a02850a03d3a62747
      calabash-ios console device


4 Run calabash-ios run CANImmunize.app
