## H4Z-flash

Sebuah wrapper script bash ringan untuk meng-compile dan meng-flash kode `.ino` ke board ESP8266 secara instan di Terminal Linux.

## Cara install.

Sebelum menginstal h4z-flash, kamu perlu menginstal dependensi utamanya di sistem kamu. Untuk pengguna Arch Linux, jalankan perintah ini:

```bash
sudo pacman -S arduino-cli esptool

Selanjutnya, kamu harus mengonfigurasi arduino-cli agar mengenali board ESP8266. Jalankan perintah ini satu per satu:
Bash

   arduino-cli config init
   arduino-cli config set board_manager.additional_urls [https://arduino.esp8266.com/stable/package_esp8266com_index.json](https://arduino.esp8266.com/stable/package_esp8266com_index.json)
   arduino-cli core update-index
   arduino-cli core install esp8266:esp8266
   
Untuk menginstal h4z-flash, clone repositori ini ke komputer kamu:
Bash

   git clone [https://github.com/h4znetwork/h4z-flash.git](https://github.com/h4znetwork/h4z-flash.git)

Masuk ke direktori yang baru saja diunduh:

   cd h4z-flash

Berikan izin eksekusi pada script:

   chmod +x h4z-flash

Pindahkan script ke direktori bin sistem agar bisa dijalankan dari folder mana saja:

   sudo mv h4z-flash /usr/local/bin/

   Catatan: Untuk menghindari error permission saat mengirim data ke port USB serial di Linux, tambahkan user kamu ke dalam grup uucp. Kamu harus log out dan log in kembali (atau restart) agar efeknya berjalan:
   sudo usermod -aG uucp $USER

## Cara pakai.
Untuk melakukan flash kode kamu, buka terminal di dalam folder tempat file .ino kamu berada. Pastikan file .ino tersebut memiliki nama yang sama persis dengan nama foldernya.

Untuk menjalankan h4z-flash menggunakan port serial default (/dev/ttyUSB0), gunakan perintah ini (dengan asumsi "servo_wifi.ino" adalah copy dari file kode kamu):

   h4z-flash servo_wifi.ino

Atau, jika kamu ingin menggunakan port serial spesifik tempat ESP8266 kamu terhubung, tambahkan path port di akhir perintah:

   h4z-flash servo_wifi.ino /dev/ttyUSB1
