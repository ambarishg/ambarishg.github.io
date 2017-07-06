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
