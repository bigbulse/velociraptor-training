# 🐧 Setting up a Linux Client

### Installation

During installation the <mark style="color:green;">Velociraptor</mark> installer created two configuration files: one for the server and one for clients.\
\
Use the client configuration  file to create  a client Debian package with the following command:

<mark style="color:blue;">`velociraptor  --config client.config.yaml rpm client`</mark>\
``\
``\
``SCP this to the client endpoint.\
\
On the client endpoint, install the package with this command:

<mark style="color:blue;background-color:green;">`sudo rpm -i velociraptor_x.x.x_client.rpm`</mark>\


### Confirm in the GUI

The <mark style="color:green;">Velociraptor</mark> Admin GUI at <mark style="color:blue;">`https://SERVER-IP:8889/`</mark>will dynamically update with the new client machine. At the top left of the Admin GUI is a search bar. The newly added client can be seen by searching for their hostname using the search query <mark style="color:blue;">`host:hostname`</mark>or by clicking the drop down menu to the right, then clicking "Show All".

![](<../../.gitbook/assets/search\_clients (1).png>)

