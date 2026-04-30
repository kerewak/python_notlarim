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


Listeleri Kopyalamak

li1 = ["elma", "armut", "erik"]
li1 = li2
li1'de yapılan değişiklik l2'yi de etkiler. Çünkü listeler değiştirilebilen veri tipidir.


Liste Üreteçleri
liste = [i for i in range(1000)]
liste = []

for i in range(1000):
    liste += [i]
    
liste = [i for i in range(1000) if i % 2 == 0]


liste = []
for i in range(1000):
    if i % 2 == 0:
        liste += [i]

        
liste = [[1, 2, 3],
         [4, 5, 6],
         [7, 8, 9],
         [10, 11, 12]]

tümü = []

for i in liste:
    for z in i:
        tümü += [z]

print(tümü)


liste = [[1, 2, 3],
         [4, 5, 6],
         [7, 8, 9],
         [10, 11, 12]]

tümü = [z for i in liste for z in i]
print(tümü)

tahta = [["___", "___", "___"],
         ["___", "___", "___"],
         ["___", "___", "___"]]

print("\n"*15)

for i in tahta:
    print("\t".expandtabs(30), *i, end="\n"*2)

kazanma_ölçütleri = [[[0, 0], [1, 0], [2, 0]],
                     [[0, 1], [1, 1], [2, 1]],
                     [[0, 2], [1, 2], [2, 2]],
                     [[0, 0], [0, 1], [0, 2]],
                     [[1, 0], [1, 1], [1, 2]],
                     [[2, 0], [2, 1], [2, 2]],
                     [[0, 0], [1, 1], [2, 2]],
                     [[0, 2], [1, 1], [2, 0]]]

x_durumu = []
o_durumu = []

sıra = 1
while True:
    if sıra % 2 == 0:
        işaret = "X".center(3)
    else:
        işaret = "O".center(3)

    print()
    print("İŞARET: {}\n".format(işaret))

    x = input("yukarıdan aşağıya [1, 2, 3]: ".ljust(30))
    if x == "q":
        break

    y = input("soldan sağa [1, 2, 3]: ".ljust(30))
    if y == "q":
        break

    x = int(x)-1
    y = int(y)-1

    print("\n"*15)

    if tahta[x][y] == "___":
        tahta[x][y] = işaret
        if işaret == "X".center(3):
            x_durumu += [[x, y]]
        elif işaret == "O".center(3):
            o_durumu += [[x, y]]
        sıra += 1
    else:
        print("\nORASI DOLU! TEKRAR DENEYİN\n")

    for i in tahta:
         print("\t".expandtabs(30), *i, end="\n"*2)

    for i in kazanma_ölçütleri:
        o = [z for z in i if z in o_durumu]
        x = [z for z in i if z in x_durumu]

        if len(o) == len(i):
            print("O KAZANDI!")
            quit()
        if len(x) == len(i):
            print("X KAZANDI!")
            quit()




