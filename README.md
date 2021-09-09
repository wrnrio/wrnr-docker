# wrnr-docker

*General instructions for installing WRNR.io on docker and in AWS OwnVPC mode.*<br>
In this model WRNR.io runs on the users VPC and uses an object storage model where all your data is stored and retrieved from your own S3 partition.
No data ever leaves your VPC.

### AWS instance suggested
WRNR.io is an I/O heavy solution storing ingest data and processed data _temporarily_ and retrieving it to answer queries.<br>
All data should be stored locally and on SSD with atleast a `gp3` storage type.<br>
**It is suggested to create a storage volume of size depending on your daily ingest and it be mounted to the EC2 instance.
By creating a mounted volume, the container can be refreshed and/or moved to a different EC2 instance without loss of data.**<br>
_The recommended EC2 instance types are m5dn.large and above._

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
- Create an EC2 instance (preferably m5dn.large or bigger)
- Clone this repo
- Run `docker-compose up` or `docker-compose start`

## Using WRNR.io ##
- Login to the UI by selecting the IP address of the EC2 instance
- The product comes with a self-signed certificate that can be accepted by _Firefox_ or with _Chrome_ download the certificate and import to keychain (for mac only)
- Signup and confirm code and you're all set to use WRNR.io
