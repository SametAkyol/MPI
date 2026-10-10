# MPI — Multi-Protocol Interface

**MPI (Multi-Protocol Interface)**, farklı haberleşme arayüzlerini tek bir donanım platformunda bir araya getirmek amacıyla geliştirilen endüstriyel haberleşme kartıdır.

Proje; kablosuz RF haberleşmesi, Ethernet bağlantısı, CAN bus, RS485 ve USB arayüzlerini tek bir donanım üzerinde birleştirerek farklı sistemler arasında esnek bir haberleşme altyapısı oluşturmayı hedefler.

## 1. Proje Hedefi

MPI'nin temel amacı, farklı haberleşme standartlarına ihtiyaç duyan gömülü sistemler ve endüstriyel elektronik uygulamaları için kompakt, modüler ve genişletilebilir bir donanım platformu oluşturmaktır.

Kartın tasarımında aşağıdaki hedefler gözetilmektedir:

- Birden fazla haberleşme arayüzünün tek kartta birleştirilmesi
- Kablolu ve kablosuz haberleşme seçeneklerinin sunulması
- Gömülü sistemlerle entegrasyonun kolaylaştırılması
- Donanım ve yazılım geliştirme süreçlerinin desteklenmesi
- Endüstriyel uygulamalara uygun bir elektronik altyapı oluşturulması

## 2. Haberleşme Arayüzleri

| Arayüz | Amaç |
|---|---|
| RF | Kablosuz veri iletişimi |
| Ethernet | Kablolu ağ bağlantısı |
| CAN | Dağıtık kontrol sistemleri arasında haberleşme |
| RS485 | Endüstriyel seri haberleşme |
| USB | Bilgisayar bağlantısı, yapılandırma ve geliştirme |

Arayüzlerin desteklediği veri hızları, protokoller ve çalışma modları donanım tasarımına ve firmware uygulamasına bağlıdır.

## 3. Donanım Mimarisi

MPI donanımı temel olarak aşağıdaki işlevsel bloklardan oluşacak şekilde tasarlanmaktadır:

- **Kontrol birimi:** Haberleşme arayüzlerinin yönetimi ve veri işleme.
- **RF birimi:** Kablosuz haberleşme için gerekli RF donanımı.
- **Ethernet birimi:** Ağ bağlantısını sağlayan Ethernet fiziksel katmanı ve ilgili devreler.
- **CAN arayüzü:** CAN veri yolu bağlantısı için gerekli fiziksel katman devresi.
- **RS485 arayüzü:** Diferansiyel seri haberleşme için transceiver devresi.
- **USB arayüzü:** USB bağlantısı ve desteklenen çalışma modları için gerekli devreler.
Desteklenen protokoller, veri yönlendirme mekanizması ve yapılandırma yöntemi firmware geliştirme sürecinde belirlenecektir.

**MPI — Multi-Protocol Interface**  
*One board. Multiple communication interfaces.*
