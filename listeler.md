Liste tanımlamak

liste = ["öğe1","öğe2","öğe3"]

Listeler bir veya daha fazla veri tipini içinde barındıran kapsayıcı bir veri tipidir.
Listelerin içinde başka listeler de bulunabilir.
dir() ve split() fonksiyonu liste çıktısı verir.


sayılar = [[0, 10], [6, 60], [12, 54], [67, 99]]
for i in sayılar:
    print(*range(*i))


Liste oluşturmanın bir yöntemi daha
list() fonksiyonu

alfabe = "abcçdefgğhıijklmnoöprsştuüvyz"
harf_listesi = list(alfabe)
print(harf_listesi)

>['a', 'b', 'c', 'ç', 'd', 'e', 'f', 'g', 'ğ', 'h', 'ı', 'i', 'j',
 'k', 'l', 'm', 'n', 'o', 'ö', 'p', 'r', 's', 'ş', 't', 'u', 'ü',
 'v', 'y', 'z']

list() fonksiyonu boş bir liste oluşturmak için de kullanılabilir. liste = [] koduna alternatif.
li = list()
print(li)
>[]

list(range(10))
>[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
range türünde bir veriyi list türüne çeviriyoruz.

Listeler değiştirilebilen (mutable) veri tipidir.

liste = [1, 2, 3]
liste[0:len(liste)] = 5, 6, 7
print(liste)
>[5, 6, 7]

liste[:] de yazabilirdik.

Listelere + işareti ile ekleyeceğimiz öğelerin de liste tipinde olması gerekiyor.
liste = [2, 4, 5, 7]
liste + [8]
>[2, 4, 5, 7, 8]


