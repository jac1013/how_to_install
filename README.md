## List of Software.

* [Git](#Git)
* [Node.js](#Node.js)
* [Redis](#Redis)
* [MongoDB](#MongoDB)
* [Java 1.7](#Java_1.7)
* [PostgreSQL](#PostgreSQL)
* [PGAdmin3](#PGAdmin3)
* [MySQL](#MySQL)
* [PHPMyAdmin](#PHPMyAdmin)
* [Android Studio](#Android_Studio)
* [IntellijIdea](#IntellijIdea)
* [Gradle](#Gradle)
* [Maven](#Maven)
* [Netbeans](#Netbeans)
* [Glassfish](#glassfish)
* [Tomcat](#Tomcat)
* [Eclipse](#Eclipse)
* [SublimeText2](#SublimeText2)
* [Shutter](#Shutter)
* [Chrome](#Chrome)
* [Terminator](#Terminator)
* [Zsh](#Zsh)
* [OhMyZsh](#OhMyZsh)
* [Gparted](#Gparted)
* [Keepassx](#Keepassx)
* [Meld](#Meld)
* [VirtualBox](#VirtualBox)
* [Emacs](#Emacs)
* [Unetbootin](#Unetbootin)
* [Furiousmount](#Furiousmount)
* [Umbrelo](#Umbrelo)
* [Sqlite](#Sqlite)
* [SqliteBrowser](#SqliteBrowser)
* [Xdotool](#Xdotool)

### Well not everything is about programming.

* [Stelarium](#Stelarium)
* [Solfege](#Solfege)
* [TeeWorlds](#TeeWorlds)
* [Wine](#Wine)
* [VLC](#VLC)
* [Cairo-dock](#Cairo-dock)
* [Transmission](#Transmission)
* [Skype](#Skype)

## How To Install.

<a name="Git"/>
## Git

```$ sudo apt-get install git```

---------------------------------------------------------------------------------

<a name="Node.js"/>
## Node.js

Download [nodejs](nodejs.org) then go to the folder where your tar.gz is and
__Replacing the X's with the version number you downloaded__ do this:

    $ tar -zxf node-v0.xx.xx.tar.gz 
    $ cd node-v0.xx.xx
    $ ./configure && make && sudo make install
    
If you have g++-4.8 this won't work read [here](http://stackoverflow.com/questions/21542983/cant-make-node-js-ubuntu-13-10).

You will have to do this first:

    $ sudo apt-get install g++-4.7
    
Then instead of ```./configure && make && sudo make install``` you will have to specify the g++ compiler like this:

    $ ./configure
    $ CXX=g++-4.7 make
    $ sudo CXX=g++-4.7 make install
    
Lastly type:

    $ node -v
    
It should show you the version of nodejs you just installed.
 
For other ways go here: [joyent_node](https://github.com/joyent/node/wiki/installation)

---------------------------------------------------------------------------------

<a name="Redis"/>
## Redis

Download [redis](redis.io) then go to the folder where your tar.gz is and __Replacing the X's with the version number you downloaded__ do :

    $ tar -zxvf redis-x.x.x.tar.gz
    $ cd redis-x.x.x
    $ make
    $ sudo make install
    
To run server:

    $redis-server
    
To test something from the CLI (_While the server is running do this in another CLI instance_):

    $ redis-cli
    $ set Hello World
    $ get Hello
    
---------------------------------------------------------------------------------

<a name="Java_1.7"/>
## Java (Same apply for other versions)

Download [Java](http://www.oracle.com/technetwork/java/javase/downloads/), we explain it here with the _tar.gz_ file:

    $ tar -zxvf jdk-7u55-linux-x64.tar.gz
    
Do this:
    
    $ java -version
    java version "1.7.0_25"
    OpenJDK Runtime Environment (IcedTea 2.3.12) (7u25-2.3.12-4ubuntu3)
    OpenJDK 64-Bit Server VM (build 23.7-b01, mixed mode)
    
Ok, but we want oracle's version not OpenJDK version so you will have to go to your bash profile or zsh profile file(_bash: ~/.bashrc, zsh: ~/.zshrc_) and after this line:

```export PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"```
   
Add this one:

```export PATH="path_to_your_java_bin_folder:$PATH"```
    
Then ```java -version``` will print this:

    $ java version "1.7.0_55"
    Java(TM) SE Runtime Environment (build 1.7.0_55-b13)
    Java HotSpot(TM) 64-Bit Server VM (build 24.55-b03, mixed mode)
    
note: _tilde_ (__~__) means __/home/your_username/__
    
---------------------------------------------------------------------------------

    


    

