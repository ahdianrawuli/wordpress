## Melakukan deployment wordpress

1. Membuat network cluster dengan perintah :
	docker network create wp_network --subnet 172.18.0.0/16
2. Up container ingress dengan menggunakan perintah docker-compose
	docker-compose -f ingress/docker-compose.yml up --build -d
3. Up container db dengan menggunakan perintah docker-compose
        docker-compose -f db/docker-compose.yml up --build -d
4. Up container wp dengan menggunakan perintah docker-compose
        docker-compose -f wp/docker-compose.yml up --build -d

## Melakukan scaling wordpress

1. Jika traffict semakin membesar, maka service "wp" dapat di scaleup dengan perintah
	docker-compose -f wp/docker-compose.yml scale wp=4

## notes

Deployment "ingress" saya pisahkan agar kedepannya service "wp" bisa di jadikan HA.
Untuk ingress sendiri hanyalah berfungsi sebagai loadbalancer. dan ingress ini seharus nya tidak boleh berada 1 server dengan frontend/backend

Terima Kasih
