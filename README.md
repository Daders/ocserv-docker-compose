![image](https://github.com/user-attachments/assets/6f6122c2-dfa9-4358-8358-1f0c3212e6e5)# ocserv-docker-compose
Docker compose for fast and easy ocserv configuration

# How to start
git clone https://github.com/Daders/ocserv-docker-compose.git
cd ocserv-docker-compose

docker-compose up -d

# Environment variables
CAMOUFLAGE_SECRET - special parameter which should be used in url for client connection
OCSERV_USER - user for client connection;
OCSERV_PASS - user password for client connection;
LETSENCRYPT_DOMAIN - domain in self generated certificate;
LETSENCRYPT_RENEW - how many days before certificate renew;

# Config directory
Config directory will contain certificates, passwd file and ocserv config.
If you want to reinit container than delete content of this folder.

# Manage Users
To manage users (e.g., add, delete, or update users), you can execute the following commands:

Add a new user:

docker-compose exec ocserv ocpasswd -c /etc/ocserv/ocpasswd newusername

Delete an existing user:

docker-compose exec ocserv ocpasswd -c /etc/ocserv/ocpasswd -d oldusername


# Setup client with NetworkManager
To connect to an OpenConnect VPN (such as the one you set up with Ocserv), you'll need the necessary OpenConnect and NetworkManager plugins. 
sudo apt update
sudo apt install network-manager-openconnect network-manager-openconnect-gnome

1. Click on the Network icon in the system tray
2. Select Settings or Network Settings
![image](https://github.com/user-attachments/assets/b6991c98-ce51-4182-b531-4299eb3c2078)
3. In the Network settings, click on the + (Add) button next to VPN to add a new VPN connection.
4. In the Add VPN dialog, choose Multi-protocol VPN client (OpenConnect) from the list.
![image](https://github.com/user-attachments/assets/14834abe-d29a-44e3-9711-f4fb4238cbb0)
5. Add gateway information. It's your domain (if you have real one) or ip address followed by /?yousecretkey where yousecretkey from CAMOUFLAGE_SECRET env variable
e.g. 172.0.0.1/?my_secret
![image](https://github.com/user-attachments/assets/14d01d43-a137-4155-b4da-f31b17bc1284)
6. Connect with new VPN connection
7. Check and approve self signed certificate -> I really know what i am doing -> Connect anyway
![image](https://github.com/user-attachments/assets/c3a3041a-5264-4ec6-a234-43953d40e2f5)
8. Enter your username and password form env variables OCSERV_USER and OCSERV_PASS

