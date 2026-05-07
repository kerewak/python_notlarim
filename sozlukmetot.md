Sözlüklerin Metotları

keys()
values()
items()
get()
clear()
copy()
fromkeys()
pop()
popitem()
setdefault()
update()




keys()

Eğer bir sözlüğün sadece anahtarlarını almak isterseniz keys() metodundan yararlanabilirsiniz:

sözlük = {"a": 0,
          "b": 1,
          "c": 2,
          "d": 3}
print(sözlük.keys())
>dict_keys(['a', 'b', 'c', 'd'])


liste = list(sözlük.keys())
liste
>['a', 'b', 'c', 'd']



demet = tuple(sözlük.keys())
demet
>('a', 'b', 'c', 'd')


kardiz = "".join(sözlük.keys())
kardiz

>'abcd'


values()

keys() metodu bir sözlüğün anahtarlarını veriyor. Bir sözlüğün değerlerini ise values() metodu verir:

sözlük
>{'a': 0, 'b': 1, 'c': 2, 'd': 3}

print(sözlük.values())
>dict_values([0, 1, 2, 3])

liste = list(sözlük.values())
liste
>[0, 1, 2, 3]

demet = tuple(sözlük.values())
demet
(0, 1, 2, 3)


kardiz = "".join(sözlük.values())
>
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: sequence item 0: expected str instance, int found

Bunun sebebi, sözlükteki değerlerin int tipinde olmasıdır. Bildiğiniz gibi, sadece aynı tip verileri birbiriyle birleştirebiliriz.
Eğer birleştirmek istediğimiz veriler birbirinden farklı tipte ise, bunları birleştirmeden önce bir dönüştürme işlemi yapmamız gerekir:

kardiz = "".join([str(i) for i in sözlük.values()])
kardiz
>'0123'

Elbette eğer isteseydik bu öğelerin her birinin arasına bir virgül de koyabilirdik:

kardiz = ", ".join([str(i) for i in sözlük.values()])
kardiz
>'0, 1, 2, 3'


items()
Bu metot, bir sözlüğün hem anahtarlarını hem de değerlerini aynı anda almamızı sağlar:


sözlük.items()
>dict_items([('a', 0), ('b', 1), ('c', 2), ('d', 3)])

Gördüğünüz gibi, tek bir liste içinde iki öğeli demetler halinde hem anahtarları hem de değerleri görebiliyoruz.
Bu metot sıklıkla for döngüleri ile birlikte kullanılarak bir sözlüğün anahtar ve değerlerinin manipüle edilebilmesini sağlar:

for anahtar, değer in sözlük.items():
    print("{} = {}".format(anahtar, değer))

>a = 0
b = 1
c = 2
d = 3


get()

Bu metot sözlüklerin en kullanışlı metotlarından biridir. Bu metot pek çok durumda işinizi bir hayli kolaylaştırır.

#!/usr/bin/env python3.0
ing_sözlük = {"dil": "language", "bilgisayar": "computer", "masa": "table"}
sorgu = input("Lütfen anlamını öğrenmek istediğiniz kelimeyi yazınız:")
print(ing_sözlük[sorgu])

ing_sözlük = {"dil": "language", "bilgisayar": "computer", "masa": "table"}
sorgu = input("Lütfen anlamını öğrenmek istediğiniz kelimeyi yazınız:")
if sorgu not in ing_sözlük:
    print("Bu kelime veritabanımızda yoktur!")
else:
    print(ing_sözlük[sorgu])


Ama açıkçası bu pek verimli bir yaklaşım sayılmaz. Yukarıdaki yöntem yerine sözlüklerin get() metodundan faydalanabiliriz. Bakalım bunu nasıl yapıyoruz:

ing_sözlük = {"dil": "language", "bilgisayar": "computer", "masa": "table"}
sorgu = input("Lütfen anlamını öğrenmek istediğiniz kelimeyi yazınız:")
print(ing_sözlük.get(sorgu, "Bu kelime veritabanımızda yoktur!"))


Sözlüklerin get() adlı metodu, parantez içinde iki adet argüman alır. Birinci argüman sorgulamak istediğimiz sözlük öğesidir.
İkinci argüman ise bu öğenin sözlükte bulunmadığı durumda kullanıcıya hangi mesajın gösterileceğini belirtir. 
Buna göre, yukarıda yaptığımız şey, önce “sorgu” değişkenini sözlükte aramak, eğer bu öğe sözlükte bulunamıyorsa da kullanıcıya,
“Bu kelime veritabanımızda yoktur!” cümlesini göstermekten ibarettir…


