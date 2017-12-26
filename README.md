# DockerComposePhp
Dibuat untuk memenuhi Tugas Teori TCC yaitu run file PHP di Docker Compose
Nama: Thomas Prayudhi | NIM : 155410041
untuk tutorial lengkapnya bisa dilihat di file dengan nama tutorial.docx
TUTORIAL
1. Pertama install docker compose terlebih dahulu yaitu buka terminal dan mengetikkan apt-get install docker compose tunggu hingga proses intall selesai
2. Setelah itu membuat folder untuk menampung file-file yang diperlukan untuk docker compose, nama dan letaknya bebas. Sebagai contoh saya menggunakan nama folder Docker di Download
3. Selanjutnya membuat beberapa file yaitu index.php, docker-compose.yml dan site.conf untuk isi dari masing-masing file bisa dilihat di gambar atau di tutorial.docx
4. Buka terminal dan masuk ke folder docker yang sudah kita buat tadi dengan mengetikkan cd Downloads/Docker
5. Selanjutnya untuk up docker composenya maka dapat mengetikkan perintah docker-compose up -d dan tunggu sampai proses selesai
6. Untuk mengetahui images apa saya yang sudah kita buat maka bisa dengan mengetikkan docker images
7. Sebelum melihat di browser file phpnya, kita harus mengetahui ip docker maka dapat dengan mengetikkan ifconfig maka akan terlihat ip dockernya yaitu 172.17.0.1
8. Langkah terkahir membuka browser dan mengetikkan ip docker dan portnya tadi kita membuat port 8080 maka kita ketikkan dialamat broeser kita 172.17.0.1:8080 dan enter maka akan terlihat file php yang sudah dibuat tadi             
