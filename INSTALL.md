## Install Caspyter locally

## 1. Make sure you have the following dependencies

Install them using your package manager.
 
* libice6
* libsm6
* libxt6
* libxrender1
* libfontconfig1
* libcups2
* libxml2
* libxslt-dev
* libgtk2.0-0
* python-qt4
 
## 2. Download CASA
 
```
wget https://almascience.eso.org/arcdistribution/casa-distro/linux/release/casa-release-4.5.2-el6.tar.gz
tar zxf casa-release-4.5.2-el6.tar.gz
```

Or, symlink your downloaded casa release to this directory

```
ln -s PATH/TO/casa-release-4.5.2-el6.tar.gz .
```
 
## 3. Install patchELF

You can install it by downloading the 0.6 version from git, using Kasper's script:
 
```
sudo sh /path/to/caspyter/scripts/patchELF.sh
```

Or you can install it using your package manager


## 4. Install virtualenv

Virtual env enables you to have side-by-side installations of python: with virtual env
you can have different environments for python, and you avoid polluting your system
python installation with packages you don't need for your daily normal work, and
have independent environments for each of your developments.

You can read this resource to install virtualenv on your system: [A beginners guide to use virtualenv](http://www.pythonforbeginners.com/basics/how-to-use-python-virtualenv)

After installing virtual env, we are ready to create the virtual env for casanova project.

### 4.1 Create a virtualenv for casanova:

On casanova root folder, type this command:
```
virtualenv -p python2.7 python-env
```

### 4.2 Activate the new virtual environment

 enter the following command
```
source python-env/bin/activate
```

It will create a new folder with a bare python2.7 installation, and a special script
to activate this brand new environment, to activate it.

### 4.3 Install the required python packages

You will need to install several packages that are not provided with casa, but that 
you need in your system.

Also, make sure you have the package "python-dev" or "python-devel" (the name may change
for your specific linux distribution) in order to have the header "python.h" and many others
to compile some python packages.

Then, start installing the following packages:

```
pip install ipython
pip install jupyter
pip install numpy
pip install matplotlib
```

Now we're ready to install Casanova.

## 5. Prepare build directory

Create a directory where you will install casanova

```
mkdir build
```

Go to the build directory, and symlink your casa release to it, then return to
the project folder. If you have installed casa on the folder /opt/usr, you can
do the following:

```
cd build
ln -s /opt/usr/casa-release-4.5.2-el6 .
cd ..
```


## 6. Install Casanova

Run the script *install_casanova* with two parameters. The first one must be the
absolute path to your casanova repository (where this file is located), and the 
second one the absolute path to the target installation directory.

```
./install_casanova `pwd` `pwd`/build
```

* Edit `infodir` and `casainstalldir` parameters in `caspyter/install_casanova` file, and then run `caspyter/install_casanova`
* Edit `caspyter` parameter in `caspyter/casanova_startup` and then add this to your `.bashrc`:

```
alias caspyter="source /path/to/caspyter/casanova_startup"
```
 
### If you get an error like `CXXABI_1.3.8' not found`, you might want to try this:
```
strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep CXXABI_1.3.8
```
If it returns `CXXABI_1.3.8`, try with:
```
cp /usr/lib/x86_64-linux-gnu/libstdc++.so.6 /home/user/anaconda2/bin/../lib/libstdc++.so.6
```

