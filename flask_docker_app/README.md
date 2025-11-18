🚀 Flask Docker App --- Production-Ready Deployment on AWS EC2
============================================================

This project is a fully functional, modular **Flask web application** that is:

-   Cleanly structured

-   Fully Dockerized

-   Environment-variable driven

-   Compatible with Docker Compose

-   Successfully deployed on an **Ubuntu EC2 instance**

-   Exposed publicly over port **80**

-   Automatically restarted via Docker

It includes HTML templates, CSS, form handling, environment-based configuration, and production-style containerization.

* * * * *

📌 Features
-----------

-   🔹 Modular Flask application structure

-   🔹 HTML templates & CSS styling

-   🔹 Form handling with POST requests

-   🔹 `.env`-based configuration using `python-dotenv`

-   🔹 Dockerfile for production-ready builds

-   🔹 Docker Compose support

-   🔹 Deployment on AWS EC2 (Ubuntu)

-   🔹 Port 80 mapping for public access

-   🔹 Auto-restart container via `--restart unless-stopped`

-   🔹 Secure environment key handling

* * * * *

🧱 Project Structure
--------------------

<pre class="overflow-visible!" data-start="1910" data-end="2115"><div class="contain-inline-size rounded-2xl relative bg-token-sidebar-surface-primary"><div class="sticky top-9"><div class="absolute end-0 bottom-0 flex h-9 items-center pe-2"><div class="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs"></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="whitespace-pre!"><span><span>

flask_docker_app/
├── app/
│   ├── main.py
│   ├── templates/
│   │   ├── index.html
│   │   └── result.html
│   └── static/
│       └── style.css
├── .env
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
└── README.md
  
</span></span></code></div></div></pre>

* * * * *

🛠️ Technologies Used
---------------------

-   **Python 3.11**

-   **Flask**

-   **HTML5, CSS**

-   **Docker**

-   **Docker Compose**

-   **python-dotenv**

-   **AWS EC2 (Ubuntu 22.04 LTS)**

* * * * *

⚙️ Local Development
====================

### 1️⃣ Clone the repository

`git clone <your-repository-url>
cd flask_docker_app`

### 2️⃣ Create a virtual environment

`python3 -m venv venv
source venv/bin/activate`

### 3️⃣ Install dependencies

`pip install -r requirements.txt`

### 4️⃣ Run the app locally

`python app/main.py`

Now visit:\
👉 <http://localhost:5000>

* * * * *

🐳 Docker Usage
===============

Build the image
---------------

`docker build -t flask-docker-app .`

Run the container (local)
-------------------------

`docker run -d -p 5000:5000 flask-docker-app`

Visit:\
👉 <http://localhost:5000>

* * * * *

📦 With Docker Compose
======================

### Start using Compose

`docker compose up --build -d`

### Stop

`docker compose down`

* * * * *

☁️ Deployment on AWS EC2 (Ubuntu 20.04/22.04)
=============================================

### 1️⃣ Update system

`sudo apt update && sudo apt upgrade -y`

### 2️⃣ Install Docker

`sudo apt install -y ca-certificates curl gnupg lsb-release
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo\
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg]\
  https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" |\
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
sudo systemctl enable --now docker`

### 3️⃣ Allow non-root Docker (optional)

`sudo usermod -aG docker $USER
newgrp docker`

### 4️⃣ Clone your project

`git clone <your-repository-url>
cd flask_docker_app`

### 5️⃣ Create `.env`

`cat > .env <<EOF
FLASK_ENV=production
FLASK_DEBUG=False
FLASK_PORT=5000
SECRET_KEY=$(openssl rand -base64 32)
EOF`

### 6️⃣ Build & run container on port 80

`docker build -t flask-docker-app .
docker run -d --env-file .env -p 80:5000 --name Flask-App --restart unless-stopped flask-docker-app`

### 7️⃣ Test on EC2

`curl -I http://localhost`

### 8️⃣ Test from browser

`http://<your-ec2-public-ip>/`

* * * * *

🏗️ Best Practice: ALWAYS Use `docker build → tag → push`
---------------------------------------------------------

Even if your container is already running, **never use `docker commit`** to create images from a running container.\
This is a DevOps anti-pattern.

### ❌ Why you should NOT use `docker commit`

-   It creates **untracked**, **unreproducible** images

-   Cannot be version-controlled

-   Breaks CI/CD pipelines

-   No Dockerfile history

-   Encourages manual, inconsistent builds

-   Not suitable for production

### ✅ Recommended Workflow (ALWAYS)

Whenever you want to create or update an image, follow this clean, production-grade flow:

### **1️⃣ Build**

`docker build -t myapp:latest .`

### **2️⃣ Tag**

`docker tag myapp:latest <your-dockerhub-username>/myapp:latest`

Or with versioning:

