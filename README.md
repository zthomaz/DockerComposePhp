# DockerComposePhp
Dibuat untuk memenuhi Tugas Teori TCC yaitu run file PHP di Docker Compose
Nama: Thomas Prayudhi | NIM : 155410041
untuk tutorial lengkapnya bisa dilihat di file dengan nama tutorial.docx
TUTORIAL
1. Pertama install docker compose terlebih dahulu yaitu buka terminal dan mengetikkan apt-get install docker compose tunggu hingga proses intall selesai
2. Setelah itu membuat folder untuk menampung file-file yang diperlukan untuk docker compose, nama dan letaknya bebas. Sebagai contoh saya menggunakan nama folder Docker di Download
3. Selanjutnya membuat beberapa file yaitu index.php yang akan di run didocker compose dengan isian dibawah ini hilangkan tanda //
            <?php
            echo "<b>";
//            echo "<center><h1>Tugas Teori TCC 12 - Docker Compose</h1></center>";
            echo "<br>";
            echo "<h3>Nama 		: Thomas Prayudhi Triutomo<br>";
            echo "NIM 			: 155410041<br>";
            echo "Jurusan 		: Teknik Informatika<br>";
            echo "Github		: github.com/zthomaz</h3>";
            echo "</b>";
            ?>
  file dengan nama docker-compose.yml yang didalamnya terdapat macam service images dan port yang akan kita build yang isinya sebagai berikut:
            version: '2'
            services:
                web:
                    image: nginx:latest
                    ports:
                        - "8080:80"
                    volumes:
                        - ./index:/index
                        - ./site.conf:/etc/nginx/conf.d/default.conf
                    networks:
                        - index-network
                php:
                    image: php:fpm
                    volumes:
                        - ./index:/index
                    networks:
                        - index-network
            networks:
                index-network:
                    driver: bridge
  
  file dengan nama site.conf yang berisikan file yang akan kita up nantinya dengan isian
            server {
              listen 80;
              index index.php index.html;
              server_name localhost;
              error_log  /var/log/nginx/error.log;
              access_log /var/log/nginx/access.log;
              root /index;

              location ~ \.php$ {
                  try_files $uri =404;
                  fastcgi_split_path_info ^(.+\.php)(/.+)$;
                  fastcgi_pass php:9000;
                  fastcgi_index index.php;
                  include fastcgi_params;
                  fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
                  fastcgi_param PATH_INFO $fastcgi_path_info;
              }
          }
4. Buka terminal dan masuk ke folder docker yang sudah kita buat tadi dengan mengetikkan cd Downloads/Docker
5. Selanjutnya untuk up docker composenya maka dapat mengetikkan perintah docker-compose up -d dan tunggu sampai proses selesai
6. Untuk mengetahui images apa saya yang sudah kita buat maka bisa dengan mengetikkan docker images
7. Sebelum melihat di browser file phpnya, kita harus mengetahui ip docker maka dapat dengan mengetikkan ifconfig maka akan terlihat ip dockernya yaitu 172.17.0.1
8. Langkah terkahir membuka browser dan mengetikkan ip docker dan portnya tadi kita membuat port 8080 maka kita ketikkan dialamat broeser kita 172.17.0.1:8080 dan enter maka akan terlihat file php yang sudah dibuat tadi             
