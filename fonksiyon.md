Fonksiyon Nedir ve Ne İşe Yarar?

Fonksiyonların görevi, karmaşık işlemleri bir araya toplayarak, bu işlemleri tek adımda yapmamızı sağlamaktır.
Fonksiyonlar çoğu zaman, yapmak istediğimiz işlemler için bir şablon vazifesi görür. Fonksiyonları kullanarak,
bir veya birkaç adımdan oluşan işlemleri tek bir isim altında toplayabiliriz. Python’daki ‘fonksiyon’ kavramı 
başka programlama dillerinde ‘rutin’ veya ‘prosedür’ olarak adlandırılır. Gerçekten de fonksiyonlar rutin olarak
tekrar edilen görevleri veya prosedürleri tek bir ad/çatı altında toplayan araçlardır.


Fonksiyon Tanımlamak ve Çağırmak


def kayıt_oluştur(isim, soyisim, işsis, şehir):
    print("-"*30)

    print("isim           : ", isim)
    print("soyisim        : ", soyisim)
    print("işletim sistemi: ", işsis)
    print("şehir          : ", şehir)

    print("-"*30)


kayıt_oluştur("Kerem", "Akdeniz", "Ubuntu", "Kütahya")




Bu yapının ilk parçası şudur:
def kayıt_oluştur(parametre1, parametre2, parametre3, parametre4):
    (...)

İkinci parçası ise şu:

kayıt_oluştur(parametre1, parametre2, parametre3, parametre4)


ilk parçaya ‘fonksiyon tanımı’ (function definition),
ikinci parçaya ise ‘fonksiyon çağrısı’ (function call) adı verilir. 


Bu derse gelinceye kadar öğrendiğimiz print(), type() ve open() gibi fonksiyonlara teknik olarak ‘gömülü fonksiyonlar’ (builtin functions) adı verilir.

Fonksiyonların Yapısı


def selamla():
    print("Elveda Zalim Dünya!")


Python’da kabaca iki tip fonksiyon bulunur. Bunlardan biri gömülü fonksiyonlar (builtin functions), öteki ise özel fonksiyonlardır (custom functions). 


def sistem_bilgisi_göster():
    import sys
    print("\nSistemde kurulu Python'ın;")
    print("\tana sürüm numarası:", sys.version_info.major)
    print("\talt sürüm numarası:", sys.version_info.minor)
    print("\tminik sürüm numarası:", sys.version_info.micro)

    print("\nKullanılan işletim sisteminin;")
    print("\tadı:", sys.platform)
    
version_info.major: Python’ın ana sürüm numarası (Örn. 3)

version_info.minor: Python’ın alt sürüm numarası (Örn. 4)

version_info.micro: Python’ın minik sürüm numarası (Örn. 0)

platform: Kullanılan işletim sisteminin adı (Örn. ‘win32’ veya ‘linux2’)



Fonksiyonlar Ne İşe Yarar?

def kare_bul():
    sayı = 12
    çıktı = "{} sayısının karesi {} sayısıdır"
    print(çıktı.format(sayı, sayı**2))
    
def kare_bul(sayı):
    çıktı = "{} sayısının karesi {} sayısıdır"
    print(çıktı.format(sayı, sayı**2))



Bir fonksiyonu tanımlarken belirlediğimiz adlara parametre, aynı fonksiyonu çağırırken belirlediğimiz adlara ise argüman deniyor.

Sıralı (veya İsimsiz) Parametreler


İsimli Parametreler



kayıt_oluştur(soyisim="Öz", isim="Ahmet", işsis="Debian", şehir= "Ankara")

Biz kendimiz varsayılan değerli parametreler içeren fonksiyonları nasıl tanımlayabiliriz?


def kur(kurulum_dizini="/usr/bin/"):
    print("Program {} dizinine kuruldu!".format(kurulum_dizini))


Eğer isterseniz kullanıcılarınızı bir kurulum dizini belirlemeye zorlamak da isteyebilirsiniz. Bunun için yine varsayılan değerli parametrelerden yararlanabilirsiniz:

def kur(kurulum_dizini=''):
    if not kurulum_dizini:
        print("Lütfen programı hangi dizine kurmak istediğinizi belirtin!")
    else:
        print("Program {} dizinine kuruldu!".format(kurulum_dizini))



Özellikle programların kurulmasını sağlayan ‘setup’ betiklerinde her aşama için bir varsayılan değer belirlenip,
kullanıcının sadece ‘Next’ tuşlarına basarak sağlıklı bir kurulum yapması sağlanabiliyor.
Eğer kullanıcı varsayılan değerlerin dışında birtakım değerler belirlemek isterse, yukarıda örneğini verdiğimiz yapı kullanıcıya böyle bir özgürlük de sağlıyor.


Rastgele Sayıda İsimsiz Parametre Belirleme

def fonksiyon(*parametreler):
    print(parametreler)

fonksiyon(1, 2, 3, 4, 5)
>(1, 2, 3, 4, 5)


def çarp(*sayılar):
    sonuç = 1
    for i in sayılar:
        sonuç *= i
    print(sonuç)


* işareti herhangi bir öğeyi alıp, bunu parçalarına ayırıyor.


def fonksiyon(*args):
    ...

Rastgele Sayıda İsimli Parametre Belirleme


def fonksiyon(**parametreler):
    print(parametreler)

fonksiyon(isim="Ahmet", soyisim="Öz", meslek="Mühendis", şehir="Ankara")
>{'isim': 'Ahmet', 'soyisim': 'Öz', 'meslek': 'Mühendis', 'şehir': 'Ankara'}


def kayıt_oluştur(**bilgiler):
    print("-"*30)

    for anahtar, değer in bilgiler.items():
        print("{:<10}: {}".format(anahtar, değer))

    print("-"*30)

