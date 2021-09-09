# wrnr-docker

To create a docker environment with `docker-compose`

- Clone this repo

### Create IAM User with S3 Access ###
1. Create a User Group (say s3users) 
2. Add `AmazonS3FullAccess` to permissons 
3. Create a User (s3user) 
4. Give it **_Programmatic Access_** 
5. Add the user to group created above 
6. Get the ACCESS_KEY_ID and SECRET_ACCESS_KEY 

### Run in docker ###
- Run `docker-compose up` or `docker-compose start`
