### kubectl alias
#### `__start_kubectl`
```bash
echo 'source <(kubectl completion bash)' >> ~/.bashrc
cat >> ~/.bashrc <<EOF
alias k='kubectl'
alias kc='kubectl -n kube-system'
alias ki='kubectl -n ingress-ngxin'
alias kk='kubectl -n kubernetes-dashboard'

for _i in k kc ki kk; do
  complete -F __start_kubectl "${_i}"
done
EOF
source ~/.bashrc
```

#### `_complete_alias`
```bash
# download bash_completion.sh for kubectl
$ curl -fsSL https://raw.githubusercontent.com/cykerway/complete-alias/master/bash_completion.sh > ~/.bash_completion.sh
$ chmod +x !$

$ cat >> ~/.bashrc << EOF
source <(kubectl completion bash)
source ~/.bash_completion.sh

alias k='kubectl'
alias kc='kubectl -n kube-system'
alias ki='kubectl -n ingress-ngxin'
alias kk='kubectl -n kubernetes-dashboard'

while read -r _i; do
  complete -F _complete_alias "${_i}"
done < <(sed '/^alias /!d;s/^alias //;s/=.*$//' '~/.bashrc')
EOF
source ~/.bashrc
```
### update image for deploy
```bash
$ k -n devops set image deployments/devops-jenkins devops-jenkins=jenkins/jenkins:2.200
deployment.extensions/devops-jenkins image updated
```
- result
```bash
$ k -n devops get pods -w
NAME                              READY   STATUS    RESTARTS   AGE
devops-jenkins-54d6db68ff-bz5b6   1/1     Running   0          6d17h
devops-jenkins-6bdd4fc6dd-l9spp   0/1     Pending   0          0s
devops-jenkins-6bdd4fc6dd-l9spp   0/1     Pending   0          0s
devops-jenkins-6bdd4fc6dd-l9spp   0/1     ContainerCreating   0          0s
devops-jenkins-6bdd4fc6dd-l9spp   1/1     Running             0          8s
devops-jenkins-54d6db68ff-bz5b6   1/1     Terminating         0          6d17h
devops-jenkins-54d6db68ff-bz5b6   0/1     Terminating         0          6d17h
devops-jenkins-54d6db68ff-bz5b6   0/1     Terminating         0          6d17h
devops-jenkins-54d6db68ff-bz5b6   0/1     Terminating         0          6d17h

$ k -n devops get deploy -w
NAME             READY   UP-TO-DATE   AVAILABLE   AGE
devops-jenkins   1/1     1            1           22d
devops-jenkins   1/1     1            1           22d
devops-jenkins   1/1     1            1           22d
devops-jenkins   1/1     0            1           22d
devops-jenkins   1/1     1            1           22d
devops-jenkins   2/1     1            2           22d
devops-jenkins   1/1     1            1           22d

$ k -n devops get deploy devops-jenkins -o yaml --export | grep image\:
Flag --export has been deprecated, This flag is deprecated and will be removed in future.
        image: jenkins/jenkins:2.200
```

### duplicate secrets to the other ns
```bash
$ k -n ingress-nginx get secrets my-certs -o yaml --export | k apply -n devops -f -
```
- [others](https://github.com/jetstack/cert-manager/issues/494)
- [Pro-Tip – Copying Kubernetes Secrets Between Namespaces](https://www.revsys.com/tidbits/copying-kubernetes-secrets-between-namespaces/)
