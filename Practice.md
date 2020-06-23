<div align=right>
    <a href="https://github.com/LunightLab">
        <img alt="author" src= "https://img.shields.io/badge/author-lunight-blue?style=glat-square" target="_blank"></a>
    </a>
    <a href="https://github.com/LunightLab/LuLabTemplate">
        <img alt="template version" src= "https://img.shields.io/badge/template%20version-1.0-blue?style=glat-square" target="_blank"></a>
    </a>
</div>

Practice
========

**<div align=right> 워크샵 내용정리 </div>**

### Docker Simple test

```bash
Microsoft Windows [Version 10.0.18362.836]
(c) 2019 Microsoft Corporation. All rights reserved.

C:\Users\user06>docker container ls
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
6fd6e037700f        ubuntu              "top"               3 minutes ago       Up 3 minutes                            sleepy_perlman

C:\Users\user06>docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                     PORTS                     NAMES
6fd6e037700f        ubuntu              "top"                    3 minutes ago       Up 3 minutes                                         sleepy_perlman
a48e580e6af9        mongo:3.4           "docker-entrypoint.s…"   2 weeks ago         Exited (255) 6 hours ago   0.0.0.0:8081->27017/tcp   mongo
f39bacb59a78        nginx               "/docker-entrypoint.…"   2 weeks ago         Exited (255) 6 hours ago   0.0.0.0:8080->80/tcp      nginx
919c5f36bf3f        ubuntu              "top"                    2 weeks ago         Exited (255) 6 hours ago                             wizardly_borg

C:\Users\user06>docker container exec -it 6fd6e037700f
"docker container exec" requires at least 2 arguments.
See 'docker container exec --help'.

Usage:  docker container exec [OPTIONS] CONTAINER COMMAND [ARG...]

Run a command in a running container

C:\Users\user06>docker container exec -it 6fd6e037700f bash
root@6fd6e037700f:/# ls
bin  boot  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@6fd6e037700f:/# ps -ex
  PID TTY      STAT   TIME COMMAND
    1 pts/0    Ss+    0:00 top PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin HOSTNAME=6fd6e037700f TERM=xterm HOME=/root
    6 pts/1    Ss     0:00 bash PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin HOSTNAME=6fd6e037700f TERM=xterm HOME=/root
   15 pts/1    R+     0:00 ps -ex HOSTNAME=6fd6e037700f PWD=/ HOME=/root LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40
root@6fd6e037700f:/#
```

###Pyton app test

**app.py**

```pyton
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello():
    return "hello world!"

if __name__ == "__main__":
    app.run(host="0.0.0.0")
```

**practice**

```
파이썬 설치
C:\Users\user06\Desktop>python3 --version

C:\Users\user06\Desktop>pip3 --version
pip 19.2.3 from c:\users\user06\appdata\local\programs\python\python38-32\lib\site-packages\pip (python 3.8)

C:\Users\user06\Desktop>pip3 install flask
Collecting flask
  Downloading https://files.pythonhosted.org/packages/f2/28/2a03252dfb9ebf377f40fba6a7841b47083260bf8bd8e737b0c6952df83f/Flask-1.1.2-py2.py3-none-any.whl (94kB)
     |████████████████████████████████| 102kB 226kB/s
Collecting Jinja2>=2.10.1 (from flask)
  Downloading https://files.pythonhosted.org/packages/30/9e/f663a2aa66a09d838042ae1a2c5659828bb9b41ea3a6efa20a20fd92b121/Jinja2-2.11.2-py2.py3-none-any.whl (125kB)
     |████████████████████████████████| 133kB 344kB/s
Collecting click>=5.1 (from flask)
  Downloading https://files.pythonhosted.org/packages/d2/3d/fa76db83bf75c4f8d338c2fd15c8d33fdd7ad23a9b5e57eb6c5de26b430e/click-7.1.2-py2.py3-none-any.whl (82kB)
     |████████████████████████████████| 92kB 453kB/s
Collecting itsdangerous>=0.24 (from flask)
  Downloading https://files.pythonhosted.org/packages/76/ae/44b03b253d6fade317f32c24d100b3b35c2239807046a4c953c7b89fa49e/itsdangerous-1.1.0-py2.py3-none-any.whl
Collecting Werkzeug>=0.15 (from flask)
  Downloading https://files.pythonhosted.org/packages/cc/94/5f7079a0e00bd6863ef8f1da638721e9da21e5bacee597595b318f71d62e/Werkzeug-1.0.1-py2.py3-none-any.whl (298kB)
     |████████████████████████████████| 307kB 409kB/s
Collecting MarkupSafe>=0.23 (from Jinja2>=2.10.1->flask)
  Downloading https://files.pythonhosted.org/packages/93/b8/95b1c38f5b00ed2c0d16cf65f2b07a5ae73eeacf66d2010c0e934737d1d9/MarkupSafe-1.1.1-cp38-cp38-win32.whl
Installing collected packages: MarkupSafe, Jinja2, click, itsdangerous, Werkzeug, flask
Successfully installed Jinja2-2.11.2 MarkupSafe-1.1.1 Werkzeug-1.0.1 click-7.1.2 flask-1.1.2 itsdangerous-1.1.0
WARNING: You are using pip version 19.2.3, however version 20.1.1 is available.
You should consider upgrading via the 'python -m pip install --upgrade pip' command.

C:\Users\user06\Desktop>
```

