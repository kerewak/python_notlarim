Kümeler ve Dondurulmuş Kümeler

Kümeler

Adından da az çok tahmin edebileceğiniz gibi kümeler, matematikten bildiğimiz “küme” kavramıyla sıkı sıkıya bağlantılıdır.
Bu veri tipi, matematikteki kümelerin sahip olduğu bütün özellikleri taşır.
Yani matematikteki kümelerden bildiğimiz kesişim, birleşim ve fark gibi özellikler Python’daki kümeler için de geçerlidir.


Küme Oluşturmak

Örneğin boş bir kümeyi şöyle oluşturuyoruz:
>boş_küme = set()

küme = set(["elma", "armut", "kebap"])

Dikkat ederseniz, küme oluştururken listelerden faydalandık.
Gördüğünüz gibi set() fonksiyonu içindeki öğeler bir liste içinde yer alıyor.
Dolayısıyla yukarıdaki tanımlamayı şöyle de yapabiliriz:


liste = ["elma", "armut", "kebap"]
küme = set(liste)



Bu daha temiz bir görüntü oldu. Elbette küme tanımlamak için mutlaka liste kullanmak zorunda değiliz. İstersek demetleri de küme haline getirebiliriz:

demet = ("elma", "armut", "kebap")
küme = set(demet)

Hatta ve hatta karakter dizilerinden dahi küme yapabiliriz:
kardiz = "Python Programlama Dili için Türkçe Kaynak"
küme = set(kardiz)

kardiz = "a"
küme = set(kardiz)

Ama sayılardan küme oluşturamayız:
n = 10
küme = set(n)
>TypeError: 'int' object is not iterable


bilgi = {"işletim sistemi": "GNU", "sistem çekirdeği": "Linux",
"dağıtım": "Ubuntu GNU/Linux"}

küme = set(bilgi)

küme = {'Python', 'C++', 'Ruby', 'PHP'}
type(küme)
><class 'set'>

Bu arada, bir sözlüğü kümeye çevirdiğinizde, elbette sözlüğün yalnızca anahtarları kümeye eklenecektir. Sözlüğün değerleri ise böyle bir işlemin sonucunda ortadan kaybolur.

bilgi = {"işletim sistemi": "GNU", "sistem çekirdeği": "Linux",
"dağıtım": "Ubuntu GNU/Linux"}

Bu sözlükteki anahtar-değer çiftlerini bir küme içine, çift öğeli demetler olarak yerleştirebiliriz:

liste = [(anahtar, değer) for anahtar, değer in bilgi.items()]
küme = set(liste)
>{('işletim sistemi', 'GNU'), ('dağıtım', 'Ubuntu GNU/Linux'), ('sistem çekirdeği', 'Linux')}

Bu sözlükteki anahtar-değer çiftlerini bir küme içine, çift öğeli demetler olarak yerleştirebiliriz:

liste = [(anahtar, değer) for anahtar, değer in bilgi.items()]
küme = set(liste)

Gördüğünüz gibi, liste üreteçlerini kullanarak önce bir liste oluşturuyoruz.
Bu liste her bir anahtarı ve değeri tek tek bir demet içine yerleştiriyor.
Daha sonra da bu listeyi set() fonksiyonuna göndererek kümemizi oluşturuyoruz.


Kümelerin Yapısı













