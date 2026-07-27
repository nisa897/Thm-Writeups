# W1seGuy - TryHackMe Write-up

![Room Banner](https://tryhackme-images.s3.amazonaws.com/room-icons/000000000000000000000000.png)

| Detay | Bilgi |
| :--- | :--- |
| **Platform** | [TryHackMe](https://tryhackme.com/r/room/w1seguy) |
| **Zorluk** | Kolay |
| **Kategori** | Cryptography / Reverse Engineering |
| **Tarih** | 2026-07-27 |

---

## 📌 Özet
Bu odada XOR şifrelemesinin zayıflıkları ve bilinen düz metin saldırısı (Known-Plaintext Attack) üzerine odaklanılmıştır:
1. Netcat ile hedef port üzerinden şifreli hex metninin elde edilmesi.
2. Zafiyet barındıran Python kaynak kodunun analizi.
3. Bayrağın bilinen `THM{` ön eki kullanılarak XOR anahtarının (Known-Plaintext Attack) çıkarılması.
4. Eksik anahtar karakterlerinin Python ile brute-force edilerek 1. Bayrağın (Flag 1) elde edilmesi.

---

## 🔍 1. Keşif ve Bilgi Toplama (Reconnaissance)

İlk olarak verilen hedef IP adresi üzerindeki açık portları tespit etmek amacıyla Nmap taraması gerçekleştirilmiştir:

```bash
nmap -sC -sV -oN nmap/initial <HEDEF-IP>
