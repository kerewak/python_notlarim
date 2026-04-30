Listelerin Metotları

append()
Bu metodu, bir listeye öğe eklemek için kullanıyoruz.

liste = ["elma", "armut", "çilek"]
liste.append("erik")
liste
>['elma', 'armut', 'çilek', 'erik']

append() metodu orijinal liste üzerinde doğrudan değişiklik yapmamıza izin verdiği için daha az kod yazmamızı ve programımızın daha performanslı çalışmasını sağlıyor.


extend()
li1 = [1, 3, 4]
li2 = [10, 11, 12]
li1. extend(li2)

print(li1)
>[1, 3, 4, 10, 11, 12]

işletim_sistemleri = ["Windows", "GNU/Linux", "Mac OS X"]
platformlar = ["IPhone", "Android", "S60"]
işletim_sistemleri.extend(platformlar)
print(işletim_sistemleri)
>['Windows', 'GNU/Linux', 'Mac OS X', 'IPhone', 'Android', 'S60']


insert()
insert kelimesi ‘yerleştirmek, sokmak’ gibi anlamlara gelir. insert() metodu da bu anlama uygun olarak, öğeleri listenin istediğimiz bir konumuna yerleştirir. 

f = open("deneme.txt", "r")
içerik = f.readlines()
içerik.insert(1, "Ferhat Yaz\n")

g = open("deneme.txt", "w")
g.writelines(içerik)

f.close()
g.close()

remove()
Bu metot listeden öğe silmemizi sağlar. 

reverse()
Liste öğelerini ters çevirmek için dilimleme yöntemini kullanabiliriz.
meyveler = ["elma", "armut", "çilek", "kiraz"]
meyveler[::-1]
>['kiraz', 'çilek', 'armut', 'elma']

Eğer istersek reversed() metodunu da kullabiliriz.

print(*reversed(meyveler))

reverse() metodunu kullanalım.
liste = ["elma", "armut", "çilek"]
liste.reverse()
liste
>['çilek', 'armut', 'elma']



pop()
Tıpkı remove() metodu gibi, bu metot da bir listeden öğe silmemizi sağlar

liste = ["elma", "armut", "çilek"]
liste.pop()
>'çilek'

pop() metodunu kullanarak bir liste öğesini sildiğimizde, silinen öğe ekrana basılacaktır.

parametre ile kullandığımızda istediğimiz sıradakini silebiliriz.


sort()
Liste öğelerini belirli bir düzene göre sıralamamızı sağlar.
sort() metodunun reverse parametresi önkoşul olarak False'dur
üyeler.sort(reverse=True) True olduğunda listeyi ters bir şekilde sıralar.

Türkçe karakterleri sıkıntısız bir şekilde sıralamak için şu kodları yazmalıyız:

harfler = "abcçdefgğhıijklmnoöprsştuüvyz"
çevrim = {harf: harfler.index(harf) for harf in harfler}
isimler = ["ahmet", "ışık", "ismail", "çiğdem", "can", "şule"]
isimler.sort(key=lambda x: çevrim.get(x[0]))
print(isimler)


index()
Bu metot bir liste öğesinin liste içindeki konumunu söyler bize.

liste = ["elma", "armut", "çilek"]
liste.index("elma")
>0

Karakter dizilerinin index() metoduyla ilgili söylediğimiz her şey listelerin index() metodu için de geçerlidir.

count()
Bu metot bir öğenin veri tipinde kaç defa geçtiğini yazdırır.


copy()
Daha önce iki yöntemden bahsetmiştik bunlara ek olarak:
liste2 = liste1.copy() yapabiliriz.

clear()
Bu metodun görevi bir listenin içeriğini silmektir.

liste = [1, 2, 3, 5, 10, 20, 30, 45]
liste.clear()
liste
>[]

del sözcüğünden farklıdır. del ifadesi listeyi direkt kaldırırken, clear() içeriğini temizler.




Demetlerin Metotları
bu veri tipinin bizi ilgilendiren iki metodu var:
1.index()
2.count()

index()
Bu metot bir demet öğesinin demet içindeki konumunu söyler bize:

demet = ("elma", "armut", "çilek")
demet.index("elma")
>0


count()
Bu metot bir öğenin o veri tipi içinde kaç kez geçtiğini söyler:
demet = ("elma", "armut", "elma", "çilek")
demet.count("elma")
>2



































