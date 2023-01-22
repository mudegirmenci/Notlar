### dd Komutu ###

temel amacı dosyaları kopyalamak olan dd komutu ile disk veya partition yedeği oluşturup, tekrar geri yükleme işlemleri hızlıca yapılabilir.

# dd if=/dev/sda of=/dev/sdb 

if -> input file
of -> output file
bs -> block size

### Temel Kullanım Amaçları ###


    Diskteki verilerin imhası.
    Bir bölümü veya sürücünün tüm bölümünü yedekleme, geri yükleme.
    Sabit boyutta dosyalar oluşturma.
    Veri formatlarının dönüşümü.

Örnek 1:Diskin içeriğini temizlemek için;

# dd if=/dev/zero of=/dev/sdb


Örnek 2:Geri yükleme işlemi için bir bölüm HDD yedeklemesi almak;

# dd if=/dev/sda2 of=~/hdddisk.img


Örnek 3:Bir sabit diski başka bir sabit diske kopyalamak için;

# dd if=/dev/sda of=/dev/sdb

Örnek 4:İmaj dosyasını başka bir makineye geri yüklemek için;

# dd if=hdadisk.img of=/dev/sdb3


Örnek 5:Oluşturulan imajı sıkıştırmak için gzip veya bzip2 kullanılabilir;

# dd if=/dev/sda2 | bzip hdadisk.img.bz2

Örnek 6:Disk üzerindeki verilerin imha (wipe) edilmesi için:

# dd if=/dev/zero of=/dev/sdx bs=1M conv=noerror

Örnek 7:Bu komut sayesinde 1M sıfır byte bilgisi (00) sda olarak nitelendirilen disk üzerine yazılacaktır. Disk üzerinde partition’ların bir önemi olmaz, disk tamamen sıfır ile doldurulur.
    
Örnek 8:cp komutu yerine kullanabiliriz.

	
# dd if=/home/imran/abc.txt of=/mnt/abc.txt
  
Örnek 9:  Kişisel verilerinizi silebiliriz. Bir çok insan rm -rf / verilerinizi yapıp yapmadığımızı düşünür. Ancak bu silme işlemini Photorec veya bazı adli tıp araçları gibi disk kurtarma araçlarını kullanarak kurtarabiliriz. Ancak, verilerinizi kurtarmamayı istemiyorsanız, verilerin bulunduğu bölümünüze rastgele veri yazmanız gerekir.

# dd if=/dev/random of=/dev/sdb

Örnek 10:Verileri kurtarmayı dahada zorlaştırmak için, birden çok kez komut verebiliriz.

# for i in {1..10};do dd if=/dev/random of=/dev/sdb;done

Örnek 11: swap olarak kullanılabilecek dd komutuyla sanal dosya sistemi oluşturabiliriz.

# dd if=/dev/zero of=/swapfile bs=1024 count=200000

bs : block boyutudur. Blok boyutunu belirtmezseniz, dd varsayılan bir blok boyutunu 512 bayt kullanır. Aşağıdaki kurallar blok boyutları için çalışacaktır. kB(1000 byte), K(1024 byte), Mb(1000*1000 byte), MB(1024*1024 byte), Gb, GB, T, P ,E ,Z, Y opsiyonları kullanılabilir.

Örnek 12:Disk yazma hızını ölçmek için;

# dd if=/dev/zero of=tempfile bs=1M count=1024

Örnek 13:Disk buffer okuma ölçmek için;

# dd if=tempfile of=/dev/null bs=1M count=102


Örnek 14: Disk gerçek okuma hızını ölçmek için;
	
/sbin/sysctl -w vm.drop_caches=3
dd if=tempfile of=/dev/null bs=1M count=1024




DD sabit bir diskin,usb belleğin,cd nin yada dvd nin imajını alabilir.Aldığınız bu imajı sisteme mount ederekte usb bilgisayarımıza takılıymış gibi açabilir yada verilerimizi kurtarabiliriz.

DD alt seviye kopyalama yapar yanı diskimizinboş alanlarda dahil  tamamının kopyalayıp imajını alır.Yani disk boyutu ile imaj boyutu aynı olmalıdır.

DD komutu if ve of olmak üzere iki temel parametre alır. Diğer parametreler ise isteğe bağlıdır.If bilgisi burada kaynak aygıt/partition u, of ise hedefi göstermektedir.

Bunun dışında bs  kaçar byte kopyalanacağını belirtir.conv=noerror ise hata alsan bile kopyalamaya devam et demeye yarar.

Öncelikle burada sudo fdisk -l komutu ile flash belleğimizin yolunu bulduk bunun dışında diske nerden yazılmaya başlandığı (Start 2048) bitişi (End=798176) Diskin formatı gibi bilgileri edindik.Burada sdb flash bellleğimizi sdb1 ise onun bir partition göstermektedir.Bu yüzden imaj alırken diskimizin tamamını yanı sdb nin imajını almalıyız.


sudo dd if=/dev/sdb of=/home/mustafa/usb.img bs=10 conv=noerror ile usb imajı masaüstüne alınır.


mkdir ile imajac diye boş bir klasör oluşturdum.sudo mount -o offset=1048576 /home/ahmet/Desktop/disk.img  /home/ahmet/Desktop/imajac/ komutu ile de disk.img adlı imaj dosyamı imajac adlı klasöre mount ettim.Artık imajac klasörüne tıkladığımızda imajımıza ulaşıyoruz.Burada mount komutu ile ilgili offset önemli offset değerini kendimiz hesaplıyoruz ilk resimdeki sudo fdisk -l komutunun çıktısındaki diskin yazılmaya başlandığı değeri start değeri  2048 idi.Sector size 512 idi.Bu iki sayıyı çarptığımızda 2048×512=1048576  bizim offset değerimiz oluyor.


https://gurelahmet.com/linuxta-dd-ile-imaj-alma-ve-imaj%C4%B1n-canland%C4%B1r%C4%B1lmas%C4%B1/





https://www.cihangungor.com/adli-incelemelerde-dd-komutunun-kullanimi/
http://www.mustafabektastepe.com/2017/01/15/dd-komutu/


