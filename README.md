# PRTG İnterface SSL 


Bu repository, PRTG (Paessler Router Traffic Generator) için SSL sertifikası kurulumu işlemlerini win-acme aracı kullanarak otomatikleştirmek amacıyla hazırlanmıştır. win-acme, Let's Encrypt tarafından ücretsiz olarak sağlanan SSL sertifikalarını Windows ortamında kolayca almanıza olanak tanır.

Bu repoyu kullanarak, PRTG'nin güvenli HTTPS üzerinden çalışmasını sağlayabilir ve Let's Encrypt sertifikalarını sisteminize otomatik olarak entegre edebilirsiniz.


## Kurulum Adımları

1. win-acme aracını indirin.

2. PRTG'yi HTTPS'ye Yönlendirin: PRTG'nin HTTPS üzerinden çalışması için IIS üzerinde gerekli yapılandırmayı yapın.

3. SSL Sertifikası Alın: win-acme ile PRTG alan adı için SSL sertifikası alın.

4. PRTG'nin sertifika dosya kısmına gerekli dosyaları yükleyiniz.



## Nasıl Kurulur?

https://www.win-acme.com bu link üzerinden win-acme'yi indiriyoruz ve kurulumunu sağlıyoruz. Sitelerimizin win-acme terminalinde çıkması için IIS indirmemiz gerekmektedir. IIS üzerinden alan adınız için web sitesi oluşturmanız gerekmektedir.

![image](https://github.com/user-attachments/assets/fa73c281-bcf3-4acd-8427-b0c2b72b4aad)

Bu ekran üzerinde "N" harfine basıp ilerliyoruz. İleri ki kısımlarda web sitemiz gözükecek ve size uygun olan kısımları seçerek ilerlemeniz gerekecektir. Oluşturmuş olduğunuz sertifika `pfx` ve `pem` uzantılarıyla gelmektedir. PRTG bizden `.pem` `.crt` ve `.key` dosyalarını istemektedir. 

`C:\ProgramData\win-acme\acme-v02.api.letsencrypt.org\Certificates>` klasöründe oluşturmuş olduğunuz SSL dosyaları bulunmaktadır. Burada bulunan `.pem` , `.crt` ve `.key` dosyalarını da çıkartmak gerekmektedir. Aşağıdaki komutları sırayla yazınız.

```
openssl pkey -in yourfile.pem -out prtg.key
openssl x509 -in yourfile.pem -out prtg.crt
```

Bu komutları sırayla yazdıktan sonra `C:\Program Files (x86)\PRTG Network Monitor\cert` dosya yoluna giderek PRTG'ye ait olan `.pem`  `.crt` ve `.key` dosyalarını siliniz. Oluşturmuş olduğunuz dosyaları aşağıdaki isimlerle aktarmamız gerekmektedir. Dosya PRTG tarafı hata verecektir. win-acme sisteminin oluşturmuş olduğu `.pem`  dosyasını buraya `root.pem` ismi ile aktarmanız gerekecektir.

![image](https://github.com/user-attachments/assets/82a6bf1c-3cf6-4525-90ba-0d44bfd187c7)




