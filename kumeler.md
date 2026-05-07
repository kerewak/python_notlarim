Kümeler ve Dondurulmuş Kümeler

Kümeler

Adından da az çok tahmin edebileceğiniz gibi kümeler, matematikten bildiğimiz “küme” kavramıyla sıkı sıkıya bağlantılıdır.
Bu veri tipi, matematikteki kümelerin sahip olduğu bütün özellikleri taşır.
Yani matematikteki kümelerden bildiğimiz kesişim, birleşim ve fark gibi özellikler Python’daki kümeler için de geçerlidir.


Küme Oluşturmak

Örneğin boş bir kümeyi şöyle oluşturuyoruz:
>boş_küme = set()

küme = set(["elma", "armut", "kebap"])

Dikkat ederseniz, küme oluştururken listelerden faydalandık.
Gördüğünüz gibi set() fonksiyonu içindeki öğeler bir liste içinde yer alıyor.
Dolayısıyla yukarıdaki tanımlamayı şöyle de yapabiliriz:


liste = ["elma", "armut", "kebap"]
küme = set(liste)



Bu daha temiz bir görüntü oldu. Elbette küme tanımlamak için mutlaka liste kullanmak zorunda değiliz. İstersek demetleri de küme haline getirebiliriz:

demet = ("elma", "armut", "kebap")
küme = set(demet)

Hatta ve hatta karakter dizilerinden dahi küme yapabiliriz:
kardiz = "Python Programlama Dili için Türkçe Kaynak"
küme = set(kardiz)

kardiz = "a"
küme = set(kardiz)

Ama sayılardan küme oluşturamayız:
n = 10
küme = set(n)
>TypeError: 'int' object is not iterable


bilgi = {"işletim sistemi": "GNU", "sistem çekirdeği": "Linux",
"dağıtım": "Ubuntu GNU/Linux"}

küme = set(bilgi)

küme = {'Python', 'C++', 'Ruby', 'PHP'}
type(küme)
><class 'set'>

Bu arada, bir sözlüğü kümeye çevirdiğinizde, elbette sözlüğün yalnızca anahtarları kümeye eklenecektir. Sözlüğün değerleri ise böyle bir işlemin sonucunda ortadan kaybolur.

bilgi = {"işletim sistemi": "GNU", "sistem çekirdeği": "Linux",
"dağıtım": "Ubuntu GNU/Linux"}

Bu sözlükteki anahtar-değer çiftlerini bir küme içine, çift öğeli demetler olarak yerleştirebiliriz:

liste = [(anahtar, değer) for anahtar, değer in bilgi.items()]
küme = set(liste)
>{('işletim sistemi', 'GNU'), ('dağıtım', 'Ubuntu GNU/Linux'), ('sistem çekirdeği', 'Linux')}

Bu sözlükteki anahtar-değer çiftlerini bir küme içine, çift öğeli demetler olarak yerleştirebiliriz:

liste = [(anahtar, değer) for anahtar, değer in bilgi.items()]
küme = set(liste)

Gördüğünüz gibi, liste üreteçlerini kullanarak önce bir liste oluşturuyoruz.
Bu liste her bir anahtarı ve değeri tek tek bir demet içine yerleştiriyor.
Daha sonra da bu listeyi set() fonksiyonuna göndererek kümemizi oluşturuyoruz.


Kümelerin Yapısı
kardiz = "Python Programlama Dili"
küme = set(kardiz)
print(küme)
{'r', 'm', 'y', 'n', 'g', 'D', 't', 'l', 'h', 'i', 'P', 'a', ' ', 'o'}


liste = ["elma", "armut", "elma", "kebap", "şeker", "armut",
"çilek", "ağaç", "şeker", "kebap", "şeker"]

for i in set(liste):
    print(i)
>şeker
armut
çilek
kebap
elma
ağaç

Gördüğünüz gibi, liste içinde birden fazla bulunan öğeler, Python’daki kümeler yardımıyla teke indirilebiliyor.

liste = ["elma", "armut", "elma", "kiraz",
"çilek", "kiraz", "elma", "kebap"]

for i in set(liste):
    print("{} listede {} kez geçiyor!".format(i, liste.count(i)))
>
kebap listede 1 kez geçiyor!
elma listede 3 kez geçiyor!
kiraz listede 2 kez geçiyor!
armut listede 1 kez geçiyor!
çilek listede 1 kez geçiyor!