kayıt_oluştur(ad="Fırat", soyad="Özgül", şehir="İstanbul", tel="05333213232")


Tıpkı * işaretlerinin betimlediği parametrenin geleneksel olarak ‘args’ şeklinde adlandırılması gibi, 
** işaretlerinin betimlediği parametre de geleneksel olarak ‘kwargs’ şeklinde adlandırılır.
Dolayısıyla yukarıdaki gibi bir fonksiyonu Python programcıları şöyle tanımlar:


def kayıt_oluştur(**kwargs):
    ...


return Deyimi

def ismin_ne():
    isim = input("ismin ne? ")
    return isim

print("Merhaba {}. Nasılsın?".format(ismin_ne()))
>ismin ne? kerem Merhaba kerem. Nasılsın?

Bu deyim, içinde bulunduğu fonksiyonun çalışma sürecini kesintiye uğratır. Yani return deyimini kullandığınız satırdan sonra gelen hiçbir kod çalışmaz.




import random

dir(random)
['BPF', 'LOG4', 'NV_MAGICCONST', 'RECIP_BPF', 'Random',
'SG_MAGICCONST', 'SystemRandom', 'TWOPI', '_BuiltinMethodType',
'_MethodType', '_Sequence', '_Set', '__all__', '__builtins__',
'__cached__', '__doc__', '__file__', '__initializing__',
'__loader__', '__name__', '__package__', '_acos', '_ceil',
'_cos', '_e', '_exp', '_inst', '_log', '_pi', '_random', '_sha512',
'_sin', '_sqrt', '_test', '_test_generator', '_urandom', '_warn',
'betavariate', 'choice', 'expovariate', 'gammavariate', 'gauss',
'getrandbits', 'getstate', 'lognormvariate', 'normalvariate',
'paretovariate', 'randint', 'random', 'randrange', 'sample',
'seed', 'setstate', 'shuffle', 'triangular', 'uniform',
'vonmisesvariate', 'weibullvariate']


liste = ["ahmet", "mehmet", "sevgi", "sevim", "selin", "zeynep", "selim"]
random.sample(liste, 2)
>['sevim', 'ahmet']


random modülü içinde bulunan shuffle() adlı başka bir fonksiyon, bir dizi içindeki öğelerin sırasını rastgele bir şekilde karıştırmamızı sağlar



Fonksiyonların Kapsamı ve global Deyimi

x = 0

def fonk():
    x = 1
    return x

print('fonksiyon içindeki x: ', fonk())
print('fonksiyon dışındaki x: ', x)

>fonksiyon içindeki x:  1
fonksiyon dışındaki x:  0

Gördüğünüz gibi fonksiyon içindeki ve fonksiyon dışındaki aynı adlı değişkenler birbirine karışmıyor. Bunun sebebi, Python’daki ‘isim alanı’ (namespace) adlı bir kavramdır.




Peki isim alanı ne demek?

Python’da değişkenlerin, fonksiyonların ve daha sonra göreceğiniz gibi sınıfların bir kapsamı vardır.
Bu kapsama Python’da ‘isim alanı’ adı verilir. Dolayısıyla Python’da her nesnenin, geçerli ve etkin olduğu bir isim alanı bulunur.
Örneğin yukarıdaki kodlarda fonksiyon dışındaki x değişkeni ana isim alanında yer alan ‘global’ bir değişkendir.
Fonksiyon içindeki x değişkeni ise fonk() değişkeninin isim alanı içinde yer alan ‘lokal’ bir değişkendir.
Bu iki değişken, adları aynı da olsa, birbirlerinden farklı iki nesnedir.



x = []
print('x\'in ilk hali:', x)

def değiştir():
    print('x\'i değiştiriyoruz...')
    x.append(1)
    return x

değiştir()
print('x\'in son hali: ', x)
>[1]

Python herhangi bir nesneye göndermede bulunduğumuzda,
yani o nesnenin değerini talep ettiğimizde aradığımız nesneyi ilk önce mevcut isim alanı içinde arar.
Eğer aranan nesneyi mevcut isim alanı içinde bulamazsa yukarıya doğru bütün isim alanlarını tek tek kontrol eder.


x = 0

def fonk():
    print(x)

fonk()
>0

Yukarıdaki örnekte, biz print() ile x’in değerini sorguladığımızda
Python öncelikle fonk() adlı fonksiyonun isim alanına baktı. 
Orada x’i bulamayınca bu kez global alana yönelip, orada bulduğu x’in değerini yazdırdı.


Eğer bir nesne değiştirilebilir bir nesne ise, o nesnenin değerini, lokal isim alanlarından değiştirebilirsiniz:

isim = 'Fırat'

def fonk():
    isim += ' Özgül'
    return isim

print(fonk())

Hata verir

isim = 'Fırat'

def fonk():
    isim += ' Özgül'
    return isim

print(fonk())

Hata verir

isim = 'Fırat'

def fonk():
    global isim
    isim += ' Özgül'
    return isim

print(fonk())
>Fırat Özgül

İşte bu satır, isim adlı değişkenin global alana taşınmasını sağlıyor. Böylece global alanda bulunan isim adlı değişkeni değişikliğe uğratabiliyoruz.
global deyimi her ne kadar ilk bakışta çok faydalı bir araçmış gibi görünse de 
aslında programlarımızda genellikle bu deyimi kullanmaktan kaçınmamız iyi bir fikir olacaktır.
Çünkü bu deyim aslında global alanı kirletmemize neden oluyor. Global değişkenlerin lokal isim alanlarında değişikliğe uğratılması,
eğer dikkatsiz davranırsanız programlarınızın hatalı çalışmasına yol açabilir.














