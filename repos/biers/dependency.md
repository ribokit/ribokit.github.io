---
permalink: /Biers/dependency/
level: 2
prev: ../install/
---

# Biers Dependency

**This guide has been tested for _Mac OS X_ systems only.**{: style="color:#ff5c2b;"} We have not used _Windows_ machines for **Biers** before.

<hr/>

## Setting up MATLAB

You may need to launch MATLAB from command-line to make sure it finds all the paths for RNAstructure and VARNA, as outlined below. 

>Simply double-clicking on the MATLAB icon may not work!

Go into the `.bash_profile` in your home directory, and include a line like:

```
alias matlab=/Applications/MATLAB_R20XXa.app/bin/matlab
```


> Use any text editor you prefer, e.g. `vim`, `nano` (easiest), `emacs`.

> Make sure you replace the version number (20xxa) with your 'real' version number!

## RNAstructure

We are using the **Command Line** (Text Interface) of RNAstructure. Following are instructions that are based on RNAstructure's [help page](http://rna.urmc.rochester.edu/Text/index.html). 

* #### Biers is compatible only with RNA structure 6.0 and later. 
RNAstructure versions earlier than 6.0 have bugs in treatment of DMS data.

* #### Install a C compiler, preferably `gcc`. 

You may already have this compiler or (on Mac OS X) the `clang` compiler which replaced it; at your terminal type:

```bash
which gcc
```

If you don't get a path, you can install `gcc`. One way to do it is through `Developer Tools`, available for free at the Apple Store.

Alternatively, you can install `gcc` via `brew`, a handy package manager for _Mac OS X_. If you don't have `brew` installed, do:

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" # may need sudo
```

Then install `gcc` with:

```bash
brew tap homebrew/versions
brew install gcc49
```

> We have only tested `gcc` version `4.x`. Newer version (e.g. `5.x`, `6.x`) may have issues with compiler flags. We have also tested `clang`, which is actually what runs instead of `gcc` on Max OS X.

Test if `gcc` is the default C compiler. You can say:

```bash
which gcc
gcc --version
```

If you're trying to avoid using `clang` (system default) and instead really want to run this `gcc`, you may need to get rid of `clang`, which occupies the namespace. To fix it, try:

```bash
brew unlink gcc49
brew link gcc49
```

> Usually, the `brew` installed `gcc` exeutables are located at a path like `/usr/local/Cellar/gcc/4.x.x/bin` (also a copy of each right at `/usr/local/bin`). Look for `gcc-4.x`, `g++-4.x`, `c++-4.x`, `cpp-4.x`.

<br/>

* #### Compile RNAstructure locally.

Check `/path/to/RNAstructure/compiler.h` to make sure `CXX=g++` or `CXX = g++-4.x`.

Now run the following command to compile the code:

```bash
cd /path/to/RNAstructure/
make clean
cd RNA_class/
make clean
cd ..
make all
make install # may need sudo make install
```

* #### Set environment variable `DATAPATH` for thermodynamic tables.

Edit file `~/.bash_profile`, add a line:

```bash
export PATH=/usr/local/bin:$PATH
export DATAPATH=/path/to/RNAstructure/data_tables/
```

> Use any text editor you prefer, e.g. `vim`, `nano` (easiest), `emacs`.

> Make sure you replace the path with your 'real' path!

Now close the terminal window and start a new one. (This allows the `~/.bash_profile` to take effect.)

<br/>

<hr/>

## VARNA

* #### Download VARNA **.jar** file and place on your desktop or wherever you keep applications.

> Any of the _types_ listed on the [download page](http://varna.lri.fr/index.php?lang=en&page=downloads&css=varna) works. The minimal _Binaries_ suffices.

Double-click on `VARNA.jar` 

> `VARNA.jar` may ask you to install Java runtime – just follow the instructions.  If you see blank data or do not see chemical mapping data, install the latest JDK: [http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

> Note: we used to recommend running VARNA through a Web browser, but we are not aware of any browsers that still allow _Java_ applications to run.


* #### Set up path to VARNA.
Edit file `~/.bash_profile`, add a line:

```bash
export VARNA=/path/to/VARNA.jar
```

> Use any text editor you prefer, e.g. `vim`, `nano` (easiest), `emacs`.

> Make sure you replace the path with your 'real' path!

Now close the terminal window and start a new one. (This allows the `~/.bash_profile` to take effect.)

<br/>


## Summary of what should be in your **.bash_profile**

After all the installation, check that your home directory's `.bash_profile` should have four lines like the following.

```
export PATH=/usr/local/bin:$PATH
export DATAPATH=/path/to/RNAstructure/data_tables/
export VARNA=/path/to/VARNA.jar
alias matlab=/Applications/MATLAB_R20XXa.app/bin/matlab
```

> Early versions of Biers recommended that these lines be placed in `.bashrc`. If you are using `.bashrc`, make sure your `.bash_profile` has a line like `source ~/.bashrc`

<hr/>

* Previous: [MATLAB installation](/Biers/install/)
* Next: [Predict secondary structure](/Biers/rnastructure/)

<hr/>