###Docker test

**DockerFile**

```
FROM python:3.6.1-alpine
 RUN pip install flask
 CMD ["python","app.py"]
 COPY app.py /app.py'
```

**practice**

```
C:\Users\user06\Desktop\sample>docker image build -t python-hello-world .
Sending build context to Docker daemon  3.072kB
Step 1/4 : FROM python:3.6.1-alpine
3.6.1-alpine: Pulling from library/python
90f4dba627d6: Pull complete                                                                                          19bc0bb0be9f: Pull complete                                                                                          e05eff433916: Pull complete                                                                                          e70196200a87: Pull complete                                                                                          a6d780959950: Pull complete                                                                                          Digest: sha256:0945574465b917d524ce9b748479a286c2ed3c5a97311ac5950464907d4d8b53
Status: Downloaded newer image for python:3.6.1-alpine
 ---> ddd6300d05a3
Step 2/4 : RUN pip install flask
 ---> Running in c033b9e26a5d
Collecting flask
  Downloading https://files.pythonhosted.org/packages/f2/28/2a03252dfb9ebf377f40fba6a7841b47083260bf8bd8e737b0c6952df83f/Flask-1.1.2-py2.py3-none-any.whl (94kB)
Collecting click>=5.1 (from flask)
  Downloading https://files.pythonhosted.org/packages/d2/3d/fa76db83bf75c4f8d338c2fd15c8d33fdd7ad23a9b5e57eb6c5de26b430e/click-7.1.2-py2.py3-none-any.whl (82kB)
Collecting itsdangerous>=0.24 (from flask)
  Downloading https://files.pythonhosted.org/packages/76/ae/44b03b253d6fade317f32c24d100b3b35c2239807046a4c953c7b89fa49e/itsdangerous-1.1.0-py2.py3-none-any.whl
Collecting Werkzeug>=0.15 (from flask)
  Downloading https://files.pythonhosted.org/packages/cc/94/5f7079a0e00bd6863ef8f1da638721e9da21e5bacee597595b318f71d62e/Werkzeug-1.0.1-py2.py3-none-any.whl (298kB)
Collecting Jinja2>=2.10.1 (from flask)
  Downloading https://files.pythonhosted.org/packages/30/9e/f663a2aa66a09d838042ae1a2c5659828bb9b41ea3a6efa20a20fd92b121/Jinja2-2.11.2-py2.py3-none-any.whl (125kB)
Collecting MarkupSafe>=0.23 (from Jinja2>=2.10.1->flask)
  Downloading https://files.pythonhosted.org/packages/b9/2e/64db92e53b86efccfaea71321f597fa2e1b2bd3853d8ce658568f7a13094/MarkupSafe-1.1.1.tar.gz
Building wheels for collected packages: MarkupSafe
  Running setup.py bdist_wheel for MarkupSafe: started
  Running setup.py bdist_wheel for MarkupSafe: finished with status 'done'
  Stored in directory: /root/.cache/pip/wheels/f2/aa/04/0edf07a1b8a5f5f1aed7580fffb69ce8972edc16a505916a77
Successfully built MarkupSafe
Installing collected packages: click, itsdangerous, Werkzeug, MarkupSafe, Jinja2, flask
Successfully installed Jinja2-2.11.2 MarkupSafe-1.1.1 Werkzeug-1.0.1 click-7.1.2 flask-1.1.2 itsdangerous-1.1.0
You are using pip version 9.0.1, however version 20.1.1 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
Removing intermediate container c033b9e26a5d
 ---> bec6e6a023e9
Step 3/4 : CMD ["python","app.py"]
 ---> Running in fbc07ca5511e
Removing intermediate container fbc07ca5511e
 ---> 09a7a4f8ee05
Step 4/4 : COPY app.py /app.py
 ---> 9cd720f3b2e9
Successfully built 9cd720f3b2e9
Successfully tagged python-hello-world:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.

C:\Users\user06\Desktop\sample>
C:\Users\user06\Desktop\sample>docker images
REPOSITORY           TAG                 IMAGE ID            CREATED              SIZE
python-hello-world   latest              9cd720f3b2e9        About a minute ago   98.5MB
nginx                latest              4571e56e27f0        2 weeks ago          132MB
ubuntu               latest              1d622ef86b13        8 weeks ago          73.9MB
mongo                3.4                 f76f959b2a49        4 months ago         431MB
hello-world          2                   0470c9644f5b        10 months ago        76.1MB
hello-world          1                   457fe56f05c8        10 months ago        76.1MB
node                 9.4.0-alpine        b5f94997f35f        2 years ago          68MB
python               3.6.1-alpine        ddd6300d05a3        2 years ago          88.7MB

C:\Users\user06\Desktop\sample>docker run -p 5001:5000 -d python-hello-world
e0fe8529c9ca187cd20db497c54315202538afff2743ff541d9288fa2b14a18b

C:\Users\user06\Desktop\sample>docker container ls
CONTAINER ID        IMAGE                COMMAND             CREATED             STATUS              PORTS                    NAMES
e0fe8529c9ca        python-hello-world   "python app.py"     4 seconds ago       Up 4 seconds        0.0.0.0:5001->5000/tcp   elated_hawking
bed3eb2c7fdf        ubuntu               "top"               19 minutes ago      Up 19 minutes                                gracious_morse

C:\Users\user06\Desktop\sample>
```

