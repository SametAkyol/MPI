# MPI — Multi-Protocol Interface

MPI (Multi-Protocol Interface), kablolu ve kablosuz haberleşme arayüzlerini tek bir donanım platformunda bir araya getiren, gömülü sistemler ve endüstriyel uygulamalar için geliştirilmiş bir haberleşme kartıdır.

STM32F407VET6 mikrodenetleyicisi, DP83825 Ethernet PHY ve CC1101 + CC1190 RF alt sistemi üzerine kurulan MPI; Ethernet, RF, CAN, RS485 ve USB arayüzlerini tek bir PCB üzerinde birleştirir.

Donanım tasarımı, PCB üretimi ve doğrulama çalışmaları tamamlanmıştır.

## 1. Donanım Özeti

MPI'nin temel donanım bileşenleri ve işlevleri aşağıda verilmiştir.

| Bileşen | İşlev |
|---|---|
| STM32F407VET6 | Ana mikrodenetleyici; sistem kontrolü ve veri işleme |
| DP83825 | Ethernet fiziksel katman (PHY) arayüzü |
| CC1101 | Sub-GHz RF alıcı-vericisi |
| CC1190 | RF verici gücünü ve alıcı performansını artırmaya yönelik RF ön uç |

Bu bileşenler, farklı haberleşme arayüzlerinin merkezi bir mikrodenetleyici üzerinden yönetilmesini sağlayan donanım altyapısını oluşturur.

## 2. Haberleşme Arayüzleri

MPI, farklı haberleşme ihtiyaçlarını tek kart üzerinden karşılamak üzere beş temel arayüz sunar.

| Arayüz | Açıklama |
|---|---|
| **RF** | CC1101 ve CC1190 üzerinden kablosuz veri iletişimi |
| **Ethernet** | DP83825 üzerinden kablolu ağ bağlantısı |
| **CAN** | CAN veri yolu üzerinden haberleşme |
| **RS485** | Diferansiyel seri haberleşme |
| **USB** | Bilgisayar bağlantısı ve desteklenen USB işlevleri |

Arayüzlerin çalışma modları, veri hızları ve desteklenen protokoller ilgili donanım yapılandırmasına ve firmware uygulamasına bağlıdır.

## 3. Donanım Mimarisi

### 3.1. Ana Kontrol Birimi

STM32F407VET6, MPI kartının merkezi işlem birimidir. Haberleşme çevre birimlerini yönetir, verileri işler ve farklı arayüzler arasındaki iletişim için gerekli kontrol işlevlerini yürütür.

### 3.2. Ethernet Alt Sistemi

DP83825 Ethernet PHY, mikrodenetleyici ile Ethernet fiziksel bağlantısı arasındaki katmanı sağlar. Bu alt sistem, kartın Ethernet ağı üzerinden harici cihazlarla iletişim kurmasına olanak tanır.

### 3.3. RF Alt Sistemi

Kablosuz haberleşme alt sistemi, CC1101 RF alıcı-vericisi ve CC1190 RF ön ucundan oluşur.

- **CC1101:** Desteklenen Sub-GHz frekans bantlarında RF sinyallerinin gönderilmesini ve alınmasını sağlar.
- **CC1190:** RF verici çıkış gücünü artırır ve alıcı tarafındaki RF performansını iyileştirmeye yönelik işlevler sunar.

RF çalışma frekansı, modülasyon, veri hızı ve RF performansı kullanılan yapılandırmaya bağlıdır.

### 3.4. CAN Arayüzü

CAN arayüzü, CAN veri yolu kullanan gömülü kontrol sistemleri ve dağıtık elektronik sistemlerle haberleşmek üzere tasarlanmıştır.

### 3.5. RS485 Arayüzü

RS485 arayüzü, diferansiyel seri haberleşme altyapısı üzerinden endüstriyel cihazlar ve gömülü sistemlerle iletişim kurulmasını sağlar.

### 3.6. USB Arayüzü

