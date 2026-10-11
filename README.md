# MPI — Multi-Protocol Interface

**MPI (Multi-Protocol Interface)**, kablolu ve kablosuz haberleşme teknolojilerini tek bir donanım platformunda bir araya getirmek amacıyla tasarlanmış çok arayüzlü bir gömülü haberleşme kartıdır.

Kart; STM32F407VET6 mikrodenetleyicisi, DP83825 Ethernet PHY ve CC1101 RF alıcı-vericisi ile CC1190 RF ön ucunu bir araya getirerek gömülü sistemler ve endüstriyel uygulamalar için esnek bir haberleşme altyapısı sunar.

## 1. Donanım Özeti

MPI kartında kullanılan temel bileşenler:

- **STM32F407VET6:** Sistem kontrolü, veri işleme ve haberleşme arayüzlerinin yönetiminden sorumlu ana mikrodenetleyici.
- **DP83825:** Kablolu ağ bağlantısını sağlayan Ethernet fiziksel katman entegresi (PHY).
- **CC1101:** Kablosuz veri iletişimi için kullanılan Sub-GHz RF alıcı-vericisi.
- **CC1190:** CC1101 tabanlı RF sistemi için verici gücünü ve alıcı hassasiyetini artırmaya yönelik RF ön uç entegresi.

Donanım tasarımı tamamlanmış ve doğrulanmıştır.

## 2. Haberleşme Arayüzleri

| Arayüz | İşlev |
|---|---|
| RF | CC1101 ve CC1190 üzerinden kablosuz haberleşme |
| Ethernet | DP83825 üzerinden kablolu ağ bağlantısı |
| CAN | CAN veri yolu üzerinden haberleşme |
| RS485 | Diferansiyel seri haberleşme |
| USB | Bilgisayar bağlantısı, yapılandırma ve geliştirme |

Arayüzlerin çalışma modları ve desteklenen haberleşme parametreleri, ilgili donanımın özelliklerine ve firmware yapılandırmasına bağlıdır.

## 3. Donanım Mimarisi

### 3.1. Ana Kontrol Birimi

STM32F407VET6, kartın merkezi işlem birimidir. Haberleşme çevre birimlerini yönetir, veri işleme görevlerini yürütür ve gömülü uygulamalar için gerekli işlem gücünü sağlar.

### 3.2. Ethernet Alt Sistemi

DP83825 Ethernet PHY, mikrodenetleyici ile Ethernet ağı arasındaki fiziksel katman bağlantısını sağlar.

Bu alt sistem sayesinde MPI, harici sistemler ve ağ destekli cihazlarla kablolu haberleşme kurabilir.

### 3.3. RF Alt Sistemi

Kablosuz haberleşme alt sistemi, CC1101 RF alıcı-vericisi ve CC1190 RF ön ucundan oluşur.

- **CC1101:** Desteklenen Sub-GHz frekans bantlarında RF sinyallerinin gönderilmesi ve alınmasını sağlar.
- **CC1190:** RF verici çıkışının güçlendirilmesini ve alıcı tarafındaki RF performansının iyileştirilmesini sağlar.

RF alt sistemi, uyumlu cihazlar arasında kablosuz veri aktarımı için tasarlanmıştır. Çalışma frekansı, modülasyon türü, veri hızı, çıkış gücü ve alıcı performansı kullanılan RF yapılandırmasına bağlıdır.

### 3.4. CAN Arayüzü

CAN arayüzü, gömülü kontrol sistemleri ve dağıtık kontrol uygulamaları için CAN veri yolu haberleşmesi sağlar.

### 3.5. RS485 Arayüzü

RS485 arayüzü, endüstriyel otomasyon ve gömülü kontrol sistemlerinde yaygın olarak kullanılan diferansiyel seri haberleşmeyi destekler.

### 3.6. USB Arayüzü

USB arayüzü, kartın bir bilgisayara veya uyumlu USB cihazına bağlanmasını sağlar. Sunulan işlevler firmware uygulamasına bağlıdır.

## 4. Tasarım ve Doğrulama

MPI donanımının tasarımı ve doğrulama çalışmaları tamamlanmıştır.

Birden fazla haberleşme arayüzünün aynı PCB üzerinde birleştirilmesiyle harici haberleşme adaptörlerine duyulan ihtiyacın uygun uygulamalarda azaltılması amaçlanmıştır.

Ölçülmüş performans değerleri; test koşulları ve doğrulama sonuçlarıyla birlikte teknik dokümantasyonda belirtilmelidir.

## 5. Kullanım Alanları

MPI aşağıdaki uygulamalarda kullanılabilecek şekilde tasarlanmıştır:

- Gömülü haberleşme ağ geçitleri
- Endüstriyel haberleşme ve kontrol sistemleri
- Kablosuz telemetri
- Ağ bağlantılı gömülü cihazlar
- Donanım geliştirme ve haberleşme testleri
- Kablolu ve kablosuz haberleşme arayüzlerinin entegrasyonu

## 6. Proje Durumu

MPI donanım tasarımı ve doğrulama çalışmaları tamamlanmıştır.

Mevcut donanım platformu, firmware geliştirme, sistem entegrasyonu ve uygulamaya özel yapılandırma çalışmaları için hazırdır.

---

**MPI — Multi-Protocol Interface**

*Tek kart. Çoklu haberleşme arayüzü.*

3. PCB Tasarımı

MPI kartının PCB tasarımı, üst ve alt katman yerleşimleri ile üç boyutlu kart modeli aşağıda gösterilmiştir.

PCB Yerleşimi

<table>
  <tr>
    <td align="center" width="50%">
      <strong>Üst Katman (Top Layer)</strong><br/>
      <img src="https://github.com/user-attachments/assets/d5433e8e-2538-40c4-8412-6a4c6e5e6e8c" alt="MPI PCB üst katman yerleşimi" width="100%"/>
    </td>
    <td align="center" width="50%">
      <strong>Alt Katman (Bottom Layer)</strong><br/>
      <img src="https://github.com/user-attachments/assets/a0e4d9a6-5cd6-4a28-980d-a0b8eef832a3" alt="MPI PCB alt katman yerleşimi" width="100%"/>
    </td>
  </tr>
</table>

3D PCB Modeli

<p align="center">
  <img src="https://github.com/user-attachments/assets/688c323e-c201-444d-af2e-180ad89e1214" alt="MPI PCB üç boyutlu tasarım modeli" width="100%"/>
</p>

Gerçek Donanım

<p align="center">
  <img src="https://github.com/user-attachments/assets/1997f581-32af-422f-b33d-931ccba52fec" alt="MPI üretilmiş PCB ve gerçek donanım" width="80%"/>
</p>




