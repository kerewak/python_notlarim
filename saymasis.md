Onlu Sayma Sistemi
(0 * (10 ** 0)) + (8 * (10 ** 1)) + (9 * (10 ** 2)) + (1 * (10 ** 3))
>1980

Sekizli Sayma Sistemi
(4 * (8 ** 0)) + (7 * (8 ** 1)) + (6 * (8 ** 2)) + (3 * (8 ** 3))
>1980

On Altılı Sayma Sistemi
7bc
((c * 16 ** 0)) + ((b * 16 ** 1)) + ((7 * 16 ** 2))


    a –> 10

    b –> 11

    c –> 12

    d –> 13

    e –> 14

    f –> 15


((12 * (16 ** 0)) + ((11 * (16 ** 1)) + ((7 * (16 ** 2))
>1980

İkili Sayma Sistemi
(0 * (2 ** 0)) + (0 * (2 ** 1)) + (1 * (2 ** 2)) + (1 * (2 ** 3))
>12


Sayma Sistemlerini Birbirine Dönüştürme

Fonksiyon Kullanarak

bin()
Bu fonksiyon bir sayının ikili (binary) sayı sistemindeki karşılığını verir:
bin(2)
>'0b10'

bu karakter dizisinin ilk iki karakteri '0b', o sayının ikili sisteme ait bir sayı olduğunu gösteren bir işarettir.

hex()
Bu fonksiyon, herhangi bir sayıyı alıp, o sayının on altılı sistemdeki karşılığını verir:

hex(10)
>'0xa'
'0x', o sayının on altılı sisteme ait bir sayı olduğunu gösteriyor.

oct()
Bu fonksiyon, herhangi bir sayıyı alıp, o sayının sekizli sistemdeki karşılığını verir:
oct(10)
>'0o12'
'0o', o sayının sekizli sisteme ait bir sayı olduğunu gösteriyor.

int()
Bu fonksiyonun şimdiye kadar gördüğümüz işlevi dışında bir işlevi daha vardır. 
Biz bu fonksiyonu kullanarak herhangi bir sayıyı onlu sistemdeki karşılığına dönüştürebiliriz:
int('7bc', 16)
>1980

Biçimlendirme Yoluyla

b
'{:b}'.format(12)
>'1100'

x
'{:x}'.format(1980)
>'7bc'

o
'{:o}'.format(1980)
>'3674'


n = '7bc'
"{} sayısının onlu karşılığı {:d} sayısıdır.".format(n, int(n, 16))

veya

n = '7bc'
"{} sayısının onlu karşılığı {} sayısıdır.".format(n, int(n, 16))

Bilgisayarlar bu sayı sistemleri arasında sadece ikili sayı sistemini ‘anlayabilir’.
Bilgisayar dediğimiz şey, üzerinden elektrik geçen devrelerden ibaret bir makinedir.
Eğer bir devrede elektrik yoksa o devrenin değeri ~0 volt iken, o devreden elektrik geçtiğinde devrenin değeri ~5 volttur. Gördüğünüz gibi,
ortada iki farklı değer var: ~0 volt ve ~5 volt. Yukarıda anlattığımız gibi, ikili (binary) sayma sisteminde de iki değer bulunur: 0 ve 1.
Dolayısıyla ikili sayma sistemi bilgisayarın iç işleyişine en uygun sistemdir. ikili sistemde ~0 volt’u 0 ile, ~5 volt’u ise 1 ile temsil edebiliyoruz.
Yani devreden elektrik geçtiğinde o devrenin değeri 1, elektrik geçmediğinde ise 0 olmuş oluyor. Tabii bilgisayar açısından bakıldığında devrede elektrik vardır veya yoktur.
Biz insanlar bu ikili durumu daha kolay bir şekilde temsil edebilmek için her bir duruma 0 ve 1 gibi bir ad veriyoruz.



















