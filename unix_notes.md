## Core Unix commands 

Most unix commands have super short names, which makes them quick to
type but annoying to lean. Major file system related commands include:

pwd: Print working directory
ls: List files and directories
cd: Change Directory
mkdir: Make a new directory
rm: Remove files and directory (delete)
cp: Copy files or dirs (source > destination)
mv: Move files or dirs (basically re-name)
nano: A wee text editor (very basic but always available)

curl:       Download files from web or ftp
wget:       Download files from the web
tar -zxvf:  UnTar (Unpackage) Tar archive files
gunzip:     UnZip files
# $PATH:      The places (dirs) to look for programs

## AWS EC2 Instance

Connect to my instance with: 

# ssh -i "bimm143_austin.pem" ubuntu@ec2-16-147-10-5.us-west-2.compute.amazonaws.com

Secure Copy files between machines, in this case from our instance to our laptop

scp -i ~/Downloads/bimm143_austin.pem ubuntu@ec2-16-147-10-5.us-west-2.compute.amazonaws.com:/home/ubuntu/work/bimm143_github/class16/results.txt .


## Class 17 Instance

ssh -i ~/Downloads/bimm143_austin.pem ubuntu@ec2-44-247-255-211.us-west-2.compute.amazonaws.com

export KEY=~/Downloads/bimm143_austin.pem
export SERVER=ubuntu@ec2-44-247-255-211.us-west-2.compute.amazonaws.com

ssh -i $KEY $SERVER


# scp -r -i $KEY $SERVER:~/*_quant



i








