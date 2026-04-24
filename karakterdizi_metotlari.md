swapcase() 
karakter dizisi içindeki büyük harfleri küçük harfe, küçük harfleri büyük harfe çevirir.

casefold()
bu metot bazı harfler için lower() metodunun verdiğinden farklı bir çıktı verir (örneğin 'ß' harfi).

strip()
karakter dizisinin başındaki ve sonundaki istediğimiz karakteri silmeye yarar.

lstrip()
karakter dizisinin sol tarafındaki gereksiz karakterlerden kurtulmamızı sağlar.

rstrip()
karakter dizisinin sağ tarafındaki gereksiz karakterlerden kurtulmamızı sağlar.

join()
parçalanmış karakter dizisini birleştirmeye yarar.

kardiz = "Beşiktaş Jimnastik Kulübü"
bölünmüş = kardiz.split()
print(bölünmüş)
" ".join(bölünmüş)

count()
Bu metodun görevi bir karakter dizisi içinde belli bir karakterin kaç kez geçtiğini sorgulamaktır.
2.parametre -> kaçıncı sıradan başlayacak.
3.parametre -> sıranın bitişi dahil değil.

index()
Karakterlerin, bir karakter dizisi içinde hangi sırada bulunduğunu öğrenmemizi sağlar
2.parametre -> kaçıncı sıradan başlayacak.

rindex()
karakter dizisini soldan sağa doğru değil de, sağdan sola doğru okumamızı sağlar.

find(), rfind()
find() ve rfind() metotları tamamen index() ve rindex() metotlarına benzer.
Tek farkı sorgulanan karakter bulunamazsa hata çıktısı yerine -1 çıktısı verir

center()
karakter dizisini ortalamaya yarar
2.parametre --> boşluk yerine karakter ekleme

rjust(), ljust()
rjust() metodu bir karakter dizisini sağa yaslarken, ljust() metodu karakter dizisini sola yaslar. 
2.parametre --> boşluk yerine karakter ekleme

zfill()
zfill() metodu yardımıyla karakter dizilerinin sol tarafına istediğimiz sayıda sıfır ekleyebiliriz.

partition()
Bu metot yardımıyla bir karakter dizisini belli bir ölçüte göre üçe bölüyoruz.

rpartition()
Bölmek için sağdan sola doğru okur.

encode()
Bu metot yardımıyla karakter dizilerimizi istediğimiz kodlama sistemine göre kodlayabiliriz. 

str.maketrans(), translate()
Türkçe karakterleri ingilizce karşılıklarına çevirirken kullanırız.
str.maketrans() bir sözlük nesnesi verir
3.parametre --> silinecekler

chr()
harflerin sayısal karşılıklarını verir.

isalpha()
karakter dizisinin alfabetik olup olmadığını sorgular.

isdigit()
karakter dizisinin sayı değerli olup olmadığını denetler.

isalnum()
karakter dizisinin alfanümerik olup olmadığını denetler.

isdecimal()
karakter dizisinin ondalık sayı olup olmadığını denetler.

isidentifier()
karakter dizisinin bir değişken adı olup olamayacağını denetler.

isnumeric()
karakter dizisinin sayı değerli olup olmadığını denetler.

isspace()
karakter dizisinin sadece boşluktan oluşup oluşmadığını kontrol eder.

isprintable()
karakter dizisinin basılabilen bir karakter olup olmadığını sorgular.
örneğin "a" basılabilirken "\n" basılamaz.
