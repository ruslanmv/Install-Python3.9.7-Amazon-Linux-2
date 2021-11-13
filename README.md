# Script to install-Python3.9.7-Amazon-Linux-2
#Script to install Python 3.9.7 on Amazon Linux 2 AMI (HVM), SSD Volume Type 
#ami-04ad2567c9e3d7893 (64-bit x86) / ami-0d1a4d53e40abecc4 (64-bit Arm)

sudo yum -y groupinstall "Development Tools"
sudo yum -y install gcc openssl-devel bzip2-devel libffi-devel
wget https://www.python.org/ftp/python/3.9.7/Python-3.9.7.tgz
tar zxvf Python-3.9.7.tgz
cd Python-3.9.7/
./configure
make
sudo make altinstall
python3.9 --version