`docker tag myapp:latest <your-dockerhub-username>/myapp:v1`

### **3️⃣ Push**

`docker push <your-dockerhub-username>/myapp:latest`

Or:

`docker push <your-dockerhub-username>/myapp:v1`

### **4️⃣ Pull & Run Anywhere**

On EC2, Kubernetes, or another machine:

`docker pull <your-dockerhub-username>/myapp:latest
docker run -d -p 80:5000 --env-file .env <your-dockerhub-username>/myapp:latest`

* * * * *

🧠 Why This Is the Right Approach
---------------------------------

-   Fully reproducible builds

-   Consistent deployments across all environments

-   Versioned images (traceable & manageable)

-   Compatible with CI/CD pipelines

-   Follows DevOps, Docker, and Cloud best practices

-   Makes debugging easier

-   Ensures your production image matches your source code

* * * * *
  

🔰 Screenshots
=========================

<img width="1365" height="702" alt="Screenshot from 2025-11-18 13-24-57" src="https://github.com/user-attachments/assets/b8960e51-b800-448a-8414-ec7d511d14e3" />

<img width="1365" height="488" alt="Screenshot from 2025-11-18 08-09-36" src="https://github.com/user-attachments/assets/9fdeab0f-1e02-4382-8a84-5e212acfd728" />

<img width="1365" height="295" alt="Screenshot from 2025-11-18 13-27-01" src="https://github.com/user-attachments/assets/79982e9b-a3cc-4196-b996-3857cd40b3c5" />


---

<img width="1365" height="702" alt="Screenshot from 2025-11-18 12-59-51" src="https://github.com/user-attachments/assets/5772f631-9f76-4b3e-a729-3a97703b227c" />

<img width="1365" height="488" alt="Screenshot from 2025-11-18 12-47-06" src="https://github.com/user-attachments/assets/f3b6e45d-d315-4d2e-a1fd-f8beecfcdc16" />

---

<img width="1365" height="488" alt="Screenshot from 2025-11-18 12-47-14" src="https://github.com/user-attachments/assets/d1ff6f61-29aa-40f2-8bc6-dc2e3c5b0cb2" />

<img width="1365" height="488" alt="Screenshot from 2025-11-18 12-47-20" src="https://github.com/user-attachments/assets/86545cae-ff73-4300-87b8-10de2af5a989" />

---

<img width="1365" height="702" alt="Screenshot from 2025-11-18 13-00-24" src="https://github.com/user-attachments/assets/3e415d37-f839-4ae4-98f5-929f0324372b" />

<img width="1365" height="702" alt="Screenshot from 2025-11-18 13-12-02" src="https://github.com/user-attachments/assets/384fbb57-180e-4cfe-9117-0dc407f836d9" />


* * * * *

🎓 What I Learned (Summary)
========================================

During this project, I gained hands-on expertise across both **web development** and **DevOps / cloud deployment** skills:

### 🔹 Flask Application Development

-   Structuring a modular Flask web app

-   Handling routing, POST forms, template rendering

-   Using Jinja2 templates and static files

### 🔹 Environment Variable Management

-   Creating `.env` files

-   Using `python-dotenv`

-   Securing Flask `SECRET_KEY`

-   Configuring debug mode and port via environment variables

### 🔹 Docker & Containerization

-   Writing a production-grade Dockerfile

-   Using `.dockerignore` to reduce image size

-   Building and running containers

-   Mapping ports (`80:5000`)

-   Auto-restart policies (`--restart unless-stopped`)

-   Inspecting logs and debugging container issues

### 🔹 Docker Compose

-   Defining services in `docker-compose.yml`

-   Mapping env files

-   Running multi-container apps

-   Using `docker compose up --build -d`

### 🔹 AWS EC2 Deployment

-   Installing Docker on Ubuntu

-   Managing firewall, ports, and security groups

-   Deploying containers to run on port 80

-   Testing with `curl`

-   Debugging port conflicts (80 already in use)

-   Ensuring Flask binds to `0.0.0.0`

### 🔹 Debugging & Networking

-   Fixing `Connection Refused` errors

-   Checking port bindings using `ss` and `lsof`

-   Using `curl` to test local and external access

-   Understanding docker-proxy behavior

* * * * *

🧭 Conclusion
=============

This project helped me build **end-to-end capability**:

💡 From writing a Python web app\
➡️ to containerizing it\
➡️ to deploying it on a real cloud EC2 VM\
➡️ and serving it publicly over port 80

I now understand how modern applications are developed, packaged, shipped, and deployed in real environments.

* * * * *

🤝 Contribution
===============

Feel free to fork, open issues, or submit pull requests.


* * * *

📌 Author
---------

**DEEPIKA NARENDRAN**
Project: Containerizing a Flask App with Docker

GitHub: @JoinDeeHub
