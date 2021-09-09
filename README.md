# wrnr-docker

To create a docker environment with `docker-compose`

- Clone this repo

### Create IAM User with S3 Access ###
- Create a User Group (say s3users)
- Add `AmazonS3FullAccess` to permissons

- Create a User (s3user)
- Give it **_Programmatic Access_**
- Add the user to group created above
- Get the ACCESS_KEY_ID and SECRET_ACCESS_KEY

### Run in docker ###
- Run `docker-compose up` or `docker-compose start`