#!/usr/bin/env python3
soru = input("Şehrinizin adını tamamı küçük harf olacak şekilde yazın:")
if soru == "istanbul":
    print("gök gürültülü ve sağanak yağışlı")
elif soru == "ankara":
    print("açık ve güneşli")
elif soru == "izmir":
    print("bulutlu")
else:
    print("Bu şehre ilişkin havadurumu bilgisi bulunmamaktadır.")


Yukarıdaki, gayet geçerli bir yöntemdir. Ama biz istersek bu kodları “get” metodu yardımıyla çok daha verimli ve sade bir hale getirebiliriz:


#!/usr/bin/env python3
soru = input("Şehrinizin adını tamamı küçük harf olacak şekilde yazın:")
cevap = {"istanbul": "gök gürültülü ve sağanak yağışlı",
         "ankara": "açık ve güneşli", "izmir": "bulutlu"}
print(cevap.get(soru, "Bu şehre ilişkin havadurumu bilgisi bulunmamaktadır."))



clear()

Bu kelime İngilizce’de “temizlemek” anlamına gelir. Görevi sözlükteki öğeleri temizlemektir.
Yani içi dolu bir sözlüğü bu metot yardımıyla tamamen boşaltabiliriz:

lig = {"şampiyon": "Adana Demirspor", "ikinci": "Mersin İdman Yurdu",
... "üçüncü": "Adana Gençlerbirliği"}

lig.clear()

lig
>{}


Boş da olsa bellekte "lig" isimli sözlük bulunmaktadır.
Eğer siz “lig”i ortadan kaldırmak isterseniz “del” adlı bir parçacıktan yararlanmanız gerekir:


del lig
lig
>NameError: name 'lig' is not defined


copy()

Diyelim ki elimizde şöyle bir sözlük var:

hava_durumu = {"İstanbul": "yağmurlu", "Adana": "güneşli", ... "İzmir": "bulutlu"}

Biz bu sözlüğü kopyalamak istiyoruz. Hemen şöyle bir şey deneyelim:

yedek_hava_durumu = hava_durumu

Artık elimizde aynı sözlükten iki tane var:
hava_durumu
>{'İstanbul': 'yağmurlu', 'Adana': 'güneşli', 'İzmir': 'bulutlu'}

yedek_hava_durumu
>{'İstanbul': 'yağmurlu', 'Adana': 'güneşli', 'İzmir': 'bulutlu'}

Şimdi hava_durumu adlı sözlüğe bir öğe ekleyelim:

hava_durumu["Mersin"] = "sisli"

hava_durumu
>{'İstanbul': 'yağmurlu', 'Adana': 'güneşli', 'İzmir': 'bulutlu', 'Mersin': 'sisli'}

Şimdi bir de yedek_hava_durumu adlı sözlüğün durumuna bakalım:

yedek_hava_durumu
>{'İstanbul': 'yağmurlu', 'Adana': 'güneşli', 'İzmir': 'bulutlu', 'Mersin': 'sisli'}

Gördüğünüz gibi, hava_durumu adlı sözlüğe yaptığımız ekleme yedek_hava_durumu adlı sözlüğü de etkiledi. 

Eğer istediğimiz şey bellekteki nesneden iki adet oluşturmak ve bu iki farklı nesneyi iki farklı isimle adlandırmak ise yukarıdaki yöntemi kullanmak istemediğiniz sonuçlar doğurabilir. 
Yani amacınız bir sözlüğü yedekleyip orijinal sözlüğü korumaksa ve yukarıdaki yöntemi kullandıysanız, hiç farkında olmadan orijinal sözlüğü de değiştirebilirsiniz. 
İşte böyle durumlarda imdadımıza sözlüklerin “copy” metodu yetişecek. Bu metodu kullanarak varolan bir sözlüğü gerçek anlamda kopyalayabilir, yani yedekleyebiliriz…

hava_durumu = {"İstanbul": "yağmurlu", "Adana": "güneşli", ... "İzmir": "bulutlu"}

yedek_hava_durumu = hava_durumu.copy()

hava_durumu["Mersin"] = "sisli"
hava_durumu
>{'İstanbul': 'yağmurlu', 'Adana': 'güneşli', 'İzmir': 'bulutlu', 'Mersin': 'sisli'}

