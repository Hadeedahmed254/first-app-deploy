# Deploying a Node Js Application on AWS EC2

### Testing the project locally

1. Clone this project
```
git clone https://github.com/Hadeedahmed254/first-app-deploy.git
```
2. Setup the following environment variables - `(.env)` file
<img width="559" height="184" alt="Screenshot 2025-12-02 115546" src="https://github.com/user-attachments/assets/cbf6caec-e4c1-4d6b-9de0-6508f4543cf6" />

```
DOMAIN= ""
PORT=3000
STATIC_DIR="./client"

PUBLISHABLE_KEY=""
SECRET_KEY=""
```
3. Initialise and start the project
<img width="933" height="202" alt="Screenshot 2025-12-02 115553" src="https://github.com/user-attachments/assets/94adf662-c44d-4386-9f4b-190558137eb0" />

```
npm install
npm run start
```
<img width="1909" height="1020" alt="Screenshot 2025-12-02 124026" src="https://github.com/user-attachments/assets/6195f515-0b6b-43a2-b366-3521f5c86eb9" />

### Set up an AWS EC2 instance

1. Create an IAM user & login to your AWS Console
    - Access Type - Password
    - Permissions - Admin
2. Create an EC2 instance
    - Select an OS image - Ubuntu
    - Create a new key pair & download `.pem` file
    - Instance type - t2.micro
3. Connecting to the instance using ssh
```
ssh -i instance.pem ubunutu@<IP_ADDRESS>
```

### Configuring Ubuntu on remote VM

1. Updating the outdated packages and dependencies
```
sudo apt update
```
3. Install Git - [Guide by DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-22-04) 
4. Configure Node.js and `npm` - [Guide by DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-22-04)

### Deploying the project on AWS

1. Clone this project in the remote VM
```
git clone https://github.com/Hadeedahmed254/first-app-deploy.git
```
2. Setup the following environment variables - `(.env)` file
<img width="708" height="139" alt="Screenshot 2025-12-02 133332" src="https://github.com/user-attachments/assets/cb891c66-a339-40aa-b85a-173f7a789200" />

```
DOMAIN= ""
PORT=3000
STATIC_DIR="./client"

PUBLISHABLE_KEY=""
SECRET_KEY=""
```
> For this project, we'll have to set up an [Elastic IP Address](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html) for our EC2 & that would be our `DOMAIN`

3. Initialise and start the project
```
npm install
npm run start
```

> NOTE - We will have to edit the **inbound rules** in the security group of our EC2, in order to allow traffic from our particular port

<img width="1571" height="42" alt="Screenshot 2025-12-02 133417" src="https://github.com/user-attachments/assets/c2ed1678-a0c7-4fa7-9db5-05978cc0e210" />

### Project is deployed on AWS 🎉
<img width="1919" height="942" alt="Screenshot 2025-12-02 133556" src="https://github.com/user-attachments/assets/f756038b-7c23-4043-8396-3b35e33d84c3" />

