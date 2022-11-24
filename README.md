# Tutorial Chainflip Testnet

<p style="font-size:14px" align="right">
<a href="https://t.me/bangpateng_group" target="_blank">Join Telegram Bang Pateng<img src="https://user-images.githubusercontent.com/50621007/183283867-56b4d69f-bc6e-4939-b00a-72aa019d1aea.png" width="30"/></a>
</p>

<p align="center">
  <img height="auto" width="auto" src="https://user-images.githubusercontent.com/38981255/203701217-2dc774a1-eca7-4a6e-a7ee-bbe5b02882b4.JPG">
</p>

## Referensi

[Dokumen resmi](https://docs.chainflip.io/perseverance-validator-documentation/)

[Validator auction](https://stake-perseverance.chainflip.io/auctions)

[Server Discord Chainflip](https://discord.gg/cm2z9V6b)

[Vanity ETH](https://vanity-eth.tk/)

[Goerli faucet](https://goerlifaucet.com)

[Goerli RPC](https://alchemy.com/?r=b2360e83006e718e)

## Persyaratan hardware & software

### Persyaratan hardware

| Komponen | Spesifikasi minimal |
|----------|---------------------|
|CPU|4 Cores|
|RAM|32 GB DDR4 RAM|
|Penyimpanan|1 TB HDD|
|Koneksi|10Mbit/s port|

| Komponen | Spesifikasi rekomendasi |
|----------|---------------------|
|CPU|32 Cores|
|RAM|32 GB DDR4 RAM|
|Penyimpanan|2 x 1 TB NVMe SSD|
|Koneksi|1 Gbit/s port|

### Persyaratan software/OS

| Komponen | Spesifikasi minimal |
|----------|---------------------|
|Sistem Operasi|Ubuntu 16.04|

| Komponen | Spesifikasi rekomendasi |
|----------|---------------------|
|Sistem Operasi|Ubuntu 20.04|

## Create ETH Address dan Claim Faucet Goerly 

- Buat Wallet ETH Baru di : https://vanity-eth.tk/
- Generate > Backup Address dan Private Key
- Done Simpan Bae Bae
- Claim Faucet di : https://goerlifaucet.com/
- Paste Address ETH Kalian dan Done


## Create Goerli RPC

Anda memerlukan Goerli RPC untuk menjalankan node, Anda bisa membuatnya di : [https://alchemy.com/](https://alchemy.com/?r=b2360e83006e718e "https://alchemy.com/")

- Registrasi di alchemy
- Pilih `CREATE APP`
- Isi `Name` dan `Description`
- Di bagian `CHAIN` ganti `CHAIN` menjadi `GOERLI`
- Klik CREATE APP
- Setelah itu cari App yang anda buat tadi
- Pilih `VIEW DETAILS`
- Pilih `VIEW KEY`
- Salin `HTTPS` dan `Websocket`
- Simpan Dulu Amankan

## Claim tFlip Token di Discord

tFlip Token dibutuhkan untuk delegasi dan memenangkan slot validator. Jika anda mendapatkan slot validator, maka validator anda akan dimasukan active list

Minimal stake untuk mendapatkan slot validator akan berubah setiap saat, anda bisa mengecek minimal stake di : https://stake-perseverance.chainflip.io/

Untuk mendapatkan tFlip Token anda dapat mengikuti langkah-langkah dibawah:

- Join Discord : https://discord.gg/cm2z9V6b
- Pergi ke 🚰|faucet
- Kirim chat !drip <ADDRESS_ETH> anda

Contoh : !drip 0x..

## Waktunya Eksekusi

<p align="center">
  <img height="auto" width="auto" src="https://user-images.githubusercontent.com/38981255/203699565-716d3576-2c5d-420d-987c-388b344f9802.JPG">
</p>

```
sudo mkdir -p /etc/apt/keyrings
curl -fsSL repo.chainflip.io/keys/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/chainflip.gpg
```

<p align="center">
  <img height="auto" width="auto" src="https://user-images.githubusercontent.com/38981255/203699561-c14b3588-a900-4ca5-ac09-82f23dc35ecf.jpg">
</p>

```
gpg --show-keys /etc/apt/keyrings/chainflip.gpg
```

<p align="center">
  <img height="auto" width="auto" src="https://user-images.githubusercontent.com/38981255/203699559-61bc03ea-0534-4970-8ad0-e39347cac011.jpg">
</p>

```
echo "deb [signed-by=/etc/apt/keyrings/chainflip.gpg] https://repo.chainflip.io/perseverance/ focal main" | sudo tee /etc/apt/sources.list.d/chainflip.list
```

<p align="center">
  <img height="auto" width="auto" src="https://user-images.githubusercontent.com/38981255/203699558-d8eb70b1-0226-4907-a5d1-b02985b2ed46.jpg">
</p>

```
sudo apt-get update
sudo apt-get install -y chainflip-cli chainflip-node chainflip-engine
```

<p align="center">
  <img height="auto" width="auto" src="https://user-images.githubusercontent.com/38981255/203707588-a5803edf-9701-4c31-8030-55d423d02729.JPG">
</p>

```
sudo mkdir /etc/chainflip/keys
```
```
echo -n "YOUR_VALIDATOR_WALLET_PRIVATE_KEY" >> /etc/chainflip/keys/ethereum_key_file
```

Ganti `YOUR_VALIDATOR_WALLET_PRIVATE_KEY` dengan private key anda

## Buat Signing Keys

<p align="center">
  <img height="auto" width="auto" src="https://user-images.githubusercontent.com/38981255/203699551-bc9b611f-0a9f-48c1-9862-18f0c7e674ff.jpg">
</p>

```
chainflip-node key generate >> sign_key.txt
```

Check :

```
cat sign_key.txt
```

## Add Variable Secret Seed

<p align="center">
  <img height="auto" width="auto" src="https://user-images.githubusercontent.com/38981255/203699547-9bb5a7cb-fa9a-463b-86e8-c05caa80931a.PNG">
</p>

```
SECRET_SEED=ISI-DENGAN-SECRET-SEED
```

**ISI-DENGAN-SECRET-SEED** = Isi Dengan Secret Key Yang Sebelumnya Sudah di Backup di Tahap Sebelumnya

```
echo -n "${SECRET_SEED:2}" | sudo tee /etc/chainflip/keys/signing_key_file
```

## Create Node Key

<p align="center">
  <img height="auto" width="auto" src="https://user-images.githubusercontent.com/38981255/203699544-878fd8f2-2ac7-47b8-813c-b5d6145d474b.PNG">
</p>

```
sudo chainflip-node key generate-node-key --file /etc/chainflip/keys/node_key_file
```
```
cat /etc/chainflip/keys/node_key_file
```

Backup Juga Node Key Kalian Simpen

## Konfigurasi 

<p align="center">
  <img height="auto" width="auto" src="https://user-images.githubusercontent.com/38981255/203699543-31e428cb-82dd-4d99-b9d6-98186fd81dc2.png">
</p>

```
sudo mkdir -p /etc/chainflip/config
sudo nano /etc/chainflip/config/Default.toml
```

Salin File di Bawah Ini, Paste ke Terminal

```
# Default configurations for the CFE
[node_p2p]
node_key_file = "/etc/chainflip/keys/node_key_file"
ip_address="IP_ADDRESS_OF_YOUR_NODE"
port = "8078"

[state_chain]
ws_endpoint = "ws://127.0.0.1:9944"
signing_key_file = "/etc/chainflip/keys/signing_key_file"

[eth]
# Ethereum RPC endpoints (websocket and http for redundancy).
ws_node_endpoint = "WSS_ENDPOINT_FROM_ETHEREUM_CLIENT"
http_node_endpoint = "HTTPS_ENDPOINT_FROM_ETHEREUM_CLIENT"

# Ethereum private key file path. This file should contain a hex-encoded private key.
private_key_file = "/etc/chainflip/keys/ethereum_key_file"

[signing]
db_file = "/etc/chainflip/data.db"
```

Ganti Variable di Atas :

- IP_ADDRESS_OF_YOUR_NODE = Ganti Dengan IP VPS Kalian
- WSS_ENDPOINT_FROM_ETHEREUM_CLIENT = Ganti Dengan WSS ENDPOINT Yang Sebelumnya Sudah Kalian Buat di Website Alcemy
- HTTPS_ENDPOINT_FROM_ETHEREUM_CLIENT= Ganti Dengan HTTPS ENDPOINT Yang Sebelumnya Sudah Kalian Buat di Website Alcemy

## Jalankan Node

**Jalankan node**

<p align="center">
  <img height="auto" width="auto" src="https://user-images.githubusercontent.com/38981255/203699542-73a82879-40f7-4945-9fcb-5246294756c7.JPG">
</p>

```
sudo systemctl start chainflip-node
```

**Cek status node**

```
sudo systemctl status chainflip-node
```

**Cek log dan Biarkan Syncron Selesai**

<p align="center">
  <img height="auto" width="auto" src="https://user-images.githubusercontent.com/38981255/203699534-7f209f04-9ac1-41bf-a4c9-79c682d6973f.JPG">
</p>

```
tail -f /var/log/chainflip-node.log
```

Jika log sudah seperti ini 💤 Idle (15 peers), best: #3578 (0xcf9a…d842), finalized #3576 (0x6a0e…03fe), ⬇ 27.0kiB/s ⬆ 25.5kiB/s ✨ Imported #3579 (0xa931…c03e) anda dapat melanjutkan langkah selanjutnya

**Jalankan chainflip-engine**

```
sudo systemctl start chainflip-engine
```

**Cek status chainflip-engine**

```
sudo systemctl status chainflip-engine
```

**Mulai ulang chainflip-node dan chainflip-engine**

```
sudo systemctl enable chainflip-node
sudo systemctl enable chainflip-engine
```

**Cek log chainflip-engine**

```
tail -f /var/log/chainflip-node.log
```

## Stake

Sebelum melanjutkan ke langkah berikutnya, pastikan anda telah memiliki tFlip Token

Ikuti langkah-langkah berikut untuk staking tFlip Token:

* Pergi ke [Perseverance Staking App](https://stake-perseverance.chainflip.io/)
* Pilih `My nodes`
* Pilih `+ Add node` 
* Pilih `Register new node`
* Masukan `Public key (SS58)` dan jumlah tFlip Token yang ingin di-stake, lalu pencet `Stake`
* Konfirmasi transaksi di Metamask

Setelah itu mulai ulang chainflip-engine

```
sudo systemctl restart chainflip-engine
```

> Jika anda membuka website `Perseverance Staking App` menggunakan hp, pastikan anda menggunakan Desktop mode untuk melihat menu `My nodes`
> Jika anda mengikuti tutorial ini dari awal, anda dapat mencari `Public key (SS58)` di file `sign_key.txt`


## Daftarkan Validator key

Sebelum mendaftarkan Validator key, pastikan node anda telah tersinkronisasi penuh, lalu jalankan perintah dibawah:

```
sudo chainflip-cli \
      --config-path /etc/chainflip/config/Default.toml \
      register-account-role Validator
```

> Setelah menjalankan perintah diatas, tunggu sampe validator key anda terdaftar. Proses ini dapat memakan waktu beberapa saat

Setelah itu aktifkan validator agar bisa mengikuti auction selanjutnya, jalankan perintah berikut:

```
sudo chainflip-cli \
    --config-path /etc/chainflip/config/Default.toml \
    activate
```

Terakhir putar validator key anda dengan menggunakan perintah berikut:

```
sudo chainflip-cli \
    --config-path /etc/chainflip/config/Default.toml rotate
```

(OPSIONAL) anda dapat mengkostumisasi nama validator anda menggunakan perintah berikut:

```
sudo chainflip-cli \
    --config-path /etc/chainflip/config/Default.toml \
    vanity-name <NAMA_BARU_VALIDATOR_ANDA>
```

## Menghentikan validator

Jika anda ingin berhenti menjadi validator, anda bisa menggunakan perintah berikut:

```
sudo chainflip-cli \
    --config-path /etc/chainflip/config/Default.toml \
    retire
```

> Setelah menjalankan perintah diatas, anda akan berhenti mengikuti validator auction

Lalu tarik tFlip Token anda

```
sudo chainflip-cli \
    --config-path /etc/chainflip/config/Default.toml \
    claim <JUMLAH_TFLIP_TOKEN_YANG_INGIN_DITARIK> <ADDRESS_ETH_UNTUK_MENERIMA_TOKEN>
```

> Jangan lupa untuk memasukan jumlah tFlip Token yang ingin ditarik dan mengganti address ETH

## Perintah berguna

### Menjalankan service

* Menjalankan service chainflip-node

  ```
  sudo systemctl start chainflip-node
  ```

* Menjalankan service chainflip-engine

  ```
  sudo systemctl start chainflip-engine
  ```

### Memulai ulang service

* Memulai ulang service chainflip-node

  ```
  sudo systemctl restart chainflip-node
  ```

* Memulai ulang service chainflip-engine

  ```
  sudo systemctl restart chainflip-engine
  ```

### Menghentikan service

* Menghentikan service chainflip-node

  ```
  sudo systemctl stop chainflip-node
  ```

* Menghentikan service chainflip-engine

  ```
  sudo systemctl stop chainflip-engine
  ```

### Cek log

* Cek log chainflip-node

  ```
  tail -f /var/log/chainflip-node.log
  ```

* Cek log chainflip-engine

  ```
  tail -f /var/log/chainflip-engine.log
  ```
