Bu defa inceleyeceğimiz veri tipinin adı sözlük. İngilizcede buna dictionary diyorlar.


Sözlük Tanımlamak

kelimeler = {"kitap": "book"}

len(kelimeler)
>1

Yukarıdaki sözlüğü nasıl tanımladığımıza çok dikkat edin. Nasıl ki listelerin ayırt edici özelliği köşeli parantezlerdi, sözlüklerin ayırt edici özelliği de küme parantezleridir.

Esasında sözlük dediğimiz şey en basit haliyle şöyle görünür:
sözlük = {}
Bu örnek boş bir sözlüktür.
type(sözlük)
><class 'dict'>

kelimeler = {"kitap": "book", "bilgisayar": "computer"}
len(kelimeler)
>2


sözlük = {"kitap"      : "book",
          "bilgisayar" : "computer",
          "programlama": "programming",
          "dil"        : "language",
          "defter"     : "notebook"}


Sözlük Öğelerine Erişmek

print(sözlük["kitap"])
>book



çeviri_tablosu = {"Ö": "O",
                  "ç": "c",
                  "Ü": "U",
                  "Ç": "C",
                  "İ": "I",
                  "ı": "i",
                  "Ğ": "G",
                  "ö": "o",
                  "ş": "s",
                  "ü": "u",
                  "Ş": "S",
                  "ğ": "g"}



for i in çeviri_tablosu:
    print(çeviri_tablosu[i])


Sözlüklerin Yapısı


sözlük = {"kitap": "book"}

Sözlük içinde iki nokta üst üste işaretinin solunda ve sağında “kitap” ve “book” adlı karakter dizileri var.
Teknik olarak, iki nokta üst üste işaretinin solundaki karakter dizisine ‘anahtar’ (key), sağındaki karakter dizisine ise ‘değer’ (value) adı verilir.
Bu bilgilere bakarak sözlük için şöyle bir tanım verebiliriz:
Sözlükler; anahtar ve değer çiftlerinin birbirleriyle eşleştirildiği bir veri tipidir. Dolayısıyla sözlükler bu anahtar ve değer çiftleri arasında birebir ilişki kurar.


sözlük = {"sıfır": 0,
          "bir"  : 1,
          "iki"  : 2,
          "üç"   : 3,
          "dört" : 4,
          "beş"  : 5}


sözlük = {"Ahmet Özkoparan": ["İstanbul", "Öğretmen", 34],
          "Mehmet Yağız"   : ["Adana", "Mühendis", 40],
          "Seda Bayrak"    : ["İskenderun", "Doktor", 30]}




print(sözlük["Seda Bayrak"])
>['İskenderun', 'Doktor', 30]


kişiler = {"Ahmet Özkoparan": {"Memleket": "İstanbul",
                               "Meslek"  : "Öğretmen",
                               "Yaş"     : 34},

           "Mehmet Yağız"   : {"Memleket": "Adana",
                               "Meslek"  : "Mühendis",
                               "Yaş"     : 40},

           "Seda Bayrak"    : {"Memleket": "İskenderun",
                               "Meslek"  : "Doktor",
                               "Yaş"     : 30}}



print(kişiler["Mehmet Yağız"]["Memleket"])
print(kişiler["Seda Bayrak"]["Yaş"])
print(kişiler["Ahmet Özkoparan"]["Meslek"])



Sözlüklerin öteki veri tiplerinden önemli bir farkı, sözlük içinde yer alan öğelerin herhangi bir sıralama mantığına sahip olmamasıdır.
Yani sözlükteki öğeler açısından ‘sıra’ diye bir kavram yoktur.


Sözlüklere Öğe Eklemek
Tıpkı listeler gibi, sözlükler de büyüyüp küçülebilen bir veri tipidir.
Yani bir sözlüğü ilk kez tanımladıktan sonra istediğimiz zaman bu sözlüğe yeni öğeler ekleyebilir veya varolan öğeleri çıkarabiliriz.



Elimizde boş bir sözlük var:
sözlük = {}
Bu sözlüğe öğe eklemek için şöyle bir formül kullanacağız:
sözlük[anahtar] = değer

sözlük["Ahmet"] = "Adana"
print(sözlük)
>{'Ahmet': 'Adana'}

Bir sözlüğe değer olarak bütün veri tiplerini verebiliriz. Yani:

sözlük = {}
sözlük = {'a': 1}
sözlük = {'a': (1,2,3)}
sözlük = {'a': 'kardiz'}
sözlük = {'a': [1,2,3]}


Gördüğünüz gibi, sözlükler değer olarak her türlü veri tipini kabul ediyor. Ama durum sözlük anahtarları açısından böyle değildir.
Yani sözlüklere anahtar olarak her veri tipini atayamayız. Bir değerin ‘anahtar’ olabilmesi için, o öğenin değiştirilemeyen (immutable) bir veri tipi olması gerekir.
Python’da şimdiye kadar öğrendiğimiz şu veri tipleri değiştirilemeyen veri tipleridir:

gerekir. Python’da şimdiye kadar öğrendiğimiz şu veri tipleri değiştirilemeyen veri tipleridir:

    Demetler
    Sayılar
    Karakter Dizileri

Şu veri tipleri ise değiştirilebilen veri tipleridir:

Listeler
Sözlükler

Dolayısıyla bir sözlüğe anahtar olarak ancak şu veri tiplerini ekleyebiliriz:

    Demetler
    Sayılar
    Karakter Dizileri


Bu sözlüğe anahtar olarak bir demet ekleyelim:

l = (1,2,3)
sözlük[l] = 'falanca'
sözlük
>{(1, 2, 3): 'falanca'}

Bir sayı ekleyelim:

l = 45
sözlük[l] = 'falanca'
sözlük
>{45: 'falanca', (1, 2, 3): 'falanca'}

Bir karakter dizisi ekleyelim:

l = 'kardiz'
sözlük[l] = 'falanca'
sözlük
>{'kardiz': 'falanca', 45: 'falanca', (1, 2, 3): 'falanca'}

Yukarıdakiler, değiştirilemeyen veri tipleri olduğu için sözlüklere anahtar olarak eklenebildi.

Sözlük Öğeleri Üzerinde Değişiklik Yapmak

Sözlükler değiştirilebilir veri tipleridir. Dolayısıyla sözlükler üzerinde rahatlıkla istediğimiz değişikliği yapabiliriz.

Sözlük Üreteçleri (Dictionary Comprehensions)

harfler = 'abcçdefgğhıijklmnoöprsştuüvyz'

sözlük = {}
for i in harfler:
    sözlük[i] = harfler.index(i)

sözlük = {}
for i in range(len(harfler)):
    sözlük[harfler[i]] = i


İşte bu işlemleri sözlük üreteçlerini kullanarak çok daha hızlı ve pratik bir şekilde halledebiliriz. Dikkatlice bakın:

sözlük = {i: harfler.index(i) for i in harfler}



isimler = ["ahmet", "mehmet", "fırat", "zeynep", "selma", "abdullah", "cem"]
sözlük = {i: len(i) for i in isimler}
sözlük
























