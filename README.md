# docker-mongo-openshift

This Docker image is based on https://github.com/docker-library/mongo/blob/master/3.2/Dockerfile modified that it runs on OpenShift:
* It does not create volumes for `/data/db` and `/data/configdb` as it is not necessary in our usecase
* It does not create the user and group `mongodb` as on OpenShift the containers are forced to run with a random user anyway
* It does not change the owner of  `/data/db` and `/data/configdb` to `mongodb`
* It changes the permission of `/data/db` and `/data/configdb` to 775, so that the random user which is part of the group `root` can access these files
