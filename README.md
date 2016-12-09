# NAV COLLECTION INTEGRATION SERVICE KURULUM DÖKÜMANI #


 
## 1	GİRİŞ ##
Bu doküman,  Bulut tahsilat ve Dynamics NAV entegrasyon servisinin kurulumu hakkındadır.
 

##2	WİNDOWS SERVİS KURULUMU
Kurulum dosyasının son halini https://github.com/icobani/NAV-Collection-Integration-Setup adresinden indirebilirsiniz. Kurulum adımları için aşağıdaki adımları takip etmelisiniz.
##2.1	Kurulum için gereklilikler


- 	Kurulumu yapacağınız kullanıcının servis kurulumu yetkisinin olması gerekmektedir.
-	Kurulum sonrasında servis Dynamics NAV’a Windows Authantication kullanıcısı ile ulaşır. Bu şekilde herhangi bir konfig dosyasında kullanıcı bilgileri ve şifreler kaydedilmez.
-	Servisin çalışacağı servis kullanıcısının Dynamics NAV tarafındaki yetkilendirmesinin önceden yapılmış oldundan emin olunuz.
-	Servis bulut sistemine Dynamics NAV üzerinde tanımlanan Api kod, kullanıcı ve şifre bilgileri ile bağlanır. Bu ayarların Dynamics NAV üzerinde yapıldığından emin olun.
-	Bunun haricinde NAV üzerinde yapılması zorunlu olan tanımlamalar için. Dynamics NAV dökümanını edinip gerekli kurulumları tamamlayın.
 
