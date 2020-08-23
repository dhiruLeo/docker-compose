 # To Setup PostgreSQL & Cronjob to take Backups

` kubectl create -f pgsql-cm.yaml `

### Step 2. Replace your Database creds.
Replace database creds in [pgsql-cm.yaml]
!Attention: This is for simplicity these should be replaced with Secrets.

### Step 3. Create the resources

` kubectl create -f pgsql-deploy.yaml `

` kubectl create -f cronjob-pv.yaml `

` kubectl create -f cronjob-deployment.yaml `

` kubectl create -f minio-pv.yaml `

 ` POSTGRES_DB: awesomedb `
 ` POSTGRES_USER: amazinguser `
 ` POSTGRES_PASSWORD: perfectpassword `
## Contributing and Modifying

1. Make your desired changes and build the container:

` docker build -t dhirujackal/postgresql7:12.3.1 . `

2. Test it locally by executing the command below:

` docker run -v /d/backup:/pg_backup dhirujackal/postgresql7:12.3.1 `

### Step 1. Pull the image

` docker push dhirujackal/postgresql7:12.3.1 `

### Step 2. Run and map to your drive (e.g. /d/backup)
` docker run -v /host/backup:/pg_backup dhirujackal/postgresql7:12.3.1 `


## To setup NFS Server On Centos And use nfs type Persistent Volume

` yum install nfs-utils `

` mkdir /var/nfsshare `

` chmod -R 755 /var/nfsshare `

` vi /etc/exports `

` systemctl start rpcbind `

` systemctl start nfs-server  `

` systemctl start nfs-lock `

` systemctl start nfs-idmap `

 ## To Create Database inside running pgsql Pod

 ` kubectl exec -it pgsql-terraform-0 -- psql -h node-ip -U amazinguser --password -p nodeport awesomedb `

` sudo -u postgres psql -d terraform_backend `

` createdb terraform_backend `

` CREATE DATABASE terraform_backend; `

` DROP DATABASE terraform_backend; `

## To Interact with pgsql 

` sudo passwd postgres `

` \dt * `

` \l+ terraform_backend `

` terraform workspace list `

` terraform workspace new dhirendra `

## Initializing Postgres as terraform Backend to store Terraform State Files.

 ` terraform init -backend-config='conn_str=postgres://amazinguser:perfectpassword@node-ip:31186/terraform_backend?sslmode=disable' `
 