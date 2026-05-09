exit()

Bu fonksiyon, o anda çalışan programdan çıkmanızı sağlar. Eğer bu komutu etkileşimli kabukta verirseniz o anda açık olan oturum kapanacaktır.


help()

Python'ın en faydalı fonksiyonu.

id()

Python’daki her nesnenin kimliği eşşiz, tek ve benzersizdir.

input()

input() adlı bu gömülü fonksiyonu kullanarak kullanıcı ile veri alışverişinde bulunabiliyoruz.

format()

format() gömülü fonksiyonu yalnızca tek bir değeri biçimlendirmek için kullanılır.

format(12, '.2f')
>‘12.00’

Yukarıdaki ifadeyi daha önce gördüğümüz format() metodu ile şu şekilde yazabiliriz:
'{:.2f}'.format(12)
>'12.00'


filter()

Bu gömülü fonksiyon yardımıyla dizi niteliği taşıyan nesneler içindeki öğeler üzerinde belirli bir ölçüte göre bir süzme işlemi uygulayabiliriz. 


for i in l:
    if i % 2 == 1:
            print(i)



[i for i in l if i % 2 == 1]


def tek(sayı):
    return sayı % 2 == 1

filter() fonksiyonu toplam iki parametre alır. Bu parametrelerden ilki ölçütü belirleyen fonksiyon, 
ikincisi ise bu ölçütün uygulanacağı öğedir. Yukarıdaki örneğe baktığımızda, tek() adlı fonksiyonun, l adlı öğe üzerine uygulandığını görüyoruz.

filter() fonksiyonu, dizi özelliği taşıyan nesneler üzerinde belli bir ölçüte göre filtreleme işlemi yapmamızı sağlar. 




l = [400, 176, 64, 175, 355, 13, 207, 298, 397, 386, 31,
     120, 120, 236, 241, 123, 249, 364, 292, 153]


list(filter(tek, l))

veya

print(*filter(tek, l))

ya da

[i for i in filter(tek, l)]


hash()

Bu fonksiyon, belirli türdeki nesnelere bir karma değeri vermemizi sağlar. 


isinstance()

isinstance('istihza', str)
>True

isinstance('istihza', list)
>False


len()

len('istihza')
>7


map()

l = [1, 4, 5, 4, 2, 9, 10]
def karesi(n):
    return n ** 2

list(map(karesi, l))
>[1, 16, 25, 16, 4, 81, 100]



max()

max() gömülü fonksiyonunun görevi, bir dizi içindeki en büyük öğeyi vermektir.

max(1, 2, 3)
>3

max() fonksiyonu yukarıda gösterildiği gibi birtakım isimsiz parametrelerle birlikte key adlı isimli bir parametre de alır. 
Bu parametre yardımıyla max() fonksiyonunun ‘en büyük’ kavramını hangi ölçüte göre seçeceğini belirleyebiliriz. Örneğin:

isimler = ['ahmet', 'can', 'mehmet', 'selin', 'abdullah', 'kezban']
max(isimler, key=len)
>'abdullah'



min()

min() fonksiyonu max() fonksiyonunun tam tersini yapar.



open()

Bu fonksiyon herhangi bir dosyayı açmak veya oluşturmak için kullanılır. 

open(dosya_adi, mode='r', buffering=-1, encoding=None,
     errors=None, newline=None, closefd=True, opener=None)

buffering parametresi bu 1 değerini yalnızca metin kipinde alabilir. Bu kısıtlamayı da aklımızın bir kenarına not edelim…

0 ve 1 dışında buffering parametresine 1’den büyük bir değer verdiğinizde ise tampon boyutunun ne kadar olacağını kendiniz belirlemiş olursunuz.


Eğer kendi sisteminizde öntanımlı tampon boyutunun ne olduğunu merak ediyorsanız şu komutları kullanabilirsiniz:

import io
io.DEFAULT_BUFFER_SIZE

dosyalarınızın hangi satır sonu karakterine sahip olacağını yukarıda bahsettiğimiz newline adlı parametre ile belirleyebilirsiniz. Örneğin:

f = open('dosya', newline='\n')
Bu şekilde dosyanız hangi işletim sisteminde olursa olsun satır sonlarında \n karakterine sahip olacaktır.

Dosyaların metotlarını incelerseniz o listede fileno() adlı bir metodun olduğunu göreceksiniz. 
Bu metot, bize bir dosyanın ‘dosya tanımlayıcısını’ (file descriptor) verir. Dosya tanımlayıcıları,
dosyaya işaret eden pozitif tam sayılardır. 0, 1 ve 2 sayıları standart girdi, 
standart çıktı ve standart hata dosyalarına ayrılmış olduğu için, sizin açtığınız ve üzerinde işlem yaptığınız dosyaların tanımlayıcıları 2 sayısından büyük olacaktır.

Python’da bir dosyayı open() fonksiyonuyla açarken dosya adını vermenin yanı sıra, dosyanın tanımlayıcısını da kullanabilirsiniz:

z = open(4)
veya
z = open(g.fileno())

bir dosyanın tanımlayıcısı tek ve benzersizdir. Farklı dosyalar aynı tanımlayıcılara sahip olmaz


c = open(b.fileno(), closefd=False)

closefd parametresine False değeri verdiğimizde dosya kapansa bile, o dosyaya ait dosya tanımlayıcısı varolmaya devam edecektir.



pow()

bu fonksiyonu bir sayının kuvvetlerini hesaplamak için kullanıyoruz.

Üçüncü parametre ise kuvvet hesaplaması sonucu elde edilen sayının modülüsünü hesaplayabilmemizi sağlar. Yani:

pow(2, 3, 2)
>0


print()

print(deg1, deg2, deg3, ..., sep=' ', end='\n', file=sys.stdout, flush=False)

flush:bu parametre, değerleri tampona almadan doğrudan dosyaya gönderebilmemizi sağlar.
Bu parametrenin öntanımlı değeri False’tur. Yani değerler dosyaya yazılmadan önce öntanımlı olarak öncelikle tampona gider.
Ama eğer biz bu parametrenin değerini True olarak değiştirirsek, değerler doğrudan dosyaya yazılır.



quit()

Bu fonksiyonu programdan çıkmak için kullanıyoruz.


range()

Bu fonksiyonu belli bir aralıktaki sayıları listelemek için kullanıyoruz.

l = range(0, 10)

print(l)
>range(0, 10)


type(l)
><class 'range'>

range(başlangıç_değer, bitiş_değeri, atlama_değeri)


