##2.2	Setup Dosyasının İndirilmesi
[https://github.com/icobani/NAV-Collection-Integration-Setup](https://github.com/icobani/NAV-Collection-Integration-Setup "https://github.com/icobani/NAV-Collection-Integration-Setup") adresine gidiniz ve setup dosyasını seçiniz. 
![Resim](https://raw.githubusercontent.com/icobani/NAV-Collection-Integration-Setup/master/img/02.png)

Download butonuna basarak yükleme dosyasını server’a indiriniz.
![Resim](https://raw.githubusercontent.com/icobani/NAV-Collection-Integration-Setup/master/img/03.png)
 
 
##2.3	Kurulum
Kurulum dosyasını sağ mous’a basarak admin modunda çalıştırınız.
 ![Resim](https://raw.githubusercontent.com/icobani/NAV-Collection-Integration-Setup/master/img/13.png)


Bağlantı ayarlarını aşağıdaki örneğe göre yapınız.
![Resim](https://raw.githubusercontent.com/icobani/NAV-Collection-Integration-Setup/master/img/04.png)

 
-	Sunucu Adı : Dynamics NAV SQL server’ın adresi
-	Veritabanı Adı : Dynamics NAV veritabanı adı.
-	Şirket Adı : Çalışılacak şirket.
	
Bundan sonraki adımları ileri butonuna basarak takip ediniz.
 
##2.4	Servis kullanıcısının tanımlanması.
Windows + R tuşlarına basarak services.msc komutunu çalıştırınız. Aşağıdaki şekilde servisin sistemde kurulduğunu görebilirsiniz. Gördüğünüz gibi henüz servis çalışmıyor ve kullanıcısı Localsystem account’u seçilmiş durumda. Bu kullanıcı ile NAV’a bağlanamayız bu yüzden Dynamics NAV’da daha önce yetkilendirilmesi yapılmış olan kullanıcıyı bu servise atamalıyız. Bu adımdan sonra servisin çalışacağı tüm işlemler tanımlaması yapılmış olan kullanıcı ile olacaktır.
 
![Resim](https://raw.githubusercontent.com/icobani/NAV-Collection-Integration-Setup/master/img/05.png)

 
Servis üzerinde sağ mouse’a basarak Properties’e giriniz. Log On tabında ilgili kullanıcı ve şifresini giriniz.

 ![Resim](https://raw.githubusercontent.com/icobani/NAV-Collection-Integration-Setup/master/img/06.png)

 
##2.5	Config dosyası
Servisin config dosyası kurulumun yapıldığı dizindedir. Kurulum sonrasında config dosyasında değişiklik yapmak isterseniz.“NAV Collection Integration.exe.config” dosyasını sağ Mouse ile edit ediniz. appSetting penceresi içindeki kısımda değişiklik içinde live ve debug (TEST) kısmı için iki ayrı NAV tanımı yapabilirsiniz. Yani Navision test database’i yada live şeklinde. debug mode’a geçmek için değeri true yapmalısınız. 
 
![Resim](https://raw.githubusercontent.com/icobani/NAV-Collection-Integration-Setup/master/img/07.png)

 
#3	SERVİS İŞLEMLERİ
Servis içersindeki işlemlerin çoğu otomatik olarak Dynamics NAV içinde tanımlanan belli aralıklarla çalışır. Bununla birlikte istenildiği zaman da ilgili servisler dışardan da çalıştırılabilir.

![Resim](https://raw.githubusercontent.com/icobani/NAV-Collection-Integration-Setup/master/img/08.png)

##3.1	Son altı ay işlem görmüş müşterilerin entegrasyona dahil edilmesi
Bu servis otomatik olarak belli aralıklarla çalışan bir servis değildir. Bu fonksiyonun benzeri NAV içersinde de olmakla beraber. Servis üzerinden de çalıştırılabilir. Servis son altı aydaki muhasebesel hareketleri takip ederek müşteriyi entegrasyona dahil edecek ilgili işareti koyar. Servisin olduğu dizine giderek command prompt üzerinden aşağıdaki şekilde bu işlemi manuel olarak çalıştırabilirsiniz.
![Resim](https://raw.githubusercontent.com/icobani/NAV-Collection-Integration-Setup/master/img/09.png) 

##3.2	Firma bilgilerinin BulutTahsilat sistemine gönderilmesi
Dynamics NAV üzerinde gönderilecek olarak işaretli olan müşterileri BulutTahsilat sistemine gönderir. Servisin olduğu dizine giderek command prompt üzerinden aşağıdaki şekilde bu işlemi manuel olarak çalıştırabilirsiniz.

![Resim](https://raw.githubusercontent.com/icobani/NAV-Collection-Integration-Setup/master/img/10.png)

##3.3	Firma Banka bilgilerinin BulutTahsilat sistemine gönderilmesi
Dynamics NAV üzerinde gönderilecek olarak işaretlenmiş olan müşteri banka bilgilerini BulutTahsilat sistemine gönderir. Servisin olduğu dizine giderek command prompt üzerinden aşağıdaki şekilde bu işlemi manuel olarak çalıştırabilirsiniz.
![Resim](https://raw.githubusercontent.com/icobani/NAV-Collection-Integration-Setup/master/img/11.png) 
##3.4	BulutTahsilat eşleme yapılmış olan tahsilat bilgileri alınıyor
BulutTahsilattan eşlemesi yapılmış olan ödeme bilgilerini Dynamics NAV’a aktarır. Servisin olduğu dizine giderek command prompt üzerinden aşağıdaki şekilde bu işlemi manuel olarak çalıştırabilirsiniz.
 ![Resim](https://raw.githubusercontent.com/icobani/NAV-Collection-Integration-Setup/master/img/12.png)
##3.5	Navision'da ödeme işlemi deftere nakledilmiş kayıtlar, tamamlandı olarak işaretlenip sistemden siliniyor.
Dynamics NAV üzerinde Deftere Nakledilmiş (muhasebeleştirilmiş) ödeme kayıtları tamamlandı olarak BulutTahsilat’a gönderilir. Servisin olduğu dizine giderek command prompt üzerinden aşağıdaki şekilde bu işlemi manuel olarak çalıştırabilirsiniz.

![Resim](https://raw.githubusercontent.com/icobani/NAV-Collection-Integration-Setup/master/img/13.png)
#4	LOGLAMA SİSTEMİ
Servisin loglama dosyası log dizini içersinde bulunmaktadır. Ayrıca her Pazar günü hafta içinde oluşan log dosyası sıkıştırılarak yedeklenir ve log dosyası silinir. 