arayüz_takımları = {'Tkinter', 'PyQT', 'PyGobject'}
arayüz_takımları
>{'PyGobject', 'PyQT', 'Tkinter'}

Gördüğünüz gibi, arayüz_takımları adlı kümenin öğeleri, öğe tanımlama sırasını çıktıda korumuyor.

Küme Üreteçleri (Set Comprehensions)


import random
liste = [random.randint(0, 10000) for i in range(1000)]
yüzden_küçük_sayılar = [i for i in liste if i < 100]
print(yüzden_küçük_sayılar)


import random
liste = [random.randint(0, 10000) for i in range(1000)]
küme = {i for i in liste if i < 100}
print(küme)

Kümelerin Metotları

for i in dir(set):
    if "__" not in i:
        print(i)
        
add
clear
copy
difference
difference_update
discard
intersection
intersection_update
isdisjoint
issubset
issuperset
pop
remove
symmetric_difference
symmetric_difference_update
union
update

Kümeler de, tıpkı listeler ve sözlükler gibi, değiştirilebilir bir veri tipidir.



clear()

km = set("adana")
for i in km:
    print(i)
>
a
d
n

km.clear()
km
>set()



copy()

Listeler ve sözlükleri incelerken copy() adlı bir metot öğrenmiştik. Bu metot aynı zamanda kümelerle birlikte de kullanılabilir. Üstelik işlevi de aynıdır:

km = set("kahramanmaraş")
yedek = km.copy()
yedek
>{'a', 'r', 'h', 'k', 'm', 'ş', 'n'}

km
>{'a', 'r', 'h', 'k', 'm', 'ş', 'n'}
        

add()
Add kelimesi Türkçe’de “eklemek” anlamına gelir. Adından da anlaşılacağı gibi, bu metot yardımıyla kümelerimize yeni öğeler ilave edebileceğiz:

küme = set(["elma", "armut", "kebap"])
küme.add("çilek")
print(küme)
>{'elma', 'armut', 'kebap', 'çilek'}

Eğer bir kümeye birden fazla öğeyi aynı anda eklemek isterseniz for döngüsünden yararlanabilirsiniz:

yeni = [1,2,3]
for i in yeni:
    küme.add(i)

küme
>{1, 2, 3, 'elma', 'kebap', 'çilek', 'armut'}


Bu arada, yeri gelmişken kümelerin önemli bir özelliğinden daha söz edelim. Bir kümeye herhangi bir öğe ekleyebilmemiz için, o öğenin değiştirilemeyen (immutable) bir veri tipi olması gerekiyor. 
Bildiğiniz gibi Python’daki şu veri tipleri değiştirilemeyen veri tipleridir:

Demetler
Sayılar
Karakter Dizileri

Şu veri tipleri ise değiştirilebilen veri tipleridir:

Listeler
Sözlükler
Kümeler

Dolayısıyla bir kümeye ancak şu veri tiplerini ekleyebiliriz:

Demetler
Sayılar
Karakter Dizileri

Önce boş bir küme oluşturalım:
küme = set()

Bu kümeye bir demet ekleyelim:
l = (1,2,3)
küme.add(l)
küme

Bir sayı ekleyelim:
l = 45
küme.add(l)
küme
>{45, (1, 2, 3)}


Bir karakter dizisi ekleyelim:
l = 'Jacques Derrida'
küme.add(l)
küme
>{'Jacques Derrida', 45, (1, 2, 3)}

bir kümeye herhangi bir veri ekleyebilmemiz için o verinin ‘değiştirilemeyen’ bir veri tipi olması gerekiyor.


difference()
Bu metot iki kümenin farkını almamızı sağlar. Örneğin:

k1 = set([1, 2, 3, 5])
k2 = set([3, 4, 2, 10])
k1.difference(k2)
>{1, 5}

Demek ki k1’in k2’den farkı buymuş. Peki k2’nin k1’den farkını bulmak istersek ne yapacağız?

k2.difference(k1)
>{10, 4}

difference() metodunu kullanmak yerine sadece eksi (-) işaretini kullanarak da aynı sonucu elde edebilirsiniz:

k1 - k2
veya
k2 - k1

difference_update()

k1 = set([1, 2, 3])
k2 = set([1, 3, 5])
k1.difference_update(k2)
print(k1)
>{2}

print(k2)
>{1, 3, 5}


discard()

