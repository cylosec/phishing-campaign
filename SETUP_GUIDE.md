## Setting Up a Vultr VPS for GoPhish

1. **Create an Instance**  
   - Provider: [Vultr](https://www.vultr.com)
   - Type: Cloud Compute (VC2)
   - OS: Ubuntu 22.04 LTS (64-bit)
   - Plan: 1 CPU / 1 GB RAM is fine for small campaigns
   - Enable IPv4, disable IPv6

2. **Secure the VPS**  
   - Create a new non-root user and disable root login
   - Update system:
     ```bash
     sudo apt update && sudo apt upgrade -y
     ```
   - Configure UFW:
     ```bash
     sudo ufw allow OpenSSH
     sudo ufw allow http
     sudo ufw allow https
     sudo ufw enable
     ```

3. **Install GoPhish**
   - Download from [GoPhish releases](https://github.com/gophish/gophish/releases)
   - Unzip and make executable:
     ```bash
     tar -xzf gophish-vX.X.X-linux-64bit.tar.gz
     cd gophish
     chmod +x gophish
     ```
   - Run GoPhish in the background:
     ```bash
     ./gophish &
     ```

4. **Edit GoPhish config** (`config.json`)
   - Admin server: `127.0.0.1:3333`
   - Phish server: `127.0.0.1:8080`

5. **Set Up Nginx Reverse Proxy**
   - Use the provided `nginx-gophish.conf` in `/configs`
   - Secure with Let’s Encrypt TLS via Certbot

6. **Verify Access**
   - Admin panel: `https://yourdomain.com/admin`
   - Phishing landing page: `https://yourdomain.com/portal`


==============================================================


## Hosting the Email Portal Page

1. **Create the Landing Page**
   - Modify `campaigns/landing-page.html` to match your phishing scenario
   - Make sure it’s harmless — for awareness testing only

2. **Place the File**
   - Copy `landing-page.html` into GoPhish’s `static/` folder:
     ```bash
     cp landing-page.html ~/gophish/static/portal/index.html
     ```

3. **Update GoPhish Landing Page Settings**
   - In GoPhish Admin, create a new landing page:
     - URL: `/portal`
     - Clone HTML from `landing-page.html`

4. **Test the Page**
   - Visit: `https://yourdomain.com/portal`
   - Confirm it's routed through Nginx and served correctly

* I found Vulr---

### 💡 VPS Alternatives

While this playbook uses [Vultr](https://www.vultr.com) to host GoPhish, you can use any VPS provider 
that supports custom Linux instances.

Other options include:

- [DigitalOcean](https://www.digitalocean.com)
- [Linode](https://www.linode.com)
- [AWS EC2](https://aws.amazon.com/ec2/)
- [Google Cloud Compute](https://cloud.google.com/compute)
- [Hetzner](https://www.hetzner.com/cloud)

> 🧠 I found **Vultr** to be the most affordable and user-friendly option — especially for quick setup, 
low monthly cost, and intuitive server management.

