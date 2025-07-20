# Load Balancer Configuration Project

This project sets up a redundant web infrastructure using two web servers and a load balancer. It automates the configuration of Nginx on both web servers with a custom HTTP header and installs HAProxy on a third server to distribute traffic using a round-robin algorithm.

---

## 🧠 Project Goals

- Ensure redundancy and scalability for web services
- Automate server provisioning using Bash scripts
- Track server responses using a custom header: `X-Served-By`
- Configure HAProxy to load-balance HTTP traffic between web-01 and web-02

---

## 🛠 Files and Scripts

| Script                            | Purpose                                                        |
|-----------------------------------|----------------------------------------------------------------|
| `0-custom_http_response_header`   | Installs and configures Nginx with a custom response header    |
| `1-install_load_balancer`         | Installs and configures HAProxy with round-robin distribution  |

Each script is designed to be executed on a freshly initialized Ubuntu 16.04 server.

---

## ⚙️ Configuration Details

### Web Servers (`web-01` and `web-02`)
- Nginx configured with `X-Served-By` header
- Header value equals the hostname of each web server

### Load Balancer (`lb-01`)
- HAProxy distributes traffic using roundrobin
- Traffic is routed to both web servers on port 80

---

## 🚀 Usage

Run each script individually on its designated server:

```bash
sudo ./0-custom_http_response_header     # on web-01 and web-02
sudo ./1-install_load_balancer           # on lb-01