discard() metodu kümeden öğe silmemizi sağlayacak:
hayvanlar = set(["kedi", "köpek", "at", "kuş", "inek", "deve"])
hayvanlar.discard("kedi")
print(hayvanlar)
>{'kuş', 'inek', 'deve', 'köpek', 'at'}

hayvanlar.discard("yılan")

Bu metodun en önemli özelliği olmayan bir öğeyi silmeye çalıştığımızda hata vermemesi.



remove()

Bu metot da bir önceki bölümde gördüğümüz discard() metoduyla aynı işlevi yerine getirir. Eğer bir kümeden öğe silmek istersek remove() metodunu da kullanabiliriz:

hayvanlar.remove("köpek")

Eğer remove() metodunu kullanarak, kümede olmayan bir öğeyi silmeye çalışırsak, discard() metodunun aksine, hata mesajı alırız:

hayvanlar.remove("fare")

>Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'fare'


intersection()

intersection kelimesi Türkçe’de “kesişim” anlamına gelir. Adından da anladığımız gibi, intersection() metodu bize iki kümenin kesişim kümesini verecektir:

k1 = set([1, 2, 3, 4])
k2 = set([1, 3, 5, 7])

k1.intersection(k2)
>{1, 3}

İki kümenin kesişimini bulmak için “&” işaretinden yararlanabiliriz:

k1 & k2
>{1, 3}


intersection_update()

Bu metodun görevi, intersection() metodundan elde edilen sonuca göre bir kümenin güncellenmesini sağlamaktır:

k1 = set([1, 2, 3])
k2 = set([1, 3, 5])
k1.intersection_update(k2)

print(k1)
>{1, 3}

print(k2)
>{1, 3, 5}


isdisjoint()

Bu metodun çok basit bir görevi vardır. isdisjoint() metodunu kullanarak iki kümenin kesişim kümesinin boş olup olmadığı sorgulayabilirsiniz.

a = set([1, 2, 3])
b = set([2, 4, 6])
a.isdisjoint(b)
>False

Burada temel olarak şu soruyu sormuş oluyoruz:
a ve b ayrık kümeler mi?

Python da bize cevap olarak, “Hayır değil,” anlamına gelen False çıktısını veriyor…

a = set([1, 3, 5])
b = set([2, 4, 6])
a.isdisjoint(b)
>True


issubset()

Bu metot yardımıyla, bir kümenin bütün elemanlarının başka bir küme içinde yer alıp yer almadığını sorgulayabiliriz. Yani bir kümenin, başka bir kümenin alt kümesi olup olmadığını bu metot yardımıyla öğrenebiliriz.

a = set([1, 2, 3])
b = set([0, 1, 2, 3, 4, 5])
a.issubset(b)
>True



issuperset()

a = set([1, 2, 3])
b = set([0, 1, 2, 3, 4, 5])
b.issuperset(a)
>True

Burada ise, “b kümesi a kümesini kapsar,” sonucunu elde ediyoruz. Yani b kümesi a kümesinin bütün elemanlarını içinde barındırıyor.


union()

union() metodu iki kümenin birleşimini almamızı sağlar. 

a = set([2, 4, 6, 8])
b = set([1, 3, 5, 7])
a.union(b)
>{1, 2, 3, 4, 5, 6, 7, 8}

union() metodu yerine “|” işaretini de kullanabiliriz:

a | b


update()

Metodumuzun adı update(). Bu metot, bir kümeyi güncellememizi sağlar. İsterseniz yukarıdaki örneği, bu metodu kullanarak tekrar yazalım:

küme = set(["elma", "armut", "kebap"])
yeni = [1, 2, 3]
küme.update(yeni)
print(küme)
>{1, 2, 3, 'elma', 'armut', 'kebap'}




symmetric_difference_update()

a = set([1,2, 5])
b = set([1,4, 5])
a.symmetric_difference_update(b)
print(a)
>{2, 4}



pop()

a = set(["elma", "armut", "kebap"])
a.pop()
>'elma'



Dondurulmuş Kümeler (Frozenset)

Eğer öğeleri üzerinde değişiklik yapılamayan bir küme oluşturmak isterseniz set() yerine frozenset() fonksiyonunu kullanabilirsiniz. 

dondurulmuş = frozenset(["elma", "armut", "ayva"])

type(dondurulmuş)
><class 'frozenset'>

Dondurulmuş kümeler ile normal kümeler arasında işlev olarak hiçbir fark yoktur. Bu ikisi arasındaki fark, listeler ile demetler arasındaki fark gibidir.























