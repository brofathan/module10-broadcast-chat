# Refleksi

- Screenshot for 2.1
![image](https://github.com/brofathan/grpc-tutorial/assets/45114836/3ab4fa7a-1f3e-4dc4-8f67-c315074c7092)
Satu server dijalankan beserta ada tiga client yang terhubung ke server. Saat salah satu client mengirimkan message, message nya masuk di client lain dan di server tertera dengan client ip nya dan port nya yang berbeda-beda tiap client.

<br>

- 2.2 Modifying the websocket port
Selain mengganti port pada client.rs menjadi 8080, harus juga mengganti port pada server.rs di tcp listener pada method bind. Hal ini dilakukan agar program server.rs terhubung ke port websocket yang sama dengan client.rs. Jika misalnya client masih terhubung ke websocket pada port 2000 namun server ke port 8080, maka akan terjadi error karena client dan server tidak terhubung.

<br>

- Screenshot for 2.3
![image](https://github.com/brofathan/grpc-tutorial/assets/45114836/35ca237e-a97f-45e9-8fc8-162b2353513a)
Dengan mengubah sedikit pada kode di server.rs, maka sekarang client-client dapat melihat message dan address dari client yang berbeda. Untuk spesifik pengubahannya yaitu pada method send di bcast, dimana bcast bukan hanya mengirimkan text yang masuk dari client, tetapi juga mengirimkan address dari client tersebut `bcast_tx.send(format!("{addr} : {text}"))?;`
