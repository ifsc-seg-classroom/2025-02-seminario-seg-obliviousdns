# Passo 1: 

Baixar repo 

docker compose up --build -d

# Passo 2:

docker compose exec client bash

dig google.com

# Passo 3:

DOH_PROXY_IP=$(getent hosts doh-proxy | awk '{ print $1 ; exit }')


echo "IP do DoH Proxy: $DOH_PROXY_IP"

dig @$DOH_PROXY_IP google.com


# passo 4:
cat /etc/resolv.conf 

echo "nameserver 172.23.0.3" > /etc/resolv.conf 

cat /etc/resolv.conf 

cp /app/odoh-client-build/odoh-client-ready /usr/local/bin/odoh-client

chmod +x /usr/local/bin/odoh-client

odoh-client odoh --domain www.google.com --dnstype AAAA --target odoh.cloudflare-dns.com

# Extra
Caso necessário ( não conseguir alterar o nameserver de resolve.conf) 

comando para verificar ipv4 de doh_proxy_lab (padrao 172.23.0.2)

docker network inspect odoh-lab_lab_net

Alterar o ip no arquivo resolv.conf da pasta raiz

descomentar a linha no dockercompose


# QUERY DO WIRESHARK 
(ip.addr == 191.36.15.17 and ip.dst == 191.36.15.17)  or ip.src == 191.36.15.17
## alterar para o IP do seu computador