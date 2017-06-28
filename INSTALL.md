## Install Caspyter locally

This has been taken from GasparCorrea contribution
 
## 1. Make sure you have the following dependencies
 
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
tar zxf /home/caspyter/casa-release-4.5.2-el6.tar.gz
```
 
## 3. Install patchELF
 
```
sudo sh /path/to/caspyter/scripts/patchELF.sh
```

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

## 4. Install Casanova
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

