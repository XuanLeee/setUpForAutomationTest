# The Cucumber Test Stack:

![alt tag](https://github.com/loliiiiipop/setUpForAutomationTest/blob/master/autoTestProcess.png)

Some useful command :
Check the local gem: gem list --local


Set up step:
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

   export JAVA_HOME=$(/usr/libexec/java_home)
   export ANT_HOME=/Users/yourname/apache-ant-1.10.1
   export PATH="/Users/yourname/Library/Android/sdk/platform-tools/":$PATH:$ANT_HOME/bin

 
