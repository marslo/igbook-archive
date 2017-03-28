## Content
- [Port Redirection](#port-redirection)
- [Proxy Setup](#proxy-setup)

# Port Redirection

    # iptables -L -n
    Chain INPUT (policy ACCEPT)
    target     prot opt source               destination
    Chain FORWARD (policy ACCEPT)
    target     prot opt source               destination
    Chain OUTPUT (policy ACCEPT)
    target     prot opt source               destination

    # iptables -I INPUT 1 -p tcp --dport 8080 -j ACCEPT
    # iptables -I INPUT 1 -p tcp --dport 80 -j ACCEPT
    # iptables -A PREROUTING -t nat -i ens32 -p tcp --dport 80 -j REDIRECT --to-port 8080
    # iptables -t nat -I OUTPUT -p tcp -d 127.0.0.1 --dport 80 -j REDIRECT --to-ports 8080
    # iptables -t nat -I OUTPUT -p tcp -o lo --dport 80 -j REDIRECT --to-ports 8080

    # iptables -L -n
    Chain INPUT (policy ACCEPT)
    target     prot opt source               destination
    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:80
    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:8080
    Chain FORWARD (policy ACCEPT)
    target     prot opt source               destination
    Chain OUTPUT (policy ACCEPT)
    target     prot opt source               destination

    # netfilter-persistent save
    run-parts: executing /usr/share/netfilter-persistent/plugins.d/15-ip4tables save
    run-parts: executing /usr/share/netfilter-persistent/plugins.d/25-ip6tables save
    # iptables-save > /etc/iptables/rules.v4

# Proxy Setup
* Name: `x.x.x.x`
* Port: `80`
* Settings

        $ grep proxy /etc/profile
        export http_proxy=x.x.x.x:80
        export https_proxy=x.x.x.x:80
        export no_proxy=localhost,127.0.0.1,*.google.com
