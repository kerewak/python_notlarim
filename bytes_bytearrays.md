İnceleyeceğimiz veri tipleri bytes ve bytearrays.
Bilgisayar açısından 'karakter' soyut bir kavramdır. 
Karakter dediğimiz şey, bilgisayarların anlayabildiği tek kavram olan sayılara biz insanların atadığı birtakım işaretlerden ibarettir.
Dolayısıyla bilgisayarlar açısından karakterler değil, ikili sayma düzenindeki birtakım sayılar, yani bitler ve baytlar vardır.
1 bit, ikili sayma sistemindeki her bir basamağa verilen isimdir.
Zaten ‘bit’ kelimesinin de İngilizcede ‘ikili basamak’ anlamına gelen ‘binary digit ifadesinin kısaltmasıdır

Örneğin ikili sayma sistemindeki 0, bir bitlik bir sayı iken, 100 üç bitlik bir sayıdır.
Bu bit’lerin 8 tanesi bir araya gelince ‘bayt’ denen birimi oluşturur. Yani bayt, 8 adet bit’ten oluşan bir birimdir.

UTF-8, değişken boyutlu bir kodlama sistemidir, duruma göre 4 bayta kadar kullanabilir.
UTF-32 adlı kod çözücü hangi karakter olursa olsun hepsini 4 bayt (32 bit) ile temsil eder.
UTF-8’in bu kadar yaygın ve gözde olmasının nedeni de hem çok sayıda karakteri kodlayabilmesi, hem de bu işi yaparken tasarruflu olmayı başarabilmesidir.


Python programlama dilinde karakter dizileri UNICODE kod konumları şeklinde temsil edilir.
Dolayısıyla str adı verilen veri tipi esasında karakter dizilerini birtakım UNICODE kod konumları şeklinde gösteren soyut bir yapıdır. 
Yani biz Python’da karakter dizileri üzerinde işlem yaparken aslında baytlarla değil, UNICODE kod konumları ile muhatap oluyoruz.
Ancak UNICODE kod konumları da tamamen soyut kavramlardır.
Bunları bilgisayarın belleğinde bu şekilde temsil edemezsiniz ya da bu kod konumlarını herhangi bir ağ üzerinden başka bilgisayarlara iletemezsiniz.
Bu kod konumlarını anlamlı bir şekilde kullanabilmek için öncelikle bunları bilgisayarların anlayabileceği bir biçim olan baytlara çevirmeniz gerekir.
Çünkü dediğimiz gibi bilgisayarlar yalnızca bitler ve baytlardan anlar. İşte kod çözücülerin görevi de zaten bu kod konumlarını baytlara çevirmektir.


Python’ın 2.x sürümlerinde, bir karakter dizisi tanımladığınızda Python bu karakter dizisini bir bayt dizisi olarak temsil ediyordu. Örneğin:
kardiz = "e"
kardiz = "e"
>1
kardiz = "ş"

Kullandığınız işletim sisteminde öntanımlı kod çözücünün hangisi olduğunu şu komutla bulabilirsiniz:
import locale
locale.getpreferredencoding()

Python2 de:
"ş"[0]
>'\xc5'



Python3 ile birlikte yukarıda bahsettiğimiz durumda bazı değişiklikler oldu.
Artık str veri tipi UNICODE kod konumlarını döndürüyor. Dolayısıyla artık her karakter dizisi, sahip oldukları karakter sayısına göre sayılabiliyor:
len("ş")
>1

İşte eğer Python2’deki str veri tipini elde etmek istiyorsanız, Python3’te bytes adlı yeni veri tipini kullanmanız gerekiyor.

boş bir bayt tanımlamak için:
bayt = b''
type(bayt)
><class 'bytes'>


bytes() Fonksiyonu
Bayt veri tipi temel olarak ASCII karakterleri kabul eder. Dolayısıyla ASCII tablosu dışında kalan karakterleri doğrudan bayt olarak temsil edemezsiniz.

b'ş'
>
  File "<stdin>", line 1
SyntaxError: bytes can only contain ASCII literal characters.


