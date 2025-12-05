I tested everything with docker network + docker volume.
It works with:

1.
sudo docker network create kittygram
sudo docker volume create kg_data

2.
Change nginx.conf frontend to:
```
location / {
	proxy_set_header Host $http_host;
	proxy_pass http://frontend:8000/;
}
```

3.
sudo docker run --name db 	--net kittygram --env-file .env -v kg_data:/var/lib/postgresql/data/ -d postgres:13.10
sudo docker run --name backend 	--net kittygram --env-file .env -d kittygram_backend
sudo docker run --name frontend --net kittygram -d kittygram_frontend
sudo docker run --name gateway 	--net kittygram -p 0.0.0.0:8000:80 -d kittygram_gateway

