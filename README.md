# Script to install-Python3.9.7-Amazon-Linux-2

Script to install Python 3.9.7 on Amazon Linux 2 AMI (HVM), SSD Volume Type 
ami-04ad2567c9e3d7893 (64-bit x86) / ami-0d1a4d53e40abecc4 (64-bit Arm)

```
sudo yum -y groupinstall "Development Tools"
sudo yum -y install gcc openssl-devel bzip2-devel libffi-devel
wget https://www.python.org/ftp/python/3.9.7/Python-3.9.7.tgz
tar zxvf Python-3.9.7.tgz
cd Python-3.9.7/
./configure
make
sudo make altinstall
python3.9 --version
```

Python packages in AWS Lambda 

If you are interested to create a layer lammbda , for exmaple pandas
Step 1: Create Python Virtual Environment
python3.9 -m venv test_venv
Step 2: Activate Virtual Environment
source test_venv/bin/activate
Step 3: Check Python Version
python --version  
Step 4: Create directory with name python
mkdir python
Step 5: Install pandas library in python directory created in Step 4
pip install pandas -t python  
Step 6: Zip python directory
zip -r pandas.zip python
Step 7: Download this pandas.zip
Step 8: Upload this pandas.zip to the lambda layer
