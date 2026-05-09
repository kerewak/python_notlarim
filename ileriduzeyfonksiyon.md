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





