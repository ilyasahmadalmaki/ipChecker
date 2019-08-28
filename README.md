# ipChecker
Tool to check if a given IP is a node tor or an open proxy.

# Why?
Sometimes all your throttles are not enough to stop brute force attacks or any kind of massive attacks, so it can help you to drop, some attackers who use tor or open proxies.

# How it works
IPChecker memiliki beberapa plugin yang memotong proksi ips dari situs publik, semua ip ini disimpan dalam database di mana Anda dapat berkonsultasi dengan menggunakan API yang disediakan. Pada dasarnya, ketika Anda menjalankan perintah `` `make run``` itu akan mulai buruh pelabuhan membuat satu layanan untuk API yang dapat ditingkatkan dan mulai dengan 4 kontainer, layanan lain untuk pembaru yang merupakan skrip yang bertanggung jawab untuk menjalankan semua plugin yang mengambil semua proxy dan node, layanan ini dimulai dengan hanya satu kontainer, dan akhirnya satu wadah untuk mongodb tempat semua data disimpan. Kontainer berkomunikasi melalui jaringan buruh pelabuhan yang disebut ipchecker-network, dan hanya port 8080 yang terpapar tempat Anda mengonsumsi API. Untuk menghindari banyak false positive, api hanya mengembalikan ip dari hari ini, karena hampir proxy server dan node, adalah ip dinamis.

# Plugins

- cloudproxies.com
- gatherproxy.com
- hidemy.name
- httptunnel.ge
- multiproxy.org
- nordvpn.com
- proxy-list.org
- rebro.weebly.com
- samair.ru
- torstatus.blutmagie.de
- xroxy.com

# Install
```bash
git clone https://github.com/mthbernardes/ipChecker
cd ipchecker/
```
Option to execute the service:

| Command        | Description      |
| -------------- | ----------------:|
| ```make buld```      | Build all images |
| ```make run```      | Build and run all images |
| ```make stop```      | Stop all services |
| ```make wipe```      | Stop all services and wipe all images and mongodb data |

If you don't have docker, you'll need to install it. ([Docker Install](https://docs.docker.com/install/))

# Basic Usage
Here is the basic usage of the API, for see all the endpoints and access the / endpoint.

| Endpoint        | method           | Description  |
| ------------- |:-------------:| -----:|
| /      | GET | Document of all endpoints |
| /statistics      | GET      | Informations about blocked requests, allowed requests, and number of all proxies on database(per day) |
| /ips?ip=127.0.0.1 | GET | Search for a single IP on database |
| /all | GET      | return all ips on database |


