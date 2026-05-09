Lambda Fonksiyonları

Fonksiyon tanımlamamızı sağlayan bu yeni ifadeye lambda denir. Bu ifade ile oluşturulan fonksiyonlara ise ‘lambda fonksiyonları’…

fonk = lambda param1, param2: param1 + param2


çift_mi = lambda sayı: sayı % 2 == 0
çift_mi(100)
>True

çift_mi(99)
>False


lambda x: x + 10

'x' adlı bir parametre alan bir lambda fonksiyonu tanımla. Bu fonksiyon, bu
'x parametresine 10 sayısını eklesin.


lambda fonksiyonları özellikle grafik arayüz çalışmaları yaparken işinize yarayabilir. Örneğin:

import tkinter
import tkinter.ttk as ttk

pen = tkinter.Tk()

btn = ttk.Button(text='merhaba', command=lambda: print('merhaba'))
btn.pack(padx=20, pady=20)

pen.mainloop()














‘nonlocal’ Deyimi

nonlocal deyimi yerel olmayan anlamına gelir. Kullanım amacı global deyimi ile benzerdir.
Ancak bunu kullanmamız küresel yani global değişkenlere ulaşmamızı değil, yerel olmayan değişkenlere ulaşmamızı sağlar. 
Ayrıca bu deyimi sadece iç içe fonksiyonlarda kullanabiliriz.

def kapsayıcı_fonk():
    non_local_değişken = 1

    def iç_fonk():
        non_local_değişken = 2
        print(non_local_değişken)

    return iç_fonk


dönüş_fonksiyonu = kapsayıcı_fonk()
dönüş_fonksiyonu()
>2


a = 1

def fonk():
    global a
    a += 1
    print(a)


fonk()
>2

a
>2


def kapsayıcı_fonk():
    non_local_değişken = 1

    def iç_fonk():
        nonlocal non_local_değişken
        non_local_değişken += 1
        print(non_local_değişken)

    return iç_fonk


dönüş_fonksiyonu = kapsayıcı_fonk()
dönüş_fonksiyonu()
>2


Gördüğünüz gibi nonlocal ifadesi iç içe fonksiyonlar ile çalışırken iç fonksiyonda, kapsayıcı fonksiyonunun değişkenlerini değiştirmemizi sağlıyor. 


def yazıcı(mesaj):
    def yaz():
        nonlocal mesaj
        mesaj += " Dünya"
        print(mesaj)
    return yaz

y = yazıcı("Merhaba")
y()
>Merhaba Dünya
    

İç İçe Fonksiyonların Kullanım Alanları

İç içe fonksiyonların en fazla kullanıldığı yer bezeyicilerdir.



Üreteçler (Generators)



Üreteçlere Giriş


def fonksiyon_sayıcı():
    sayı = 0
    def say():
        nonlocal sayı
        sayı += 1
        return sayı
    return say

def üreteç_sayıcı():
    sayı = 0
    while True:
        sayı += 1
        yield sayı



type(fonksiyon_sayıcı)
><class 'function'>
type(üreteç_sayıcı)
><class 'function'>

fonk = fonksiyon_sayıcı()
üreteç = üreteç_sayıcı()

type(fonk)
><class 'function'>
type(üreteç)
><class 'generator'>

fonk()
>1
fonk()
>2
fonk()
>3
fonk()
>4

next(üreteç)
>1
next(üreteç)
>2
next(üreteç)
>3
next(üreteç)
>4


Bir fonksiyonun içinde return deyimine ulaşıldığında fonksiyon sonlanır ve fonksiyona ait yerel değişkenler silinir.
yield deyiminde böyle bir şey söz konusu değildir. Aynı iç içe fonksiyonlarda iç fonksiyonunun dış fonksiyondaki değişkeni 
kullanması gibi üreteçlerin de yerel değişkenleri Python tarafından saklanır. Ancak üreteçlerde belli değişkenler değil, yerel değişkenlerin tamamı saklanır.



Üreteçlerin Tanımlanması


‘yield’ Deyimi ve ‘next’ Fonksiyonu


def üreteç():
        yield "Merhaba"
        yield "Dünya"

g = üreteç()
next(g)
>"Merhaba"
next(g)
>"Dünya"
next(g)
>Traceback (most recent call last):
  File "<pyshell#5>", line 1, in <module>
    next(g)
StopIteration

next’ fonksiyonunun burada yaptığı iş için ‘yineleme (iteration)’ terimi kullanılır. ‘next’ fonksiyonuna parametre olarak verilebilen nesneler ise birer ‘yinelenebilir nesne (iterable object)’dir. ‘generator’ sınıfı yinelenebilir nesnelere bir örnektir.


‘yield from’ Deyimi

yield from deyimi bir üretecin içinde, başka bir üretecin yield ile döndüreceği değerleri tekrar yield etmek istediğimizde kullanılabilir. 

def üreteç1():
    yield "üreteç1 başladı"
    yield "üreteç1 bitti"

def üreteç2():
    yield "üreteç2 başladı"
    yield from üreteç1()
    yield "üreteç2 bitti"

>>> for i in üreteç2():
        print(i)

üreteç2 başladı
üreteç1 başladı
üreteç1 bitti
üreteç2 bitti
>>>

yield from bir_üreteç 
ifadesi ile bu ifade eş değerdir:
for i in bir_üreteç:
    yield i



Liste ve Sözlük Üreteçleri Hakkında

üreteç = (i for i in range(10))
type(üreteç)
><class 'generator'>
listem = list(üreteç)
listem
>[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]


Gördüğünüz gibi aslında şu yazım şekli:

üreteç = (i for i in range(10))

Bunun için bir kısaltmadır:

def üreteç_fonksiyonu():
    for i in range(10):
        yield i

üreteç = üreteç_fonksiyonu()

Aynı lambda fonksiyonların normal fonksiyonlar için bir kısaltma olması gibi.


Üreteç değişkenimizi bir defa for döngüsü ile kullandığımızda ikinci defa kullanamamaktayız.
Çünkü ilk döngüde üretecimiz bitene kadar çalıştı ve en sonunda StopIteration yükseltti.
Artık istediğimiz kadar üretecimizi kullanmayı deneyelim, StopIteration yükseltmeye devam edecektir
(unutmayalım ki for döngüsü StopIteration hatalarını yakalar ve yakaladığında da çalışmayı bırakır)


üreteç = ((str(i),i) for i in range(3))
sözlük = dict(üreteç)

üreteç = ((str(i),i) for i in range(3))
sözlük = {}
for key,value in üreteç:
        sözlük[key] = value




