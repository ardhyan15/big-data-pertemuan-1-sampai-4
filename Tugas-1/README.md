# TUGAS 1
## Installasi HDFS
Untuk melakukan installasi HDFS pertama download semua program yang dibutuhkan:
- Apache Hadoop
- WSl (jika di windows)
- SSH

### Langkah-langkah
1. Download dan Ekstrak File Hadoop ke WSL
2. Format NameNode untuk pertama kali dengan `hdfs namenode -format`
3. Jalankan HDFS dengan `start-dfs.sh`
<img width="1210" height="584" alt="Screenshot 2026-01-20 172257" src="https://github.com/user-attachments/assets/a3cf18da-83ad-404c-8ad3-e2a29f6449b9" />

4. Jalankan yarn dengan `start-yarn.sh`
![yarn localhost:8088](yarn.sh-png)
5. Cek status dengan `jps` atau `hdfs dfsadmin -report`
<img width="1210" height="612" alt="Screenshot 2026-01-20 172324" src="https://github.com/user-attachments/assets/87c07450-1a7f-4236-ac8f-3297a2af68c8" />

6. Buat script agar command bisa dipakai di direktori apapun <sup>*opsional*</sup>
<img width="1207" height="606" alt="Screenshot 2026-01-20 172343" src="https://github.com/user-attachments/assets/3a1f3dea-1a78-49e4-8a9a-0df548643022" />


### Test HDFS
1. jalankan hdfs `start-dfs.sh`
2. buat direktori pada namenode `hdfs dfs -mkdir /praktikum`
3. taruh file kedalam hdfs `hdfs dfs -put *nama file* /praktikum`
4. tampilkan isi file dengan `hdfs dfs -cat *nama file* /praktikum`
<img width="1212" height="614" alt="Screenshot 2026-01-20 172424" src="https://github.com/user-attachments/assets/a8a3c811-e241-44b6-a979-ec074b2cf279" />