Ama ASCII dışında kalan karakterleri de bayt’a dönüştürmenin bir yolu var. Bunun için bytes() adlı bir fonksiyondan yararlanacağız:
b = bytes("ş", "utf-8")

Tahmin edebileceğiniz gibi, bytes() fonksiyonu, belirttiğimiz kod çözücü ile kodlanamayan karakterlerle karşılaşılması durumunda 
ne yapılacağını belirlememizi sağlayan errors adlı bir parametreye de sahiptir:

b = bytes("Fırat", "ascii", errors="xmlcharrefreplace")
b
>b'F&#305;rat'

Baytların Metotları

Bütün veri tiplerinde olduğu gibi, bytes adlı veri tipinin de birtakım metotları bulunur. Bu metotların listesini almak için şu komutu kullanabileceğinizi biliyorsunuz:

dir(bytes)


Listeye baktığınızda bu metotları karakter dizilerinin metotları ile hemen hemen aynı olduğunu göreceksiniz.
Baytların metotları arasında olup da karakter dizilerinin metotları arasında olmayan metotları şu şekilde elde edebilirsiniz:

for i in dir(bytes):
    if i not in dir(str):
        print(i)
>decode
fromhex



decode

"İ".encode("utf-8")
>b'\xc4\xb0'

İşte bu kodlama işlemini tersine çevirebilmek, yani baytları belli bir kodlama biçimine göre karakter dizilerine dönüştürebilmek için decode() metodundan yararlanacağız:
b"\xc4\xb0".decode("utf-8")
>'İ'


Bu baytları bir de başka kodlama sistemleri ile kodlamayı deneyelim:
b"\xc4\xb0".decode("cp1254")
>'Ä°'
Gördüğünüz gibi, cp1254 adlı kod çözücü bu baytı çözebiliyor, ama yanlış çözüyor! Çünkü bu baytın gösterdiği sayı cp1254 adlı kod sayfasında ‘İ’ye değil,
> başka bir karaktere karşılık geliyor. Aslında başka iki karaktere, yani C4 ve B0 ile gösterilen Ä ve ° karakterlerine karşılık geliyor…


b"\xc4\xb0".decode("ascii")

>
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc4 in position 0: ordinal
not in range(128)


fromhex

Bu metot, onaltılı sayma sistemindeki bir sayıdan oluşan bir karakter dizisini alıp, bayta dönüştürür. Bu metodu şöyle kullanıyoruz:
bytes.fromhex("c4b0")
>b'\xc4\xb0'



Bayt Dizileri
bytes adlı veri tipi ile elde ettiğimiz veri tıpkı karakter dizileri gibi, üzerinde değişiklik yapılamayan bir veridir. 
Dolayısıyla bir bytes nesnesi üzerinde değişiklik yapabilmek için o nesneyi tekrar tanımlamamız gerekir:

b = b'PDF'
v = b'-1.7'
b = b + v
b
>b'PDF-1.7'


Ama Python programlama dilinde bytes veri tipi dışında, baytlara ilişkin ikinci veri tipi daha bulunur. 
bytearray adlı bu veri tipi, bytes veri tipinin aksine, üzerinde değişiklik yapılabilen bir veri tipidir.

pdf = bytearray(b'PDF-1.7')


Bayt Dizilerinin Metotları

Bayt dizileri bir bakıma listelerle baytların karışımı gibidir. dir(bytearray) gibi bir komutla bu veri tipinin metotlarını inceleyecek olursanız, bu veri tipinin hem baytlardan hem de listelerden birtakım metotlar aldığını görürsünüz.

Bu veri tipi listelerin şu metotlarına sahiptir:
append
clear
copy
count
extend
index
insert
pop
remove
reverse

Bu veri tipi baytların ise şu metotlarına sahiptir:
capitalize
center
count
decode
endswith
expandtabs
find
fromhex
index
isalnum
isalpha
isdigit
islower
isspace
istitle
isupper
join
ljust
lower
lstrip
maketrans
partition
replace
rfind
rindex
rjust
rpartition
rsplit
rstrip
split
splitlines
startswith
strip
swapcase
title
translate
upper
zfill


































