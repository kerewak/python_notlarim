format() Metodu ile Biçimlendirme (Yeni Yöntem)

isim = input("İsminiz: ")
print("Merhaba {}. Nasılsın?".format(isim))

aynısını bu şekilde de yapabilirdik:
isim = input("İsminiz: ")
print("Merhaba", isim + ".", "Nasılsın?")

ama format kullanmak daha pratik bir yöntem.



kalkış       = input("Kalkış yeri: ")
varış        = input("Varış yeri: ")
isim_soyisim = input("İsim ve soyisim: ")
bilet_sayısı = input("Bilet sayısı: ")

print("""{} noktasından {} noktasına, 14:30 hareket saatli
sefer için {} adına {} adet bilet ayrılmıştır!""".format(kalkış,
                                                         varış,
                                                         isim_soyisim,
                                                         bilet_sayısı))

Küme parantezi içinde sayı kullanarak değerlerin sırasını düzenleyebiliriz ve tekrarlandırabiliriz.
Parentez içini aynı zamanda isimlendirebiliriz.

print("{dil} dersleri".format(dil="python"))

print("{:>15}".format("istihza"))
>        istihza

: işareti bir biçimlendirme işlemi yapacağımızı gösterir.
> işareti ise bu biçimlendirmenin bir hizalama işlemi olacağını haber verir.
Yazdığımız sayı ise bu işlemin kaç karakterlik bir alanda yapılacağını gösterir.

Sola yaslamak isteseydik:
print("|{:<15}|".format("istihza"))
>|istihza        |

Ortalamak isteseydik:
>print("|{:^15}|".format("istihza"))

Örnek:
for sıra, karakter in enumerate(dir(str)):
    if sıra % 3 == 0:
        print("\n", end="")
    print("{:<20}".format(karakter), end="")

Eski biçimlendirme yöntemiyle kullandığımız harfleri format ile de kullanabiliyoruz.
Süslü parantez içerisinde biçimlendirme harfini koyarken soluna : işaretini koyuyoruz.

b onlu düzendeki sayıları ikili düzendeki karşılıklarına çevirir
"{:b}".format(2)
>'10'

, kullanarak sayıları basamaklarına ayırabiliriz.
"{:,}".format(1234567890)
>'1,234,567,890'


