# AMQP & Connection String Explanation

## a. What is AMQP?

AMQP adalah singkatan dari Advanced Message Queuing Protocol. Ini adalah protokol application layer berstandar terbuka yang dirancang khusus untuk message-oriented middleware (perangkat lunak perantara berbasis pesan).

AMQP memungkinkan berbagai sistem untuk berkomunikasi dengan mengirimkan pesan melalui sebuah message broker (seperti RabbitMQ). Alih-alih layanan (services) saling berbicara langsung satu sama lain, mereka mengirimkan pesan ke broker. Broker inilah yang kemudian bertugas mengarahkan (routing) dan mengirimkan pesan tersebut ke penerima (consumers) yang tepat.

**Kasus Penggunaan Umum:**
- Memisahkan ketergantungan antar layanan (decoupling microservices).
- Antrean tugas/pekerjaan (task/job queues untuk pemrosesan background).
- Arsitektur berbasis event (event-driven architectures).
- Streaming data secara real-time.

---

## b. What does `guest:guest@localhost:5672` mean?

Ini adalah sebuah connection string yang digunakan untuk menyambungkan aplikasi ke broker AMQP (contohnya, RabbitMQ). Mari kita bedah bagian-bagiannya:

```
amqp://guest:guest@localhost:5672
```

| Part        | Value       | Meaning                                                                 |
|-------------|-------------|-------------------------------------------------------------------------|
| **1st guest** | `guest`   | **username** yang digunakan untuk autentikasi dengan *message* broker         |
| **2nd guest** | `guest`   | **password** untuk username tersebut                                      |
| **localhost** | `localhost` | **host/address** dari broker, localhost berarti broker tersebut berjalan di mesin atau komputer sendiri |
| **5672**      | `5672`    | **nomor port** — ini adalah port bawaan (default) yang didengarkan oleh RabbitMQ (dan AMQP) untuk menerima koneksi masuk |

> **Catatan:** `guest:guest` adalah **default credential** di RabbitMQ. Hanya bekerja pada `localhost` secara default karena alasan keamanan. Di lingkungan *production*, harus mengganti kredensial ini.

---