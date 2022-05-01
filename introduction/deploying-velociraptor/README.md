# 🛠 Deploying Velociraptor

Deployment of <mark style="color:green;">**Velociraptor**</mark> is modular and consists of a <mark style="color:green;">**Velociraptor Server**</mark>** ** and multiple endpoints running the <mark style="color:green;">**Velociraptor Client**</mark><mark style="color:green;">.</mark>

The main components of deployment include:

1. The `client` is the instance of the <mark style="color:green;">**Velociraptor**</mark> agent running on the endpoint.
2. The `frontend` is the server component communicating with the client.
3. The `gui` is the web application server that presents the administrative interface.
4. The `API` server is used to accept API requests.

For this tutorial the <mark style="color:green;">**Velociraptor Server**</mark> was deployed as a Self-Signed SSL to an Ubuntu workstation. A Linux and Windows workstation were brought on as client machines.&#x20;

To begin deployment, from a windows box: download the latest version of the windows amd64 executable from the official GitHub: [https://github.com/Velocidex/velociraptor/releases](https://github.com/Velocidex/velociraptor/releases)\
\
Then follow the steps for Option A as outlined in the official documentation for installing and deploying <mark style="color:green;">**Velociraptor**</mark>: [https://docs.velociraptor.app/docs/deployment/self-signed/](https://docs.velociraptor.app/docs/deployment/self-signed/)\
