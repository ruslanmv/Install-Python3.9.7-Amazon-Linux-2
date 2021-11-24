# Script to install-Python3.9.7-Amazon-Linux-2 and Pandas Layer in AWS Lambda

Script to install Python 3.9.7 on Amazon Linux 2 AMI (HVM), SSD Volume Type 
ami-04ad2567c9e3d7893 (64-bit x86) / ami-0d1a4d53e40abecc4 (64-bit Arm)

First  you enter to your EC2 instance via ssh

```
ssh -i "yourkey.pem" ec2-user@ec2-XX-XX-XXX-X.compute-1.amazonaws.com
```

then

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

## Python packages in AWS Lambda 

If you are interested to create a layer lambda , for example pandas
Step 1: Create Python Virtual Environment

```
python3.9 -m venv test_venv
```

Step 2: Activate Virtual Environment

```
source test_venv/bin/activate
```

Step 3: Check Python Version

```
python --version  

```

Step 4: Create directory with name python

```
mkdir python
```

Step 5: Install pandas library in python directory created in Step 4

```
pip install pandas -t python  

```

Step 6: Zip python directory

```
zip -r pandas.zip python
```

Step 7: Download this pandas.zip

```
scp -i "yourkey.pem" ec2-user@ec2-XX-XX-XXX-X.compute-1.amazonaws.com://home/ec2-user/pandas.zip  C:\Users\username\Downloads
```

Step 8: Upload this pandas.zip to the lambda layer

