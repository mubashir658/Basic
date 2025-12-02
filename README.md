🟢 STEP 1 — Launch EC2 instance

Log into AWS Academy

Start AWS Lab

Go to EC2 service → Launch Instance

Configure EC2 instance:

Name: ubuntu (any name)

AMI: Ubuntu Server (Free tier eligible)

Architecture: 64-bit

Instance Type: t2.micro

Create new Key Pair (.pem file) → Download and save safely

Network security → Allow HTTP & HTTPS

Storage: Default 8GB

Click Launch Instance

Wait for 2/2 status checks → Passed

Select the instance → click Connect

WEEK-12

🟢 STEP 2 — Connect to EC2 using SSH

Copy SSH command from AWS console (example):

ssh -i "yourkey.pem" ubuntu@<public-ip>


Open PowerShell / Git Bash

Navigate to folder where .pem is stored:

cd <path_of_pem_file>


Paste SSH command and connect

WEEK-12

🟢 STEP 3 — Install required software on EC2

Run the commands:

sudo apt update
sudo apt-get install docker.io
sudo apt install git
sudo apt install nano


WEEK-12

🟢 STEP 4 — Create project and push to GitHub

👉 On your local computer (not EC2)

Create folder → add index.html

Open Git Bash in that folder and run:

git init
git add .
git commit -m "first commit"


Create new repository on GitHub

Add remote and push:

git branch -M main
git remote add origin <repo-https-url>
git push -u origin main


WEEK-12

🟢 STEP 5 — Clone repository in EC2

👉 On EC2 terminal:

git clone <repo-https-url>
cd <repo-folder-name>
ls


WEEK-12

🟢 STEP 6 — Create Docker image

Inside cloned folder:

nano Dockerfile


Write inside Dockerfile:

FROM nginx:alpine
COPY . /usr/share/nginx/html


Save → CTRL+O → ENTER → CTRL+X

Build Docker image:

sudo docker build -t mywebapp .


WEEK-12

🟢 STEP 7 — Run Docker container and expose port 80
sudo docker run -d -p 80:80 mywebapp


WEEK-12

🟢 STEP 8 — Access web page

Go to AWS → EC2 instance page

Copy Public IPv4 Address

Open browser and paste:

http://<public-ip>


→ You will see your index.html webpage deployed live 🎉

WEEK-12

🔴 FINAL REQUIRED SHUTDOWN STEPS (MUST DO)

Stop container in EC2:

sudo docker ps
sudo docker stop <container-id>


Terminate EC2 instance:

AWS → Instances → Instance State → Terminate

Then click End Lab

WEEK-12
