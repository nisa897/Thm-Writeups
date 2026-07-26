# TryHackMe - Pickle Rick Writeup

**Hedef IP:** `10.10.x.x`  
**Zorluk:** Kolay  
**İşletim Sistemi:** Linux  
**Kategori:** Web Exploitation / Privilege Escalation  

---

## 📌 Özet 
Pickle Rick; kaynak kod inceleme, web keşfi ve komut çalıştırmaya odaklanan bir CTF odasıdır.
---

## 🚩 Adım Adım Çözüm 

### 1. Keşif ve Bilgi Toplama 
- **Web Taraması:** Port 80 üzerinde çalışan web sunucusu incelendi.
- **Kaynak Kod Analizi:** Ana sayfanın HTML kaynak kodunda (`Ctrl + U`) yorum satırı içerisine gizlenmiş kullanıcı adı bulundu.
- **Robots.txt:** `/robots.txt` dizini kontrol edildi ve açık metin (cleartext) parola ifadesi elde edildi.

### 2. İlk Erişim ve Komut Çalıştırma (Initial Access)
- `10.10.x.x/login.php` adresine gidilerek elde edilen kullanıcı adı ve parola ile giriş yapıldı.
- **Command Panel** (`/portal.php`) ekranına erişim sağlandı.
- **Komut Filtrelerini Atlatma :** Web filtresi `cat` gibi temel komutları engellediği için alternatif dosya okuma komutlarından olan 'less' kullanılarak veriler çıkarıldı:
  ```bash
  less "sup3r_s3cr3t_fl4g.txt"
  less "/home/rick/second ingredients"

### 3. Yetki Yükseltme
- 'ls -la' komutunu çalıştırınca sadece root kullanıcısının erişebildiği dosyalar görüldü.
- Mevcut www-data kullanıcısının sudo yetkileri kontrol için ;
```bash
sudo -l '''
komutu kullanıldı.
- www-data kullanıcısının şifresiz bir şekilde tüm komutları root yetkisiyle çalıştırabileceği ((ALL) NOPASSWD: ALL) görüldü.
-/root dizininde bulunan son bayrak okundu.
```bash
less 3rd.txt