### Kubernetes test

**Lab01**

```
Welcome to the IBM Cloud Kubernetes terminal, xxxxxx!
To get started, run ibmcloud ks

Note: Any files that you download and edit locally, such as YAML files,
      are stored temporarily in Kube Terminal and are not guaranteed to persist across sessions.

Note: To use the Kube Terminal for VPC clusters,
      enable a public gateway on each subnet or edit the KUBECONFIG file to use
      the private service endpoint. For more info, see 'https://ibm.biz/kube-terminal'.

xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ kubectl get pods
NAME                         READY   STATUS    RESTARTS   AGE
guestbook-59ff9b666c-4xps7   1/1     Running   0          2m23s
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ kubectl expose deployment guestbook --type="NodePort" --port=3001
Error from server (AlreadyExists): services "guestbook" already exists
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ kubectl expose deployment guestbook --type="NodePort" --port=3000
Error from server (AlreadyExists): services "guestbook" already exists
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ kubectl get service guestbook
NAME        TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
guestbook   NodePort   172.21.161.62   <none>        3000:30847/TCP   119s
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ ibmcloud cs workers osscluster

Plug-in 'container-service 1.0.99' is now available (you have 1.0.84).
Use 'ibmcloud plugin update container-service' to upgrade the plug-in.
Use 'ibmcloud config --check-version=false' to disable update check.

Kubernetes version 1.16 has removed deprecated APIs. For more information, see <http://ibm.biz/k8s-1-16-apis>

FAILED
Incorrect Usage. An argument was used without a flag: 'osscluster'. Each argument requires a flag. To see available flags, run 'ibmcloud ks workers --help'.

NAME:
        workers - List all worker nodes in a cluster.

USAGE:
        ibmcloud ks workers --cluster CLUSTER [--json] [-s] [--show-delete-reason] [--show-deleted] [--show-pools] [--worker-pool POOL]

PARAMETERS:
    --cluster value, -c value  Specify the cluster name or ID.
    --worker-pool value        Show only worker nodes that belong to the worker pool you specify.
    --show-pools               See the worker pool that each worker belongs to.
    --show-deleted             Show worker nodes that were deleted from the cluster.
    --show-delete-reason       Show the reason for worker node deletion.
    --json                     Prints the command output in JSON format.
    -s                         Do not show the message of the day or update reminders.

xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ kubectl get service
NAME         TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
guestbook    NodePort    172.21.161.62   <none>        3000:30847/TCP   4m15s
kubernetes   ClusterIP   172.21.0.1      <none>        443/TCP          16h
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ ibmcloud cs
NAME:
        ibmcloud ks - Manage IBM Cloud Kubernetes Service clusters.
USAGE:
        ibmcloud ks command [arguments...] [command options]

COMMANDS:

Cluster Management Commands:
    cluster       View and modify cluster and cluster service settings.
    worker        View and modify worker nodes for a cluster.
    worker-pool   View and modify worker pools for a cluster.
    zone          List availability zones and modify the zones attached to a worker pool.

Cluster Components Commands:
    alb              View and configure an Ingress application load balancer (ALB).
    logging          Forward logs from your cluster.
    nlb-dns          Create and manage host names for network load balancer (NLB) IP addresses in a cluster and health check monitors for host names.
    va               View a detailed vulnerability assessment report for a container that runs in a cluster.
    webhook-create   Register a webhook in a cluster.

Account Management Commands:
    api-key             View information about the API key for a cluster or reset it to a new key.
    credential          Set and unset credentials that allow you to access the IBM Cloud classic infrastructure portfolio through your IBM Cloud account.
    infra-permissions   View information about infrastructure permissions that allow you to access the IBM Cloud classic infrastructure portfolio through your IBM Cloud account.
    kms                 View and configure Key Management Service integrations.
    subnets             List available portable subnets in your IBM Cloud infrastructure account.
    vlan                List public and private VLANs for a zone and view the VLAN spanning status.
    vpcs                List all VPCs in the targeted resource group. If no resource group is targeted, then all VPCs in the account are listed.

Informational Commands:
    addon-versions   List supported versions for managed add-ons in IBM Cloud Kubernetes Service. To enable add-ons, use the 'ibmcloud ks cluster addon enable <addon>' command.
    flavors          List available flavors for a zone. Flavors determine how much virtual CPU, memory, and disk space is available to each worker node.
    messages         View the current user messages.
    versions         List all the container platform versions that are available for IBM Cloud Kubernetes Service clusters.

Configuration Commands:
    api    View or set the API endpoint and API version for the service.
    init   Initialize the Kubernetes Service plug-in and get authentication tokens.

Other Commands:
    locations   List supported IBM Cloud Kubernetes Service locations.
    script      Rewrite scripts that call IBM Cloud Kubernetes Service plug-in commands. Legacy-structured commands are replaced with beta-structured commands.

Enter 'ibmcloud ks help [command]' for more information about a command.
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ ibmcloud ks workers brloient0fmqqgoukcpg
FAILED
Incorrect Usage. An argument was used without a flag: 'brloient0fmqqgoukcpg'. Each argument requires a flag. To see available flags, run 'ibmcloud ks workers --help'.

NAME:
        workers - List all worker nodes in a cluster.

USAGE:
        ibmcloud ks workers --cluster CLUSTER [--json] [-s] [--show-delete-reason] [--show-deleted] [--show-pools] [--worker-pool POOL]

PARAMETERS:
    --cluster value, -c value  Specify the cluster name or ID.
    --worker-pool value        Show only worker nodes that belong to the worker pool you specify.
    --show-pools               See the worker pool that each worker belongs to.
    --show-deleted             Show worker nodes that were deleted from the cluster.
    --show-delete-reason       Show the reason for worker node deletion.
    --json                     Prints the command output in JSON format.
    -s                         Do not show the message of the day or update reminders.

xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ ibmcloud ks workers --cluster brloient0fmqqgoukcpg
OK
ID                                                   Public IP         Private IP      Flavor               State    Status   Zone    Version   
kube-brloient0fmqqgoukcpg-iksws02-default-00000164   161.202.254.162   10.129.80.225   b3c.4x16.encrypted   normal   Ready    tok02   1.17.6_1527   
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ ^C
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$
```

