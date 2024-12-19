### How to Run
```
cargo run

Hit the endpoint localhost:7979/ in your browser or using curl.
Hit the endpoint localhost:7979/sleep in your browser or using curl.
```


### Flow
```
Main Thread
   ├── Buat ThreadPool
   ├── Kirim job via `sender`
Worker Threads
   ├── Loop: `recv()` untuk menunggu job
   ├── Jika job diterima:
   │      ├── Cetak "Worker {id} got a job; executing."
   │      ├── Eksekusi closure
   └── Jika `recv()` gagal:
          ├── Cetak "Worker {id} disconnected; shutting down."
          └── Keluar dari loop
```