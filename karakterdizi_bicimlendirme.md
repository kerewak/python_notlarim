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




