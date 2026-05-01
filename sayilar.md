Biz Python'da üç tür sayı olduğunu biliyoruz:

1. Tam sayılar (integers)
2. Kayan noktalı sayılar (floating point numbers veya kısaca floats)
3. Karmaşık sayılar (complex numbers)

Sayıların Metotları

Tam Sayıların Metotları

bit_length()

for i in range(11):
    print(i, bin(i)[2:], len(bin(i)[2:]), sep="\t")

0       0       1
1       1       1
2       10      2
3       11      2
4       100     3
5       101     3
6       110     3
7       111     3
8       1000    4
9       1001    4
10      1010    4
    
Herhangi bir tam sayının kaç bit’lik bir yer kapladığını öğrenmek için, tam sayıların metotlarından biri olan bit_length() metodundan yararlanacağız:

sayı = 10
sayı.bit_length()
>4

bit_length() metodu, ikili sayma sistemindeki bir sayı üzerine len() fonksiyonunun uygulanması ile eşdeğerdir. Yani:
len(bin(10)[2:]) == (10).bit_length()
>True

Bu metodu doğrudan sayıların üzerine uygulayamayız. Önce bir değişkene atamamız veya parantez içinde yazmamız gerekir.

Bu durum, yani sayıyı parantez içinde gösterme zorunluluğu, 10 sayısının sağına bir nokta işareti koyduğumuzda,
Python’ın bu sayıyı bir kayan noktalı sayı olarak değerlendirmesinden kaynaklanıyor. Yani biz ‘10’ yazıp, bit_length() 
metodunu bu sayıya bağlama amacıyla sayının sağına bir nokta koyduğumuz anda, Python bu sayının bir kayan noktalı sayı olduğunu zannediyor.
Çünkü Python açısından, 10. sayısı bir kayan noktalı sayıdır. 

type(10.)
> <class 'float'>



Kayan Noktalı Sayıların Metotları


as_integer_ratio()
Bu metot, birbirine bölündüğünde ilgili kayan noktalı sayıyı veren iki adet tam sayı verir bize. 

sayı = 4.5
sayı.as_integer_ratio()
>(9, 2)

is_integer()



Karmaşık Sayıların Metotları

imag

bir gerçek bir de sanal kısımdan oluşan sayılara karmaşık sayılar (complex) adı verilir.

imag adlı nitelik, bize bir karmaşık sayının sanal kısmını verir:

c = 12+4j
c.imag
>4.0



real

real adlı nitelik bize bir karmaşık sayının gerçek kısmını verir:

c = 12+4j
c.real
>12.0



Aritmetik Fonksiyonlar

Python programlama dili, bize sayılarla rahat çalışabilmemiz için bazı fonksiyonlar sunar. Bu fonksiyonları kullanarak, karmaşık aritmetik işlemleri kolayca yapabiliriz.

Biz bu bölümde Python’ın bize sunduğu bu gömülü fonksiyonları tek tek inceleyeceğiz.

Gömülü fonksiyonlar, Python programlama dilinde, herhangi bir özel işlem yapmamıza gerek olmadan,
kodlarımız içinde doğrudan kullanabileceğimiz fonksiyonlardır. Biz şimdiye kadar pek çok gömülü fonksiyonla zaten tanışmıştık.
O yüzden gömülü fonksiyonlar bizim yabancısı olduğumuz bir konu değil. Mesela buraya gelene kadar gördüğümüz,
len(), range(), type(), open(), print() ve id() gibi fonksiyonların tamamı birer gömülü fonksiyondur.

Şimdiye kadar öğrendiğimiz gömülü fonksiyonlardan şu listede yer alanlar, matematik işlemlerinde kullanılmaya uygun olanlardır:

1. complex()
2. float()
3. int()
4. pow()
5. round()
6. hex()
7. oct()
8. bin()


abs()
Bu fonksiyon bize bir sayının mutlak değerini verir:

abs(-2)
>2

abs(2)
>2

divmod()
Bu fonksiyon, bir sayının bir sayıya bölünmesi işleminde bölümü ve kalanı verir:

divmod(10, 2)
>(5, 0)

10 sayısı 2 sayısına bölündüğünde ‘bölüm’ 5, ‘kalan’ ise 0’dır.

divmod(14, 3)
>(4, 2)

aslında divmod() fonksiyonu şu kodlarla aynı işi yapıyor:
14 // 3, 14 % 3

max()

Bu fonksiyon listenin içindeki en büyük sayıyı söyler.
Ayrıca bu fonksiyonu kullanarak liste içindeki en uzun karakter dizisini bulabiliriz.

print(max(isimler, key=len))

Bu fonksiyon key diye bir parametre alır


sayı_sistemleri = ["onlu", "sekizli", "on altılı", "ikili"]

print(("{:^9} "*len(sayı_sistemleri)).format(*sayı_sistemleri))

for i in range(17):
    print("{0:^9} {0:^9o} {0:^9x} {0:^9b}".format(i))



sayı_sistemleri = ["onlu", "sekizli", "on altılı", "ikili"]

en_uzun = len(max(sayı_sistemleri, key=len))

print(("{:^{aralık}} "*len(sayı_sistemleri)).format(*sayı_sistemleri, aralık=en_uzun))

for i in range(17):
    print("{0:^{1}} {0:^{1}o} {0:^{1}x} {0:^{1}b}".format(i, en_uzun))


min()

Bu fonksiyon, max() fonksiyonun yaptığı işin tam tersini yapar.
Yani bu fonksiyonu kullanarak bir liste içindeki en küçük sayıyı bulabiliriz.
Tıpkı max() fonksiyonunda olduğu gibi, min() fonksiyonunda da key parametresini kullanabiliriz.



sum()

Bu fonksiyon bir liste içinde yer alan bütün sayıları birbiriyle toplar. Örneğin:

a = [10, 20, 43, 45 , 77, 2, 0, 1]
sum(a)
>198

Eğer bu fonksiyonun, toplama işlemini belli bir sayının üzerine gerçekleştirmesini istiyorsak:

sum(a, 10)
>208


