**Lab02**

```
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ kubectl scale --replicas=10 deployment guestbook
deployment.apps/guestbook scaled
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ kubectl rollout status deployment guestbook
deployment "guestbook" successfully rolled out
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ kubectl get pods
NAME                         READY   STATUS    RESTARTS   AGE
guestbook-59ff9b666c-4xps7   1/1     Running   0          13m
guestbook-59ff9b666c-5t69r   1/1     Running   0          105s
guestbook-59ff9b666c-bl5lh   1/1     Running   0          105s
guestbook-59ff9b666c-gg6q9   1/1     Running   0          105s
guestbook-59ff9b666c-gqgrj   1/1     Running   0          105s
guestbook-59ff9b666c-gvqhv   1/1     Running   0          105s
guestbook-59ff9b666c-hmmbb   1/1     Running   0          105s
guestbook-59ff9b666c-hzp9x   1/1     Running   0          105s
guestbook-59ff9b666c-m77qh   1/1     Running   0          105s
guestbook-59ff9b666c-sntrs   1/1     Running   0          105s
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ kubectl set image deployment/guestbook guestbook=ibmcom/guestbook:v2
deployment.apps/guestbook image updated
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ kubectl rollout status deployment/guestbook
deployment "guestbook" successfully rolled out
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ kubectl rollout status deployment/guestbook
deployment "guestbook" successfully rolled out
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ kubectl get pod
NAME                         READY   STATUS    RESTARTS   AGE
guestbook-55c86ccd98-4j4rw   1/1     Running   0          48s
guestbook-55c86ccd98-5h4ls   1/1     Running   0          48s
guestbook-55c86ccd98-6dd7c   1/1     Running   0          57s
guestbook-55c86ccd98-8xt5m   1/1     Running   0          57s
guestbook-55c86ccd98-c9pzc   1/1     Running   0          50s
guestbook-55c86ccd98-fv2xx   1/1     Running   0          57s
guestbook-55c86ccd98-rbgvm   1/1     Running   0          46s
guestbook-55c86ccd98-wl9bd   1/1     Running   0          47s
guestbook-55c86ccd98-wqfcr   1/1     Running   0          57s
guestbook-55c86ccd98-z24vv   1/1     Running   0          57s
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ kubectl rollout undo deployment guestbook
deployment.apps/guestbook rolled back
xxxxxx@k8s-terminal ~ (⎈ iksws02/brloient0fmqqgoukcpg:default)$ kubectl get replicasets -l run=guestbook
NAME                   DESIRED   CURRENT   READY   AGE
guestbook-55c86ccd98   0         0         0       3m7s
guestbook-59ff9b666c   10        10        10      19m
```

### 참고자료

-	[https://github.com/IBM](https://github.com/IBM)  
-	[https://github.com/IBM/docker101/blob/master/workshop/docker-101/lab-2.md](https://github.com/IBM/docker101/blob/master/workshop/docker-101/lab-2.md)  
-	[https://github.com/IBM/kube101](https://github.com/IBM/kube101)  
-	[https://github.com/IBM/docker101](https://github.com/IBM/docker101)

<div align="center">

<sub><sup>Written by <a href="https://github.com/LunightLab">@Lunight</a></sup></sub><small></small>

</div>
