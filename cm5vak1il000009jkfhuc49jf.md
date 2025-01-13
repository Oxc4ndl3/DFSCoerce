---
title: "Penetration tests, or ethical hacking, simulate real-world attacks on your systems, applications, and networks to identify vulnerabilities before mali"
datePublished: Mon Jan 13 2025 17:01:44 GMT+0000 (Coordinated Universal Time)
cuid: cm5vak1il000009jkfhuc49jf
slug: penetration-tests-or-ethical-hacking-simulate-real-world-attacks-on-your-systems-applications-and-networks-to-identify-vulnerabilities-before-mali

---

nmap -sV -p443 176.235.122.12

whatweb 10.150.4.15:80

curl -I  [http://10.150.4.15:80](http://10.150.4.15:80)

**Açıklama**

Sunucu yanıt başlığına göre, nginx'in kurulu sürümü 1.17.7'den öncedir. Bu nedenle, bir bilginin açığa çıkması güvenlik açığından etkilenir.

 **Çözüm**

nginx sürüm 1.17.7 veya daha yenisine yükseltin.

**Description**

According to its Server response header, the installed version of nginx is prior to 1.17.7. It is, therefore, affected by an information disclosure vulnerability.

 **Solution**

Upgrade to nginx version 1.17.7 or later.

**Byte Memory Overwrite RCE**

 **Açıklama**

Sunucu yanıt başlığına göre, nginx'in kurulu sürümü 1.20.1'den önce 0.6.18'dir. Bu nedenle, bir uzaktan kod yürütme güvenlik açığından etkilenir. nginx çözümleyicide, kimliği doğrulanmamış uzak bir saldırganın özel hazırlanmış bir DNS yanıtı kullanarak 1 baytlık belleğin üzerine yazmasına neden olarak, çalışan işlemin çökmesine veya potansiyel olarak rastgele kod yürütülmesine neden olabilecek bir güvenlik sorunu belirlendi.

Nessus'un bu sorunu test etmediğini, bunun yerine yalnızca uygulamanın kendi bildirdiği sürüm numarasına güvendiğini unutmayın.

**Çözüm**

nginx 1.20.1 veya sonraki bir sürümüne yükseltin.

**Description**

According to its Server response header, the installed version of nginx is 0.6.18 prior to 1.20.1. It is, therefore, affected by a remote code execution vulnerability. A security issue in nginx resolver was identified, which might allow an unauthenticated remote attacker to cause 1-byte memory overwrite by using a specially crafted DNS response, resulting in worker process crash or, potentially, in arbitrary code execution.

Note that Nessus has not tested for this issue but has instead relied only on the application's self-reported version number. 

**Solution**

Upgrade to nginx 1.20.1 or later. 

Multiple Vulnerabilities

**Açıklama**

Sunucu yanıt başlığına göre, nginx'in kurulu sürümü 1.16.1'den önceki 1.9.5 veya 1.17.3'ten önceki 1.17.x'tir. Bu nedenle, birden çok hizmet reddi güvenlik açığından etkilenir:

\- HTTP/2 protokol yığınında, istisnai koşulların yanlış işlenmesi nedeniyle bir hizmet reddi güvenlik açığı bulunmaktadır. Kimliği doğrulanmamış, uzaktaki bir saldırgan, büyük bir veri isteğinin pencere boyutunu ve akış önceliğini değiştirerek bir hizmet reddi durumuna neden olarak bundan yararlanabilir. (CVE-2019-9511)

\- İstisnai koşulların yanlış işlenmesi nedeniyle HTTP/2 protokol yığınında bir hizmet reddi güvenlik açığı bulunmaktadır. Kimliği doğrulanmamış, uzak bir saldırgan, birden çok istek akışı oluşturarak ve akışların önceliğini sürekli olarak karıştırarak bir hizmet reddi durumuna neden olarak bundan yararlanabilir. (CVE-2019-9513)

\- HTTP/2 protokol yığınında, istisnai koşulların yanlış işlenmesi nedeniyle bir hizmet reddi güvenlik açığı bulunmaktadır. Kimliği doğrulanmamış, uzak bir saldırgan, hizmet reddi durumuna neden olmak için sıfır uzunluklu başlık adı ve sıfır uzunluk başlık değerine sahip bir başlık akışı göndererek bundan yararlanabilir. (CVE-2019-9516)

**Çözüm**

nginx sürüm 1.16.1 / 1.17.3 veya daha yenisine yükseltin.

**Description**

According to its Server response header, the installed version of nginx is 1.9.5 prior to 1.16.1 or 1.17.x prior to 1.17.3. It is, therefore, affected by multiple denial of service vulnerabilities :

\- A denial of service vulnerability exists in the HTTP/2 protocol stack due to improper handling of exceptional conditions. An unauthenticated, remote attacker can exploit this, by manipulating the window size and stream priority of a large data request, to cause a denial of service condition. (CVE-2019-9511)

\- A denial of service vulnerability exists in the HTTP/2 protocol stack due to improper handling of exceptional conditions. An unauthenticated, remote attacker can exploit this, by creating multiple request streams and continually shuffling the priority of the streams, to cause a denial of service condition. (CVE-2019-9513)

 - A denial of service vulnerability exists in the HTTP/2 protocol stack due to improper handling of exceptional conditions. An unauthenticated, remote attacker can exploit this, by sending a stream of headers with a zero length header name and zero length header value, to cause a denial of service condition. (CVE-2019-9516)

**Solution**

Upgrade to nginx version 1.16.1 / 1.17.3 or later.