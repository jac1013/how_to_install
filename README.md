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
    
It should show you the version of nodejs you just installed (this install __npm__ too).
 
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


<a name="MongoDB"/>
## MongoDB

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

<a name="PostgreSQL"/>
## PostgreSQL

To download the latest postgresql version you will have to update your __PPA__ before from the CLI:

    $ wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | \
    sudo apt-key add -
    $ sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ precise-pgdg main" >> /etc/apt/sources.list.d/postgresql.list'
    $ sudo apt-get update
    $ sudo apt-get postgresql-9.3

The information of the PPA it's from [here](http://www.ubuntuupdates.org/ppa/postgresql)

After this you won't be able to do anything because only _postgres_ user can, but it has no password :D, let's fix this:

    $ sudo -u postgres createuser -s $USER

This will create your unix user as a role in template1 database but you won't be able to psql yet, you have to create a database with your username like this:

    $ createdb $USER

After this you will be able to do ```$ psql``` with your unix user.

To allow postgresql to receive remote connections you will have to go to:

```/etc/postgresql/9.3/main``` __this location may vary__ and modify 2 files

###postgresql.conf:

this: 
```#listen_addresses = 'localhost'```

for this:
```#listen_addresses = '*'```

###pg_hba:

this:
```host    all             all             127.0.0.1/32          md5```

for this:
```host    all             all             0.0.0.0/32            md5```

```0.0.0.0``` means any IP direction can login, you will probably use a range here depending on your needs. 

---------------------------------------------------------------------------------

<a name="PGAdmin3"/>
## PGAdmin3

    $ sudo apt-get install pgadmin3

---------------------------------------------------------------------------------

<a name="MySQL"/>
## MySQL

    $ sudo apt-get install mysql-client
    $ sudo apt-get install mysql-server

Then we will log in as root:

    $ mysql -u root -p

After this we will add our unix user to mysql roles:

    $ mysql> CREATE USER 'your_user'@'localhost' IDENTIFIED BY 'some_pass';
    $ mysql> GRANT ALL PRIVILEGES ON *.* TO 'monty'@'localhost' WITH GRANT OPTION;

We have to restart the server to see the changes:

    $  sudo /etc/init.d/mysql restart

Finally you will be able to:

    $ mysql -p
    $ Enter password:
    $ mysql>

Concerning to this issue [error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'](http://stackoverflow.com/questions/11990708/error-cant-connect-to-local-mysql-server-through-socket-var-run-mysqld-mysq)
When I miself encounter this I did ``` $ sudo find / -type sd``` and didn't found a socket for mysql, I solve this restarting
the system and then the socket was there, after that I just modify the ```/etc/mysql/my.cnf``` file to match the socket I found
in ``` $ sudo find / -type sd``` and the issue was solved.

---------------------------------------------------------------------------------

<a name="PHPMyAdmin"/>
## PHPMyAdmin

    $ sudo apt-get install phpmyadmin

Note: if you are a begginer let phpmyadmin configure the database it will use itself.

If you go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) and you can't see phpmyadmin
then follow the instructions [here](http://askubuntu.com/questions/19127/how-to-access-phpmyadmin-after-installation)

---------------------------------------------------------------------------------

<a name="Android_Studio"/>
## Android Studio

Download [Android Studio](http://developer.android.com/sdk/installing/studio.html#download).

Decompress what you've downloaded like this (numbers change depending on version):

    $ tar -zxvf android-studio-bundle-133.1028713-linux.tgz
    $ sh android-studio/bin/studio.sh

If it prompt you with something related to OpenJDK then follow the steps to configure oracle's java [here](Java_1.7).

---------------------------------------------------------------------------------

<a name="IntellijIdea"/>
## IntellijIdea

Download [IntelliJIdea](http://www.jetbrains.com/idea/download/)

Decompress what you've downloaded like this (numbers change depending on version):

    $ tar -zxvf ideaIC-13.1.2.tar.gz
    $ sh ideaIC-13.1.2/bin/idea.sh

If it prompt you with something related to OpenJDK then follow the steps to configure oracle's java [here](Java_1.7).

---------------------------------------------------------------------------------

<a name="Gradle"/>
## Gradle

Download [Gradle](http://www.gradle.org/downloads)

Decompress what you've downloaded like this (number change depending on version):

    $ unzip gradle-1.12-all.zip

In case you don't have unzip do this first:

    $ sudo apt-get install unzip

Create an enviroment variable for gradle in your ```.bashrc``` or ```.zshrc``` file like this:

    ```export PATH="your_gradle_directory/bin:$PATH"

Lastly type:

    $ gradle -v
    
      ------------------------------------------------------------
      Gradle 1.12
      ------------------------------------------------------------

      Build time:   2014-04-29 09:24:31 UTC
      Build number: none
      Revision:     a831fa866d46cbee94e61a09af15f9dd95987421

      Groovy:       1.8.6
      Ant:          Apache Ant(TM) version 1.9.3 compiled on December 23 2013
      Ivy:          2.2.0
      JVM:          1.7.0_55 (Oracle Corporation 24.55-b03)
      OS:           Linux 3.11.0-12-generic amd64


It should show the output above, for more information go to gradle's [documantion](http://www.gradle.org/docs/current/userguide/userguide_single.html).

---------------------------------------------------------------------------------

<a name="Maven"/>
## Maven

---------------------------------------------------------------------------------

<a name="Netbeans"/>
## Netbeans

Download [Netbeans](https://netbeans.org/downloads/)

    $ sh netbeans-8.0-linux.sh
    $ ~/netbeans-8.0/bin/netbeans

If it prompt you with something related to OpenJDK then follow the steps to configure oracle's java [here](Java_1.7).

---------------------------------------------------------------------------------   

<a name="Glassfish"/>
## Glassfish

---------------------------------------------------------------------------------

<a name="Tomcat"/>
## Tomcat

---------------------------------------------------------------------------------

<a name="Eclipse"/>
## Eclipse

Download [Eclipse](https://www.eclipse.org/downloads/)

Decompress what you've downloaded like this (numbers change depending on version):

    $ tar -zxvf eclipse-standard-kepler-SR2-linux-gtk-x86_64.tar.gz 
    $ eclipse/eclipse

---------------------------------------------------------------------------------

<a name="SublimeText2"/>
## SublimeText2

Download [SublimeText2](http://www.sublimetext.com/2) 

Decompress what you've downloaded like this (numbers change depending on version):

    $ tar -jxvf ../Sublime\ Text\ 2.0.2\ x64.tar.bz2


---------------------------------------------------------------------------------





    





    

