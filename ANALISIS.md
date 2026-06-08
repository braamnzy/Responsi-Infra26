# Analisis Perbaikan

## Permasalahan 1

### Gejala
yaml: line 5, column 8: mapping values are not allowed in this context

### Penyebab
Kesalahan sintaks dan environment pada docker-compose.yml
    1. kurang tanda titik pada services
    2. db_host pada web1 tidak sesuai
    3. db_pass pada web2 tidak sesuai
    4. buildcontext pada web3 penulisan salah
    5. network pada web3 tidak akses frontend


### Solusi
Jelaskan langkah perbaikan yang dilakukan.
    1. tambahkan titik pada services
    2. ubah db_host menjadi db
    3. ubah db_pass menjadi student123
    4. ubah .web/33 menjadi ./web3
    5. tambahkan frontend pada networks web3

---

## Permasalahan 2

### Gejala
service "db" refers to undefined volume db-data: invalid compose project

### Penyebab
db.volumes tidak sinkron

### Solusi
ubah dari db-data menjadi database-data pada db.volumes

---

## Permasalahan 3

### Gejala
level=warning msg="... the attribute 'version' is obsolete, it will be ignored, please remove it to avoid potential confusion"

### Penyebab
penulisan version: "3.9" di baris paling atas sudah tidak diperlukan lagi (deprecated)

### Solusi
Hapus baris version: "3.9"


---

## Permasalahan 4

### Gejala
target web1: failed to solve: php:8.2-apach: not found

### Penyebab
Kesalahan penulisan nama base image pada file Dockerfile di dalam folder web1

### Solusi
Buka file ./web1/Dockerfile ubah menjadi FROM php:8.2-apache

---

## Permasalahan 5

### Gejala
target web3: failed to solve: php:8.2-apche: not found

### Penyebab
Kesalahan penulisan nama base image pada file Dockerfile di dalam folder web3

### Solusi
Buka file ./web3/Dockerfile ubah menjadi FROM php:8.2-apache

---

## Permasalahan 6

### Gejala
Browser menampilkan pesan This site can’t be reached - localhost refused to connect saat membuka http://localhost:8080.

### Penyebab
Kesalahan sintaks pada Nginx
1. server web11:80
2. server web3:8080

### Solusi
Buka file ./nginx/nginx.conf
1. ubah web11 menjadi web1
2. ubah web3:8080 menjadi web3:80

---

## Permasalahan 7

### Gejala
Kontainer nginx-lb berstatus Exited.

### Penyebab
Kesalahan sintaks pada nginx.conf
```nginx ```

### Solusi
Buka file ./nginx/nginx.conf
hapus ```nginx dan ``` pada awal dan akhir file