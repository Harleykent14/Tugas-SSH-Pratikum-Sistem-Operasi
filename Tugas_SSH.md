## INSTALL AND CONFIGURATION SSH

</div>


### Prepare Ubuntu
Langkah pertama yang perlu dilakukan adalah mempersiapkan Ubuntu dengan cara:
  - > sudo apt update && apt upgarade

![Screenshot from 2024-10-04 10-59-04](https://github.com/user-attachments/assets/3fc4a849-3076-42d9-82fb-c7a403ea0adf)

<br>


### Install SSH on Ubuntu
Selanjutnya lakukan penginstallan SSH di Ubuntu
 - > sudo apt install openssh-server
   
![Screenshot from 2024-10-04 11-01-27](https://github.com/user-attachments/assets/3e362e03-9b14-4791-8e21-395cfbe3884a)

<br>


### Start SSH
Mulai program SSh
  - > sudo systemctl enable --now ssh

![Screenshot from 2024-10-04 11-01-59](https://github.com/user-attachments/assets/06a809e3-8b0c-445a-80a1-a35be3e2c219)


### Cek status
  - > sudo systemctl status ssh

![Screenshot from 2024-10-04 11-02-17](https://github.com/user-attachments/assets/146d111c-427b-40e4-9453-e7b2e58b39e6)

<br>


### Configuration The Firewall
Cek UFW status
  - > sudo ufw status

![Screenshot from 2024-10-04 11-02-44](https://github.com/user-attachments/assets/47889d6b-0cf1-4264-b06e-bba41f46daa4)

Jika status UFW inactive seperti di kasus ini, maka kita dapat mengaktifkan dengan:
  - > sudo ufw enable


Izinkan lalu lintas SSH
  - > sudo ufw allow ssh

![Screenshot from 2024-10-04 11-02-57](https://github.com/user-attachments/assets/ffbe6062-1940-409a-9c97-d4a2de1256ba)

<br>


### Connect to The Server
Sambungkan ke server sendiri dengan user dan ip sendiri
  - > ssh kentvb@192.168.92.155

![Screenshot from 2024-10-04 11-04-03](https://github.com/user-attachments/assets/b2a54c38-f8d3-4a86-94f8-8ee61e216e35)


### Configuration SSH
Cadangkan dahulu file sshd_config
```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.initial
```

Lalu edit file konfigurasinya
```
sudo nano /etc/ssh/sshd_config
```

Hilangkan pagar pada Port, PubkeyAuthentication dan PermitRootLogin, untuk baris PermitRootLogin ubah menjadi PermitRootLogin no

![Screenshot from 2024-10-04 11-09-00](https://github.com/user-attachments/assets/abbff0dd-afa9-4aff-bc20-ead267323f36)


Sekarang coba untuk merestart SSH
```
sudo systemctl restart ssh
```

Lalu coba untuk menjalankan ssh lagi dengan port yang dikonfigurasi tadi
```
ssh -p 22 kentvb@192.168.92.155
```

![Screenshot from 2024-10-04 11-11-33](https://github.com/user-attachments/assets/21a02b49-e830-452e-83c2-74a0a3a72fa3)

















