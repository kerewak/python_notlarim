Demetler, özellikle görünüş olarak listelere çok benzeyen bir veri tipidir. Bu veri tipi de, tıpkı listeler gibi, farklı veri tiplerini içinde barındıran kapsayıcı bir veri tipidir.

demet = ("ahmet", "mehmet", 23, 45)
type(demet)
><class 'tuple'>

demet = "ahmet", "mehmet", 23, 45

Tek Öğeli bir Demet Tanımlamak

demet = ('ahmet',)

demet = ('elma', 'armut', 'kiraz')
demet[0]
>elma
demet[1]
>armut
demet[2]
>kiraz

listeler değiştirilebilir (mutable) bir veri tipi iken, demetler değiştirilemez (immutable) bir veri tipidir.

Ayrıca demetler üzerinde işlem yapmak listelere kıyasla daha hızlıdır. Dolayısıyla, performans avantajı nedeniyle de listeler yerine demetleri kullanmak isteyebilirsiniz.
Özellikle programların ayar (conf) dosyalarında bu veri tipi sıklıkla kullanılır. Örneğin Python tabanlı bir web çatısı (framework) olan Django’nun
settings.py adlı ayar dosyasında pek çok değer bir demet olarak saklanır. Mesela bir Django projesinde web sayfalarının şablonlarını (template) hangi 
dizin altında saklayacağınızı belirlediğiniz ayar şöyle görünür:

TEMPLATE_DIRS = ('/home/projects/djprojects/blog/templates',)
