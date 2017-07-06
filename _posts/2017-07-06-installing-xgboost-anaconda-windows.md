---
layout: post
title: Installing XGBoost on Anaconda on Windows
categories: Installation
tags:
- XGBoost
- Installation
---

Step 1 : Install Anaconda     

Step 2 : Install **Git on Windows** (https://git-for-windows.github.io/)      

Step 3 : Launch **Git Bash window**

Step 4 : The directory in which the  code is to be installed in my case is **D:\XGBoostCode**     

```bash
cd D:/XGBoostCode
```
Step 5:

```bash
git clone --recursive https://github.com/dmlc/xgboost
cd xgboost
git submodule init
git submodule update

```
**Build Preparation**
The steps are performed to download the MinGW-64 for building the XGBoost code.       

--------------------------------------------------------------------------------------------------------------------------   

Step 6 : Download **MinGW-W64-install.exe**

Step 7 : Click on the installer.      
Changed the installation directory to **D:/MinGW-W64**.       
The make command and the runtime libraries are in this directory (look for the directory that contains **mingw32-make**).The files are downloaded in **D:/MinGW-W64/mingw64/bin**.         
Add this path to the Windows **PATH** variable.     

Step 8 : Then close the Git Bash terminal, and launch it again.  This will take into account the new Path variable.  To check you are fine, type the following     

```bash
which mingw32-make
```
This should return the path **D:/MinGW-W64/mingw64/bin/mingw32-make**

To make our life easier, let us alias it as follows:
```bash
alias make='mingw32-make'
```
--------------------------------------------------------------------------------------------------------------------------
**Build XGBoost**                       

Step 8 :Navigate to the directory where the XGBoost code exists. In  my case it is **D:/XGBoostCode/xgboost**

```bash
cd  D:/XGBoostCode/xgboost
```

Step 9 : Build the XGBoost code    

```bash
$ cd dmlc-core
$ make -j4
$ cd ../rabit
$ make lib/librabit_empty.a -j4
$ cd ..
$ cp make/mingw64.mk config.mk
$ make -j4
```
 The Build should produce the libraries **libxgboost.dll** in **D:\XGBoostCode\xgboost\lib**             

 Step 10 : Rename **libxgboost.dll** to **xgboost.dll**       

  --------------------------------------------------------------------------------------------------------------------------
**Install Python Module**                         
 Step 11 :        
Navigate to the python-package location.             

```bash
cd D:/XGBoostCode/xgboost/python-package

python setup.py install
```     
END.                        
--------------------------------------------------------------------------------------------------------------------------
