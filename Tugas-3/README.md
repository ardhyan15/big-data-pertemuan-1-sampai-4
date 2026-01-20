
# Tugas 3

## Apache Flume
1. Download dan ekstrak apache flume
2. Masuk ke direktori `conf` dan buat file konfigurasi `netcat-logger.conf`
<img width="424" height="399" alt="Screenshot 2026-01-20 175137" src="https://github.com/user-attachments/assets/a5cbc9d1-0048-4daf-872c-57392d101fdb" />

3. Jalankan dengan terminal `./bin/flume-ng agent --conf conf --conf-file conf/netcat-logger.conf --name a1 -Dflume.root.logger=INFO,console`
4. Buka terminal kedua dan lakukan `telnet localhost 44444`
<img width="484" height="193" alt="Screenshot 2026-01-20 172018" src="https://github.com/user-attachments/assets/ca913537-e896-49d2-a44c-99cfa7ef6b92" />

5. Kirim pesan seperti "Hello Flume", jika berhasil akan ada output "OK"
6. Amati log di terminal pertama seharusnya akan muncul log seperti : <br>
12/01/26 15:32:19 INFO source.NetcatSource: Source starting <br>
12/01/26 15:32:19 INFO source.NetcatSource: Created serverSocket:sun.nio.ch.ServerSocketChannelImpl[/127.0.0.1:44444]<br>
12/01/26 15:32:34 INFO sink.LoggerSink: Event: { headers:{} body: 48 65 6C 6C 6F 20 77 6F 72 6C 64 21 0D          Hello Flume. }
