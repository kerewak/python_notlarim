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



f = open("falanca.pdf", "rb")
okunan = f.read()
producer_index = okunan.index(b"/Producer")

chr(okunan[producer_index])
>'/'

okunan[producer_index:producer_index+50]
>b'/Producer (Acrobat Distiller 2.0 for Macintosh)\r/T'


Resim Dosyalarının Türünü Tespit Etme

Asla unutmayın dosya uzantıları ile dosya biçimleri arasında doğrudan bir bağlantı yoktur. O yüzden dosya uzantıları, dosya biçimini anlamak açısından güvenilir bir yöntem değildir. 



JPEG
https://jpeg.org/

bir JPEG dosyasının en başında şu veriler bulunur:

FF  D8      FF      E0      ?   ?   4A      46      49      46      00


Ancak eğer ilgili JPEG dosyası bir CANON fotograf makinesi ile oluşturulmuşsa bu veri dizisi şöyle de olabilir:
FF  D8      FF      E0      ?   ?   45  78  69  66  00

255 216 255 224 ? ? 74 70 73 70 0
255 216 255 224 ? ? 45 78 69 66 0 #canon
Bu diziler içinde özellikle şu dört sayı bizi yakından ilgilendiriyor:

74 70 73 70
45 78 69 66 #canon
Bu sayılar sırasıyla ‘J’, ‘F’, ‘I’, ‘F’ ve ‘E’, ‘x’, ‘i’, ‘f’ harflerine karşılık gelir. Yani bir JPEG dosyasını ayırt edebilmek için ilgili dosyanın 7-10 arası baytlarının ne olduğuna bakmamız yeterli olacaktır. Eğer bu aralıkta ‘JFIF’ veya ‘Exif’ ifadeleri varsa, o dosya bir JPEG dosyasıdır. Buna göre şöyle bir kod yazabiliriz:

f = open(dosya_adı, 'rb')
data = f.read(10)
if data[6:11] in [b"JFIF", b"Exif"]:
    print("Bu dosya JPEG!")
else:
    print("Bu dosya JPEG değil!")


PNG
http://www.libpng.org/pub/png/spec/

bir PNG dosyasının ilk 8 baytı mutlaka aşağıdaki değerleri içeriyor:

onlu değer
137 80 78 71 13 10 26 10

on altılı değer
89 50 4e 47 0d 0a 1a 0a

karakter değeri
\211 P N G \r \n \032 \n


GIF
https://www.w3.org/Graphics/GIF/spec-gif89a.txt 

Bir dosyanın GIF olup olmadığına karar verebilmek için ilk 3 baytını okumanız yeterli olacaktır. Standart bir GIF dosyasının ilk üç baytı ‘G’, ‘I’ ve ‘F’ karakterlerinden oluşur. Dosyanın sonraki 3 baytı ise GIF’in sürüm numarasını verir. 11.02.2025 itibariyle GIF standardının şu sürümleri bulunmaktadır:

        87a - Mayıs 1987

        89a - Temmuz 1989

TIFF
https://www.itu.int/itudoc/itu-t/com16/tiff-fx/docs/tiff6.pdf
Bu şartnameye göre bir TIFF dosyası şunlardan herhangi biri ile başlar:

        ‘II’

        ‘MM’

BMP
https://www.loc.gov/preservation/digital/formats/fdd/fdd000189.shtml 
Buna göre, BMP dosyaları ‘BM’ ile başlar.











