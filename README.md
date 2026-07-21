# Cloud-Engineer-Portfolio


## 🛑 Challenges & Troubleshooting
During the deployment process, I encountered real-world cloud networking and service configuration challenges:

### 1. HTTP Traffic Timeout (Security Group Misconfiguration)
* **Challenge:** After installing Apache and deploying the code, accessing the EC2 Public IP address resulted in a `Connection Timed Out` error in the web browser.
* **Root Cause:** By default, AWS Security Groups block all inbound traffic. Port 80 (HTTP) was not enabled to permit public web requests.
* **Resolution:** Navigated to the AWS EC2 Management Console, updated the Inbound Rules for the instance's Security Group, and added an **HTTP (Port 80)** rule allowing traffic from `0.0.0.0/0`. The web page loaded immediately after saving the rule.

### 2. Document Root Cleanup for Git Synchronization
* **Challenge:** Deploying code directly via `git clone` into `/var/www/html` initially failed or ran into conflicts due to existing temporary test files.
* **Resolution:** Cleared the web directory using `sudo rm -rf *` to ensure a clean deployment environment, followed by cloning the repository with `ssudo git clone https://github.com/IreneDevop/Cloud-Engineer-Portfolio.git  .` and restarting the web service (`sudo systemctl restart httpd`).
