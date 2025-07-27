# Repository-name-lab3-custom-docker-nginx
This project demonstrates Lab 3 Part 2: Building and running a custom Docker container using a custom NGINX image on Amazon EC2.
Lab 3 Part Two – Custom Docker Container Deployment on EC2
**Lab Title**: Build & Run a Custom NGINX Docker Container on Amazon EC2 (Amazon Linux 2023)
**Student Name**: Dr. Ime Ben
**GitHub Repo**: lab3-custom-docker-nginx
**Lab Status**: ✅ Completed
**Date**: July 27, 2025
Objective
To learn how to create a custom Docker image using a Dockerfile with the nginx:alpine base image, run the container on an EC2 instance (Amazon Linux 2023), and confirm web deployment via a browser using the EC2 public IP.
Tools & Technologies Used
- AWS EC2 (Amazon Linux 2023)
- Docker Engine
- Dockerfile
- NGINX: Alpine Image
- GitHub
- SSH (via .pem key)
- VS Code / Nano
- Web Browser (Chrome)
Lab Steps and Commands

# Step 1: SSH into EC2
cd ~/Downloads
chmod 400 lab3-key.pem
ssh -i lab3-key.pem ec2-user@<EC2_PUBLIC_IP>

# Step 2: Create working directory
mkdir lab3-docker-app && cd lab3-docker-app

# Step 3: Create Dockerfile
nano Dockerfile

Dockerfile Content:
FROM nginx:alpine
RUN echo "<h1>Hello from Lab 3 Custom Docker Container!</h1>" > /usr/share/nginx/html/index.html

# Step 4: Build Docker image
sudo docker build -t lab3-custom-nginx .

# Step 5: Run Docker container on port 80
sudo docker run -d -p 80:80 --name lab3-nginx-container lab3-custom-nginx

Final Output (Browser)
Opened: http://34.243.172.110
Success Message Displayed: Hello from Lab 3 Custom Docker Container!
Outcome
- Learned how to write a basic Dockerfile using nginx:alpine.
- Successfully built and ran a custom Docker container on EC2.
- Exposed the Docker container via port 80 and accessed it using a public IP.
- Gained experience troubleshooting Docker permission issues with sudo.
Repo File Structure
lab3-custom-docker-nginx/
├── Dockerfile
├── README.md
└── screenshots/
    ├── step1.png
    ├── step2.png
    ├── ...
    └── step12.png
Notes
- Docker permission issues were resolved using sudo.
- Amazon Linux 2023 does not enable Docker for non-root users by default.
- All screenshots stored in the screenshots/ folder for easy reference.