USB arayüzü, kartın uyumlu bir bilgisayara veya USB cihazına bağlanmasını sağlar. Desteklenen çalışma modu ve işlevler firmware uygulamasına bağlıdır.

## 4. PCB Tasarımı

MPI kartı, **1,6 mm kalınlığında ve dört katmanlı bir PCB** olarak tasarlanmıştır. Katman yapısı, sinyal yönlendirmesi ve güç dağıtımı için uygun bir yerleşim altyapısı oluşturacak şekilde düzenlenmiştir.

### 4.1. PCB Katman Yapısı

Katman dizilimi aşağıdaki şekildedir:

| Katman | Kullanım |
|---|---|
| L1 | Sinyal + güç |
| L2 | GND |
| L3 | GND |
| L4 | Sinyal + güç |

İç katmanların GND düzlemleri olarak kullanılması, sinyal dönüş yollarının oluşturulmasına ve güç bütünlüğünün desteklenmesine yardımcı olur.

<p align="center">
  <img src="https://github.com/user-attachments/assets/d37de3f2-e5bc-418b-8b68-0fac166a13bc" alt="MPI dört katmanlı PCB katman dizilimi" width="85%"/>
</p>

### 4.2. PCB Yerleşimi

Kartın üst ve alt katman yerleşimleri aşağıda gösterilmiştir.

<table>
  <tr>
    <td align="center" width="50%">
      <strong>Üst Katman — Top Layer</strong><br/>
      <img src="https://github.com/user-attachments/assets/d5433e8e-2538-40c4-8412-6a4c6e5e6e8c" alt="MPI PCB üst katman yerleşimi" width="100%"/>
    </td>
    <td align="center" width="50%">
      <strong>Alt Katman — Bottom Layer</strong><br/>
      <img src="https://github.com/user-attachments/assets/a0e4d9a6-5cd6-4a28-980d-a0b8eef832a3" alt="MPI PCB alt katman yerleşimi" width="100%"/>
    </td>
  </tr>
</table>

### 4.3. Üç Boyutlu PCB Modeli

PCB'nin üç boyutlu modeli, bileşen yerleşimini ve kartın fiziksel düzenini göstermektedir.

<p align="center">
  <img src="https://github.com/user-attachments/assets/688c323e-c201-444d-af2e-180ad89e1214" alt="MPI PCB üç boyutlu tasarım modeli" width="100%"/>
</p>

### 4.4. Üretilmiş Donanım

Tasarımın fiziksel karşılığı olan üretilmiş MPI kartı aşağıda gösterilmiştir.

<p align="center">
  <img src="https://github.com/user-attachments/assets/1997f581-32af-422f-b33d-931ccba52fec" alt="Üretilmiş MPI haberleşme kartı" width="80%"/>
</p>

## 5. Tasarım ve Doğrulama

MPI donanımının tasarımı ve doğrulama çalışmaları tamamlanmıştır.

Kart; birden fazla kablolu ve kablosuz haberleşme arayüzünü aynı PCB üzerinde birleştiren bütünleşik bir donanım platformu olarak geliştirilmiştir.

Ölçülmüş performans değerleri, test koşulları ve arayüz bazındaki doğrulama sonuçları ilgili teknik dokümantasyon kapsamında sunulabilir.

## 6. Kullanım Alanları

MPI aşağıdaki uygulamalarda değerlendirilebilir:

- Gömülü haberleşme ağ geçitleri
- Endüstriyel haberleşme ve kontrol sistemleri
- Kablosuz telemetri
- Ağ bağlantılı gömülü cihazlar
- Haberleşme arayüzlerinin entegrasyonu ve test edilmesi
- Kablolu ve kablosuz sistemler arasında veri aktarımı

## 7. Proje Durumu

MPI'nin donanım tasarımı, PCB üretimi ve doğrulama çalışmaları tamamlanmıştır. Mevcut donanım platformu, firmware geliştirme ve uygulamaya özel entegrasyon çalışmaları için kullanılabilir.

---

**MPI — Multi-Protocol Interface**

*Tek kart. Çoklu haberleşme arayüzü.*
