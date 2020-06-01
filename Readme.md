# Cài đặt trên ubuntu

## Docker

```bash
$ sudo apt-get update

$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

$ sudo apt-key fingerprint 0EBFCD88

$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

$ sudo apt-get update

$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

##### Run docker không cần sudo

```bash
$ sudo usermod -aG docker $USER

$ sudo reboot
```

##### Kiểm tra cài đặt

```bash
$ docker -v
Docker version 19.03.8, build afacb8b7f0
```

## Docker Compose

```bash
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

$ sudo chmod +x /usr/local/bin/docker-compose

$ sudo reboot
```

##### Kiểm tra cài đặt 

```bash
$ docker-compose --version
docker-compose version 1.25.5, build 1110ad01
```

## Elasticsearch + Kibana

```bash
$ git clone git@github.com:hoangnv-1477/es-learning.git

$ cd es-learning

$ docker-compose up
```
Đợi một chút cho nó chạy xong nhé :D

##### Kiểm tra cài đặt elasticsearch

```bash
$ curl -X GET "localhost:9300"

{
  "name" : "es",
  "cluster_name" : "es-learning-cluster",
  "cluster_uuid" : "30XumD80QqqEVFP9Lkr_Mw",
  "version" : {
    "number" : "7.7.0",
    "build_flavor" : "default",
    "build_type" : "docker",
    "build_hash" : "81a1e9eda8e6183f5237786246f6dced26a10eaf",
    "build_date" : "2020-05-12T02:01:37.602180Z",
    "build_snapshot" : false,
    "lucene_version" : "8.5.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "You Know, for Search"
}
```
##### Kiểm tra cài đặt kibana

```bash
# Bật trình duyệt web gõ http://localhost:5601/ ra giao diện kibana là ok
```
##### Tắt service elasticsearch + kibana

```bash
$ docker-compose down
```