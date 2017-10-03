# Canimmunize-android-automation-QA
# The Cucumber Test Stack:

![alt tag](https://github.com/loliiiiipop/setUpForAutomationTest/blob/master/autoTestProcess.png)

Some useful command :

Check the local gem: gem list --local


# Set up step for Android:

1 Download Android SDK and go to Platform-tools

2 Get the apk file and put it into the Platform-tools folder (make sure the abd and fastboot are in the folder)

3 Install RVM (Ruby Version Manager): \curl -sSL https://get.rvm.io | bash 

4 Using RVM to install Ruby \curl -sSL https://get.rvm.io | bash -s stable --ruby
  ruby --version   : check version
  which ruby : show work directory 

5 Close terminal and reopen a new one, type:source ~/.rvm/scripts/rvm
  Check rvm install successfully : type rvm | head -n 1
  Will show "rvm is a function" if rvm is running succefully
  type: rvm list known , will show all the known ruby
  
6  Type: rvm install 2.0.0 , this will install ruby 2.0.0 that is stable with calabash

7 Install cucumber: gem install cucumber

8 Install bundler: gem install 'bundler'

9 Install calabash-android :gem install calabash-android

10 Download Java Development Kit (JDK)
   which Java : show/usr/bin/java
   java -version : check java version

11 Install Ant
  download apache-ant-1.10.1-bin.tar.gz
  extracts: tar vxf apache-ant-1.10.1-bin.tar.gz
  
12 Set Environment path in .bash.profile:

export JAVA_HOME=/Library/Java/Home

export ANDROID_HOME=/Users/yourname/Library/Android/sdk

export ANT_HOME=/Users/yourname/apache-ant-1.10.1

export PATH="/Users/yourname/Library/Android/sdk/":$PATH:$ANT_HOME/bin

export PATH=$PATH:$ANDROID_HOME

export PATH=$PATH:$JAVA_HOME/bin/java

export PATH=$PATH:$ANDROID_HOME/tools

export PATH=$PATH:$ANDROID_HOME/platform-tools

 to re-scourcing .bash_profile
 
  source ~/.bash_profile
  
 13 Create a Gemfile in platform-tools folder
 
 14 bundle install
 
 15 Run: calabash-android setup 
    And answer all the questions
    
 16 Resign the app :
       calabash-android resign /Users/yourname/Library/Android/sdk/platform-tools/app-canary.apk
       
 17 Run: calabash-android run app-canary.apk
 
 

# Trouble shooting 

1 Json conflic can be solved by : delete gem/gem.lock -> budndle init->edit gem file with 

  / # Contents of Gemfile
    source "https://rubygems.org"

     gem 'calabash-android'
     gem 'cucumber'

Then do bundle install

# Some basic commend

1  calabash-android run app-canary.apk

2  calabash-android console app-canary.apk


# Tips:

1 Fail scenarios can be found at logs, calabash also will take screen shot for the fail UI and save it in your working directory
2 Different sceranios can be run with :
calabash-android run your.apk --tags @important
calabash-android run your.apk  --tags @important   

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
      export CODE_SIGN_IDENTITY="iOS Developer: YOURNAME(Ottawa Hospital Research Institute)"
      export DEVICE_ENDPOINT=http://192.168.128.00:37265
      export DEVICE_TARGET=f9f66342ad6225ef481eb3a02850a03d3a627472
      calabash-ios console device

4 Run calabash-ios run some.app


