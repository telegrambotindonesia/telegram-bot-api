## Telegram-bot-api

Hasil build dari [telegram-bot-api](https://github.com/tdlib/telegram-bot-api).

Informasi tentang ini ada di [https://core.telegram.org/bots/api#using-a-local-bot-api-server](https://core.telegram.org/bots/api#using-a-local-bot-api-server)

## Kelebihan

- **Tidak ada perubahan coding** pada bot API (tidak seperti bot MTProto)
- **Download file tanpa batas limit** (normal dibatasi hanya max 20 MB)
- **Upload file hingga 2000 MB** (normal dibatas max 50MB)
- Upload file menggunakan path dan skema URI file lokal.
- Bisa menggunakan URL **HTTP** untuk webhook (normal harus HTTPS).
- Bebas menggunakan alamat `IP local` pada webhook.
- Bebas menggunakan port pada webhook.
- Set `max_webhook_connections` hingga 100.000.
- **Download berupa file asli yang langsung ke path lokal** (normal harus  mendownload ulang melalui request `getFile`).

## Penggunaan

Untuk menggunakan, kamu butuh `--api-id` dan `--api-hash` yang bisa didapatkan di [my.telegram.org](https://my.telegram.org)

Detail penggunaan bisa dilihat dengan command: `telegram-bot-api --help`

Untuk mendapatkan semua kelebihan fitur diatas, saat dijalankan **HARUS** di set mode lokal dengan penambahan parameter: `--local`

Secara default dijalankan pada mode `--http-port` port `8081`

### Contoh

Pada Linux:

```bash
./telegram-bot-api --api-id=ID --api-hash=HASH --local \
    --max-webhook-connections=100 \
    -d ~/mybot/ -p 3344 --http-stat-ip-address=192.168.0.100 \
    -s 3355 -v 3 -c 1000
```

Maksudnya:

- menjalankan telegram-bot-api dengan api_id dan api_hash sesuai parameter
- dijalankan pada mode lokal
- set port untuk webhook adalah `3344`
- max set koneksi webhook per bot adalah `100`
- dijalankan pada direktori kerja `~/mybot`
- statistik hanya dapat diakses pada lokal IP `192.168.0.100` pada port `3355`
- mode verbose level 3
- jumlah koneksi aktif semua bot dibatasi `1.000`

### Set Bot API

Bot perlu di logout dengan menggunakan method [logOut](https://core.telegram.org/bots/api#logout):

    https://api.telegram.org/botTOKEN/logOut

Setelah itu baru bisa di set ke local (misalnya IP local adalah 192.168.0.100):

    https://api.telegram.org/botTOKEN/setwebhook?url=http://192.168.0.100:3344

Bot sudah bisa berjalan dengan semestinya.    

### Dependencies

Untuk menjalankan:

- OpenSSL
- zlib

Linux (Ubuntu): `sudo apt install zlib1g-dev libssl-dev`

### Kontribusi

- Silakan build sesuai petunjuk caranya [https://tdlib.github.io/telegram-bot-api/build.html](https://tdlib.github.io/telegram-bot-api/build.html).
- Buat fork
- Bikin folder sesuai OS dan tanggal build
- Beri file `readme.md` untuk menjelaskan

Sesuai contoh folder hasil build ya.

## Mirror

- [Github](https://github.com/telegrambotindonesia/telegram-bot-api)
- [Gitlab](https://gitlab.com/botindonesia/telegram-bot-api)