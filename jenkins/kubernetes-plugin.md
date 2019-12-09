### generate credentials
#### ca.crt
```bash
$ grep certificate-authority-data ~/.kube/config | awk -F': ' '{print $NF}' |  base64 -d > ca.crt
# OR
$ sudo cat /etc/kubernetes/pki/ca.crt
```

#### client.crt & client.key
```bash
$ grep client-certificate-data ~/.kube/config | awk -F': ' '{print $NF}' |  base64 -d > client.crt
$ grep client-key-data ~/.kube/config | awk -F': ' '{print $NF}' |  base64 -d > client.key
```

#### cert.pfx
```bash
$ openssl pkcs12 -export -out cert.pfx -inkey client.key -in client.crt -certfile ca.crt
Enter Export Password:
Verifying - Enter Export Password:

$ ls
ca.crt  cert.pfx  client.crt  client.key
```

### configure in jenkins
* Go to `Manage Jenkins` -> `Configure System` or `Manage Jenkins` -> `Manage Nodes and Clouds` -> `Configure Clouds`
* `Add a new Cloud` -> `Kuberentes`
    * `Name`: <Anything you want>
    * `Kubernetes URL`:
        * get from `$ kubectl cluster-info`
        * using `https://kubernetes.default.svc.cluster.local`
    * `Kubernetes server certificate key`: content of `ca.crt`. (`$ cat ca.crt`)
    * `Credentials`:
        * `Add` -> `Jenkins`
        * **Kind**: `Certificate`
![plugin-1](../screenshot/k8s-plugin-1.png)
![plugin-2](../screenshot/k8s-plugin-2.png)
![plugin-3](../screenshot/k8s-plugin-3.png)
![plugin-4](../screenshot/k8s-plugin-4.png)
    * Setup in Jenkins
![plugin-5](../screenshot/k8s-plugin-5.png)
