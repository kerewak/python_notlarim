% İşareti ile Biçimlendirme (Eski Yöntem)

for i in range(100):
  print("%s" %%%i)

print("Karakter dizilerinin toplam %s adet metodu vardır" %len(dir(str)))

for i in dir(str):
  print(%15s %i)

% ile s arasına yerleştirdiğimiz sayı, biçimlendirilecek karakter dizisinin kaç karakter kaplayacağını ayarlar.
Sola yaslamak için negatif sayılardan yardım alabiliriz. (%-15s)

print("depoda %(miktar)s kilo %(ürün)s kaldı" %{"miktar": 25,
                                                "ürün": "elma"})

sayfa = """
<html>
    <head>
        <title> %(dil)s </title>
    </head>

    <body>
        <h1> %(dil)s </h1>
        <p>Web sitemize hoşgeldiniz! Konumuz: %(dil)s</p>
    </body>
</html>
"""

print(sayfa % {"dil": "Python Programlama Dili"})


% sabit değerini bazı harflerle birlikte kullanarak, farklı karakter dizisi biçimlendirme işlemleri gerçekleştirebiliriz.

Python’da her şey bir karakter dizisi olarak temsil edilebilir.


d harfi sayıları temsil eder.
(decimal)
print("Şubat ayı bu yıl %d gün çekiyor" %28)

print("%d" %13.5)
> 13

print("%(sayı)d" % {"sayı": 23})
>23

print("%05d" %23)
>00023
veya
print("%.5d" %23)
>00023

print("%10.5d" %23)
>     00023
Burada 23 sayısının toplam 10 boşlukluk bir yer kaplamasını ve bu 10 adet boşluğun 5 tanesinin içine 0 sayılarının ve 23 sayısının sığdırılmasını istedik.

"%-10.5d" %10
>'00010     '


i (integer)
%i ile %d nin bir farkı yoktur.

o (octal)
sekizli düzendeki sayıları temsil eder. Bu harfi kullanarak onlu düzeydeki sayıyı sekizli düzeye çevirebiliriz.

x (hexadecimal)
onaltılı düzendeki sayıları temsil eder. Bu harfi kullanarak onlu düzeydeki sayıyı onaltılı düzeye çevirebiliriz.

X (hexadecimal)
x ile aynıdır farkı, harfle gösterilen onaltılı sayıları büyük harfle temsil etmesidir

f (float)
karakter dizisi içindeki sayıyı %f yapısı ile floata çevirdiğimizde noktadan sonra öntanımlı olarak 6 hane yer alacaktır.

print("%f" %10)
>10.000000

print("%.2f" % 10)
>10.00
>
% ile f arasına .2 yerleştirdiğimizde noktadan sonraki hane sayısını belirleyebiliriz.

c (char)
Bu harf tek bir karakteri temsil eder.

ASCII tablosunda sayılara karşılık gelen karakterleri görür.
print("%c" %65)
>A

Bütün ASCII tablosunu ekrana dökebiliriz.
for i in range(128):
    print("%s ==> %c" %(i, i))


örnekler:

for i in range(20):
    print("%5d%5o%5x" %(i, i, i))
veya
for i in range(20):
    print("%(deger)5d%(deger)5o%(deger)5x" %({"deger": i}))







