# Cyber Risk Assessment Lab

## Project Overview
This cyber risk assessment and threat modeling lab simulates a real-world security evaluation lifecycle for a web application. In this project I will design a login portal using Flask, then perform vulnerability assessments, implement patches, and test the patches to see if they mitigated any vulnerabilities.

---

## Objectives
- Build a web application (login page) using Flask
- Conduct a STRIDE threat model for the application
- Perform vulnerability scans with the tools Nmap, Nikto, and OWASP ZAP
- Implement security hardening controls
- Validate improvements using the same tools

---

## Planning and Architecture

### Network Architecture
- Kali Linux (Attacker/Testing VM)
- Ubuntu (Web app design and deployment)
- Internet

![Diagram drawio](https://github.com/user-attachments/assets/bf48e4e8-4d5a-4f42-84af-a7459ec8f9f6)

### STRIDE Threat Model

![Threat Model](https://github.com/user-attachments/assets/88d4ffb5-c4cd-4caf-ade8-46d7a2018729)

---

## Web App Development
- Built a simple login application with a Python and Flask framework backend

Project file structure: ![1  File Structure](https://github.com/user-attachments/assets/dbb5eac7-14ea-491f-bbcc-1bcf56110355)

Original code for the login page: ![2  logindotpy original](https://github.com/user-attachments/assets/5d7707ba-5919-4c92-9047-7d46b3f9f0bc)

Login Page HTML: ![3  OG HTML](https://github.com/user-attachments/assets/69749598-ae99-4a06-a587-453c99a10005)

Login Page: ![7  Login w creds](https://github.com/user-attachments/assets/78228b7a-963d-4229-8fee-fd881bbbe30a)


### Intentional Vulnerabilities
- No CSRF protection
- Lack of secure headers
- Weak authentication logic

---

## Vulnerability Analysis

### Nmap Scan
- Port 5000 (Flask) was open
- Verified host reachability and service exposure
![10  NMAP scan](https://github.com/user-attachments/assets/5acbb979-078b-4519-9de6-1116e2f14cb0)

### Nikto Scan
- Missing 'X-Frame-Options'
- Missing 'X-Content-Type-Options'
- Default Werkzeug server headers exposed
![11  Nikto Scan](https://github.com/user-attachments/assets/556cc0a0-c096-46e7-b92c-546289d6d139)

### OWASP ZAP Scan
- Missing CSRF Protection
- Absence of secure headers
- No anti-clickjacking header
![14  Anti CSRF](https://github.com/user-attachments/assets/7c4b282b-8850-48d4-9842-47b3adbce362)

---

## Security Hardening

### Updates Made to 'login.py'
- Enabled Flask-WTF with CSRF protection
- Added '@after_request' headers for:
  - 'X-Frame-Options'
  - 'X-Content-Type-Options'
  - 'X-XSS-Protection'

Final login.py file with security features implemented: ![final login](https://github.com/user-attachments/assets/19f24879-67dc-4927-b52a-4043abdde5bc)

---

## Re-Testing

### Nikto Scan
- Improved Results
- Some headers still missing
![18  Nikto After](https://github.com/user-attachments/assets/92d70a00-7426-4a2c-9f45-10d89c55068c)

### ZAP Scan
- CSRF Alert Removed
- Missing CSP header remains, not yet implemented
![19  ZAP AFTER](https://github.com/user-attachments/assets/d888e14e-caa6-4c30-8776-233dcc5b9e88)

---

## Cyber Risk Assessment Report

![20  report](https://github.com/user-attachments/assets/a70ddc9e-32f6-4040-bbf0-9a8db0ae5c53)

---

## Key Takeaways
- Threat modeling and network diagram planning helps to visualize and expose risks before deployment.
- Using tools like ZAP, Nikto, and Nmap, helped simulate real vulnerability scanning workflows.
- Risk remediation and retesting mirror real-world security patching processes.
