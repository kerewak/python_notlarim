İkili (Binary) Dosyalar
Dosyalar çoğunlukla iki farklı sınıfa ayrılır: Metin dosyaları ve ikili dosyalar.

Bilgisayarların üzerinde işlem yapabildiği bu sayıların 0 ve 1 adlı iki sayı olduğunu biliyoruz.

Peki bu iki farklı sayıyı kullanarak neler yapabiliriz? Aslında, bu iki farklı sayıyı kullanarak her türlü işlemi yapabiliriz:
Basit veya karmaşık aritmetik hesaplamalar, metin düzenleme, resim veya video düzenleme, web siteleri hazırlama, uzaya mekik gönderme…
Bütün bu işlemleri sadece iki farklı sayı kullanarak yapabiliriz. Daha doğrusu bilgisayarlar yapabilir.

İşin aslı sadece tek bir dosya türü vardır: İkili dosyalar (binary files).
Yani bilgisayarlar açısından bütün dosyalar, içlerinde ne olursa olsun, birer ikili dosyadır ve içlerinde sadece 0’ları ve 1’leri barındırır.
İşte bu 0 ve 1’lerin ne anlama geleceğini, işletim sistemleri ve bu sistemler üzerine kurulu yazılımlar belirler.

Bir metin dosyası değil de ikili bir dosyayı açmak için:
f = open(dosya_adı, 'rb')

eğer ikili dosyayı 'rb' ile değil de 'r' ile açarsak bu ikili dosyanın bozulmasına sebep olabilir.


İkili Dosyalarla Örnekler

PDF Dosyalarından Bilgi Alma
Tıpkı resim, müzik ve video dosyaları gibi, PDF dosyaları da birer ikili dosyadır. 


f = open("falanca.pdf", "rb")

f.read(10)
>b'%PDF-1.3\n4'

PDF dosyasının ilk birkaç baytını okuyarak hem dosyanın bir PDF belgesi olduğunu teyit edebiliyoruz,
hem de bu PDF belgesinin, hangi PDF sürümü ile oluşturulduğunu anlayabiliyoruz.
Buna göre bu belge PDF talimatnamesinin 1.3 numaralı sürümü ile oluşturulmuş.

PDF belgelerinde, o belge hakkında bazı önemli bilgiler veren birtakım özel etiketler bulunur. Bu etiketler şunlardır:

/Creator
Belgeyi oluşturan yazılım

/Producer
Belgeyi PDF’e çeviren yazılım

/Title
Belgenin başlığı

/Author	
Belgenin yazarı

/Subject	
Belgenin konusu

/Keywords
Belgenin anahtar kelimeleri

/CreationDate	
Belgenin oluşturulma zamanı

/ModDate
Belgenin değiştirilme zamanı


















