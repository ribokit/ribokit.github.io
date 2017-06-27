---
permalink: /Biers/dependency/
level: 2
prev: ../install/
---

# Biers Dependency

**This guide has been tested for _Mac OS X_ systems only.**{: style="color:#ff5c2b;"} We have not used _Windows_ machines for **Biers** before.

<hr/>

## RNAstructure

We are using the **Command Line** (Text Interface) of RNAstructure. Based on our experience, we provide instructuions that is based on and in addtion to RNAstructure's [help page](http://rna.urmc.rochester.edu/Text/index.html).

> **In mid 2017, RNAstructure `6.0` will be released and  `Biers` will be compatible with it.** In the meanwhile, we have only tested RNAstructure versions `5.6` and `5.7`. Other versions may utilize backward-incompatible formats that produce traceback errors at runtime. You can download our working version (`5.6`) from [here](https://rmdb.stanford.edu/site_data/RNAstructure.zip). You may need to re-compile via `make clean; make Fold ShapeKnots`; make sure to update `compiler.h` to point to `CXX=g++`; and you may need to also remove `-fsched-spec-load` from `CXXFLAGS`.

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

Double-click on `VARNA.jar` – it may ask you to install Java runtime – just follow the instructions. 

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

<hr/>





