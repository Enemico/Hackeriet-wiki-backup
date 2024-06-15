Example wg.conf

```
[Interface]
# Bytt ut XXX i Address med dine IPv4 og IPv6 adresser som du har fått
Address = 10.10.235.XXX/32, 2a02:ed06:235::XXX/128

# Bytt ut PrivateKey med in private nøkkel som du har generert
PrivateKey = a1a1a1a1a1a1a1a1a1a1

# Optional
# DNS = 1.1.1.1

[Peer]
# Bytt ut PresharedKey med den du har fått, er unik per connection 
PresharedKey = 4c4b4c4b4c4b4c4b4c4b

# IP ranges som skal rutes over tunellen
AllowedIPs = 0.0.0.0/0, ::/0 

# Denne peker mot pizza.hackeriet.no, og identifiseres med public key
PublicKey = z8//zcFn8o9MWhC0J+tuHD6aYbN9yZOKWxqwI9uB7WI=
Endpoint = 185.35.202.235:443

# Optional
# PersistentKeepalive = 25

```