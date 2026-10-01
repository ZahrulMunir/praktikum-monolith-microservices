# Praktikum Monolith dan Microservices

Praktikum Arsitektur Monolith dan Microservices menggunakan Python Flask.

## 1. Clone Repository

```bash
git clone https://github.com/ZahrulMunir/praktikum-monolith-microservices.git
```
Masuk ke folder project:

cd praktikum-monolith-microservices
2. Install Library

Install Flask dan Requests:

pip install Flask requests
3. Menjalankan Monolith

Masuk ke folder Monolith:

cd Monolight

Jalankan program:

python monolith_app.py

Program berjalan pada:

http://localhost:5000
Cek data buku

Buka terminal baru, kemudian masuk ke folder project:

cd praktikum-monolith-microservices

Jalankan:

curl.exe http://localhost:5000/books
Membuat order
curl.exe -X POST -H "Content-Type: application/json" -d '{\"book_id\":1}' http://localhost:5000/orders

Jika berhasil, akan mendapatkan hasil seperti:

{
  "book_id": 1,
  "id": 1,
  "status": "berhasil"
}

4. Menjalankan Microservices

Microservices terdiri dari:

Book Service
Order Service

4.1 Menjalankan Book Service

Dari folder utama project:

cd Microservice

Jalankan:

python book_service.py

Book Service berjalan pada:

http://localhost:5001
Cek Book Service

Buka terminal baru:

cd praktikum-monolith-microservices/Microservice

Kemudian:

curl.exe http://localhost:5001/books

Untuk mengecek buku berdasarkan ID:

curl.exe http://localhost:5001/books/1

4.2 Menjalankan Order Service

Buka terminal baru.

Masuk ke folder Microservice:

cd praktikum-monolith-microservices/Microservice

Jalankan:

python order_service.py

Order Service berjalan pada:

http://localhost:5002
Membuat Order

Buka terminal baru:

cd praktikum-monolith-microservices/Microservice

Kemudian:

curl.exe -X POST -H "Content-Type: application/json" -d '{\"book_id\":1}' http://localhost:5002/orders

Jika berhasil:

{
  "book_id": 1,
  "id": 1,
  "status": "berhasil"
}
5. Pengujian Fault Isolation

Pastikan Book Service dan Order Service sedang berjalan.

Kemudian matikan Book Service dengan:

Ctrl + C

Jangan matikan Order Service.

Kemudian jalankan:

curl.exe -X POST -H "Content-Type: application/json" -d '{\"book_id\":1}' http://localhost:5002/orders

Hasil:

{
  "error": "Book Service sedang down!"
}

Hal ini menunjukkan bahwa Order Service tetap berjalan ketika Book Service dihentikan.
