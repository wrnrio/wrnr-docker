# wrnr-docker

*General instructions for installing WRNR.io on docker and in AWS OwnVPC mode.*<br>
In this model WRNR.io runs on the users VPC and uses an object storage model where all your data is stored and retrieved from your own S3 partition.
No data ever leaves your VPC.

### AWS instance suggested
WRNR.io is an I/O heavy solution storing ingest data and processed data and retrieving it to answer queries.<br>
All data should be stored locally and on SSD with atleast a `gp3` storage type.<br>
**It is suggested to create a storage volume of size depending on your daily ingest and it mounted to the EC2 instance.**<br>
**The recommended EC2 instance types are m5dn.large and above.**  

### Create IAM User with S3 Access ###
1. Create a User Group (say s3users) 
2. Add `AmazonS3FullAccess` to permissons 
3. Create a User (s3user) 
4. Give it **_Programmatic Access_** 
5. Add the user to group created above 
6. Get the ACCESS_KEY_ID and SECRET_ACCESS_KEY 

### Give it storage access on host ###
- Don't forget to create storage volume that can be attached to this mount point. This way your data will not be lost when moving instances or rebooting it.
- Create a folder for storing WRNR.io data (eg used here: /space)

### Run in docker ###
- Clone this repo
- Run `docker-compose up` or `docker-compose start`
