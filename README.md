# Muein's Cloud Engineer Portfolio

This repository contains the source code for the personal portfolio website of **Muein**, a Cloud & DevOps Engineer. The portfolio showcases professional experience, skills, and featured projects in Cloud Infrastructure, Automation, and CI/CD.

## 🚀 Live Demo

*The website is designed to be hosted on an AWS EC2 instance using Nginx.*

## 🛠️ Project Architecture & Tech Stack

- **Frontend**: HTML5, CSS3 (Vanilla), JavaScript
- **Icons**: [Lucide Icons](https://lucide.dev/)
- **Hosting**: AWS EC2
- **Web Server**: Nginx
- **CI/CD Pipeline**: GitHub Actions

## 📂 Repository Structure

- `index.html` - The main and single-page portfolio application.
- `style.css` - Custom styling for the application (modern UI/UX).
- `ameya-services.html`, `daksh-concentrix.html`, `wns-global.html` - Detailed pages for professional work experiences.
- `Muein_Resume.pdf` - Downloadable resume file.
- `.github/workflows/deploy.yml` - GitHub Actions workflow file that automates deployment to the AWS EC2 instance.

---

## 💻 Local Setup & Development

If you'd like to run or modify this project locally, simply follow these steps. No build tools (like Node.js or Webpack) are required as it uses pure HTML/CSS/JS.

### 1. Clone the Repository
```bash
git clone https://github.com/mueinofficeuse-eng/Muein-Portfolio.git
```

### 2. Navigate to the Directory
```bash
cd Muein-Portfolio
```

### 3. Open in Browser
You can simply double-click the `index.html` file or use a local live server (like VS Code's "Live Server" extension) to view the project.
```bash
# If using a Mac, you can open it via terminal:
open index.html

# If using Linux:
xdg-open index.html

# If using Windows:
start index.html
```

---

## ☁️ Deployment Pipeline (CI/CD)

The portfolio features an automated deployment pipeline powered by GitHub Actions. Every time code is pushed to the `main` branch, the changes are automatically packaged and deployed to the target AWS EC2 instance.

### Pipeline Workflow Steps
1. Checkout the latest code.
2. SSH into the EC2 instance and clean the `/var/www/html/*` directory.
3. SCP the new files (excluding `.git` and `.github` directories) to `/var/www/html`.
4. Restart the Nginx service to serve the latest content.

### Required GitHub Secrets
To make the pipeline work on your own fork/repository, you need to configure the following Secrets in your GitHub repository settings (**Settings > Secrets and variables > Actions**):

- `EC2_HOST`: The Public IP or Domain Name of your EC2 instance.
- `EC2_USER`: The SSH username (e.g., `ubuntu`, `ec2-user`).
- `EC2_SSH_KEY`: The private SSH key (`.pem` contents) used to authenticate with the EC2 machine.

### Server Commands (For Reference)
If you need to manually configure the Nginx web server or manage the instance, here are the common commands:

**Restart Nginx:**
```bash
sudo systemctl restart nginx
```

**Check Nginx Status:**
```bash
sudo systemctl status nginx
```

**Clear HTML Directory Manually:**
```bash
sudo rm -rf /var/www/html/*
```

## 📬 Contact functionality
The contact form in the portfolio relies on [FormSubmit](https://formsubmit.co) to send emails directly to `muein.officeuse@gmail.com` using Ajax without requiring a backend server.
