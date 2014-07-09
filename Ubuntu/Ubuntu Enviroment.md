# Setup Enviroment for Building Android Open Source

---
## Contains
> * Install JDK 
> * Install Required Packages
> * Install Git
> * Install Python
> * Install GNU Make

---
##Install JDK

**Check to see if your Ubuntu Linux operating system architecture is 32-bit or 64-bit**
> `file /sbin/init`
    
    Note the bit version of your Ubuntu Linux operating system architecture it will display whether it is 32-bit or 64-bit.

**Check if you have Java installed on your system. To do this, you will have to run the Java version command from terminal.**
> `java -version`

*If you have OpenJDK installed on your system it may look like this:*
    
> java version "1.7.0_15"
>OpenJDK Runtime Environment (IcedTea6 1.10pre) (7b15~pre1-0lucid1)
>OpenJDK 64-Bit Server VM (build 19.0-b09, mixed mode)

*If you have OpenJDK installed on your system, you have the wrong vendor version of Java installed for this exercise.*

**Completely remove the OpenJDK/JRE from your system and create a directory to hold your Oracle Java JDK/JRE binaries.**
> `sudo apt-get purge openjdk-\*`

    This command will completely remove OpenJDK/JRE from your system
> `sudo mkdir -p /usr/local/java`

    This command will create a directory to hold your Oracle Java JDK and JRE binaries.

**Download the Oracle Java JDK for Linux. Make sure you select the correct compressed binaries for your system architecture 32-bit or 64-bit (which end in tar.gz).**

> Open This page and download the right file.[Orcal JDK Download](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

**Copy the Oracle Java binaries into the /usr/local/java directory.**

> `cd /home/"houny"/Downloads`
> `sudo cp -r jdk-8u5-linux-x64.tar.gz /usr/local/java`
> `cd /usr/local/java`

**Unpack the compressed Java binaries, in the directory /usr/local/java**
> `sudo tar xvzf jdk-8u5-linux-x64.tar.gz`

    At this point, you should have two uncompressed binary directories in /usr/local/java for the Java JDK/JRE listed as:
    jdk1.7.0_60
    jre1.7.0_60
**Edit the system PATH file /etc/profile and add the following system variables to your system path. Use nano, gedit or any other text editor, as root, open up /etc/profile**
> `sudo gedit /etc/profile`
>or
> `sudo nano /etc/profile`

**Scroll down to the end of the file using your arrow keys and add the following lines below to the end of your /etc/profile file:**
> `JAVA_HOME=/usr/local/java/jdk1.7.0_60`
> `PATH=$PATH:$HOME/bin:$JAVA_HOME/bin`
> `export JAVA_HOME`
> `export PATH`

    Save the /etc/profile file and exit.

**Inform your Ubuntu Linux system where your Oracle Java JDK/JRE is located. This will tell the system that the new Oracle Java version is available for use.**
> `sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/java/jdk1.7.0_60/bin/java" 1`
    
    this command notifies the system that Oracle Java JRE is available for use
> `sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/local/java/jdk1.7.0_60/bin/javac" 1`

    this command notifies the system that Oracle Java JDK is available for use
> `sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/local/java/jdk1.7.0_60/bin/javaws" 1`

    this command notifies the system that Oracle Java Web start is available for use
    
**Inform your Ubuntu Linux system that Oracle Java JDK/JRE must be the default Java.**
> `sudo update-alternatives --set java /usr/local/java/jdk1.7.0_60/bin/java`

    this command will set the java runtime environment for the system
> `sudo update-alternatives --set javac /usr/local/java/jdk1.7.0_60/bin/javac`

    this command will set the javac compiler for the system
> `sudo update-alternatives --set javaws /usr/local/java/jdk1.7.0_60/bin/javaws`

    this command will set Java Web start for the system

**Reload your system wide PATH /etc/profile by typing the following command:**
> `source /etc/profile`

**Reboot your Device**

----

##Install Required Packages
> `sudo apt-get install git gnupg flex bison gperf build-essential \ zip curl libc6-dev libncurses5-dev:i386 x11proto-core-dev \ libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 \ libgl1-mesa-dev g++-multilib mingw32 tofrodos \ python-markdown libxml2-utils xsltproc zlib1g-dev:i386`

> `sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/i386-linux-gnu/libGL.so`

*Author [@Houny Chang]*  
*2014 07 09*