yedek_hava_durumu adlı sözlüğe bakalım:

yedek_hava_durumu
>{'İstanbul': 'yağmurlu', 'Adana': 'güneşli', 'İzmir': 'bulutlu'}


fromkeys()

fromkeys()’in görevi yeni bir sözlük oluşturmaktır. Bu metot yeni bir sözlük oluştururken listeler veya demetlerden yararlanır. Şöyle ki:

elemanlar = "Ahmet", "Mehmet", "Can"
adresler = dict.fromkeys(elemanlar, "Kadıköy")
adresler
{'Ahmet': 'Kadıköy', 'Mehmet': 'Kadıköy', 'Can': 'Kadıköy'}


Gördüğünüz gibi öncelikle “elemanlar” adlı bir demet tanımladık. Daha sonra da “adresler” adlı bir sözlük tanımlayarak,
fromkeys() metodu yardımıyla anahtar olarak “elemanlar” demetindeki öğelerden oluşan, değer olarak ise “Kadıköy”ü içeren bir sözlük meydana getirdik.
En başta tanımladığımız “elemanlar” demeti liste de olabilirdi. Hatta tek başına bir karakter dizisi dahi yazabilirdik oraya…


pop()
pop metodunu argümansız bir şekilde kullanamıyoruz. Yani pop metodunun parantezi içinde mutlaka bir sözlük öğesi belirtmeliyiz:

sepet = {"meyveler": ("elma", "armut"), "sebzeler": ("pırasa", "fasulye"),
"içecekler": ("su", "kola", "ayran")}

sepet.pop("meyveler")
>('elma', 'armut')

Eğer silmeye çalıştığımız anahtar sözlükte yoksa Python bize bir hata mesajı gösterecektir:
sepet.pop("tatlılar")
>KeyError: 'tatlılar'

Bir program yazarken böyle bir durumla karşılaşmak istemeyiz çoğu zaman. Yani bir sözlük içinde arama yaparken,
aranan öğenin sözlükte bulunmadığı bir durumda kullanıcıya mekanik ve anlamsız bir hata göstermek yerine,
daha anlaşılır bir mesaj iletmeyi tercih edebiliriz. Hatırlarsanız sözlüklerin get() metodunu kullanarak benzer bir şey yapabiliyorduk. 
Şu anda incelemekte olduğumuz pop() metodu da bize böyle bir imkan verir. Bakalım:

sepet.pop("tatlılar", "Silinecek öğe yok!")


popitem()
popitem() metodu da bir önceki bölümde öğrendiğimiz pop() metoduna benzer. Bu iki metodun görevleri hemen hemen aynıdır.
Ancak pop() metodu parantez içinde bir parametre alırken, popitem() metodunun parantezi boş, yani parametresiz olarak kullanılır. 
Bu metot bir sözlükten son eklenen öğeyi silmek için kullanılır(Python 3.7’den önceki sürümlerde bunun yerine rastgele bir öğe kaldırılır)…


sepet = {"meyveler": ("elma", "armut"), "sebzeler": ("pırasa", "fasulye")}
sepet.popitem()
>('sebzeler', ('pırasa', 'fasulye'))


setdefault()

sepet = {"meyveler": ("elma", "armut"), "sebzeler": ("pırasa", "fasulye")}
sepet.setdefault("içecekler", ("su", "kola"))
>('su', 'kola')

sepet.setdefault("meyveler", ("erik", "çilek"))
>('elma', 'armut')


update()
İnceleyeceğimiz son metot update() metodu… Bu metot yardımıyla oluşturduğumuz sözlükleri yeni verilerle güncelleyeceğiz. Diyelim ki elimizde şöyle bir sözlük var:

stok = {"elma": 5, "armut": 10, "peynir": 6, "sosis": 15}

yeni_stok = {"elma": 3, "armut": 20, "peynir": 8, "sosis": 4, "sucuk": 6}

Yapmamız gereken şey, stoğumuzu yeni bilgilere göre güncellemek olacaktır. İşte bu işlemi update() metodu ile yapabiliriz:

stok.update(yeni_stok)
print(stok)
>{'peynir': 8, 'elma': 3, 'sucuk': 6, 'sosis': 4, 'armut': 20}

Böylelikle malların son miktarlarına göre stok bilgilerimizi güncellemiş olduk…
































