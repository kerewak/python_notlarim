f stringleri kullanabilmemiz için Python 3.6 ya da daha yeni bir sürüm kullanmalıyız.

isim = 'Kerem'
yas = 19
f'Onun adı {isim} ve o {yas} yaşında.'
>'Onun adı Kerem ve o 19 yaşında.'

isim = 'Kerem'
yas = 10
'Onun adı {} ve o {} yaşında'.format(isim, yas)
>'Onun adı Kerem ve o 19 yaşında.'

Aynı zamanda f-string’lerin içinde Python işlemleri de yapabiliriz.

birinci_rakam = 5
ikinci_rakam = 3
f'Rakamların toplamı {birinci_rakam + ikinci_rakam} eder.'
>'Rakamların toplamı 8 eder.'

Tek satırlık hesap makinesi:
f'Sayıların toplamı { int(input("Birinci sayıyı girin: ")) + int(input("İkinci sayıyı girin: ")) } eder.'
Birinci sayıyı girin: 10
İkinci sayıyı girin: 7
'Sayıların toplamı 17 eder.'

f-string’in içinde Python kodu yazmak her zaman en iyi yol olmayabilir.

fstring = "f-string"
f"{{ {fstring}: f'{{ifade}}' şeklinde kullanılır. }}"
> "{ f-string: f'{ifade}' şeklinde kullanılır. }"

Formatlanacak ifadeden sonra = işareti eklenerek değişken adı ile birlikte sahip olduğu değerin repr hali elde edilebilir.
print ile debug edildiği durumlarda pratik bir şekilde kullanılabilir:
kaynak = "Python İstihza"
yıl = "2026"
f"{kaynak=} {yıl=}"
kaynak='Python İstihza' yıl='206'


istihza = "Python Istihza"
f"{istihza:^30}"   # "istihza".center(30)
'        Python Istihza        '
f"{istihza:-^30}"  # "istihza".center(30, '-')
'--------Python Istihza--------'
f"{istihza:30}"    # "istihza".ljust(30)
'Python Istihza                '
f"{istihza:>30}"   # "istihza".just(30)
'                Python Istihza'
f"{istihza:>030}"  # "istihza".zfill(30)
'0000000000000000Python Istihza'

f.string ve format için genel notasyon:
[[dolgu_karakteri]hizalama][işaret][#][0][genişlik][grup_karakteri][.ondalık][veri_tıpı]

dolgu_karakteri : <herhangi bir karakter>
hizalama        : "<" | ">" | "^" | "="
işaret          : "+" | "-" | " " (yalnızca sayı tipi)
genişlik        : pozitif sayı
grup_karakteri  : "_" | "," (yalnızca sayı tipi)
ondalık         : pozitif sayı (yalnızca sayı tipi)
veri_tıpı       : "b" | "c" | "d" | "e" | "E" | "f" | "F" | "g" | "G" | "n" | "o" | "s" | "x" | "X" | "%"



sayı = 123

f"{sayı:>6}"
>'   123'
f"{sayı:0>+6}"
>'00+123'
f"{sayı:0=+6}"
>'+00123'
f"Binary: {sayı:b} | Octal: {sayı:o} | Hexadecimal: {sayı:x}"
>'Binary: 1111011 | Octal: 173 | Hexadecimal: 7b'
f"Binary: {sayı:#b} | Octal: {sayı:#o} | Hexadecimal: {sayı:#x}"
>'Binary: 0b1111011 | Octal: 0o173 | Hexadecimal: 0x7b'
ondalık = 0.123
f"{ondalık:.2f}"  # f | F ondalık formatlama
>'0.12'
f"{ondalık:.5f}"
>'0.12300'
f"{ondalık:.5g}"  # g | G fazla sıfırlar dahil edilmez
>'0.123'
sayı = 123456
f"{sayı:_}"
>'123_456'
f"{sayı:-^15_}"
>'----123_456----'
f"{sayı:,}"
>'123,456'
işlem = 1 / 12
f"{işlem:.2%}"  # Sonucun 100 ile çarpılmış halini yüzde olarak çıktı verir
>'8.33%'













