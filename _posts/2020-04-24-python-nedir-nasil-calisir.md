---
layout: post
title: Python Dersleri - 1. Python Nedir ve Nasıl Çalışır? 
image: /img/python.png
tags: [python, programming]
comments: true
---

Merhabalar, bu makale ile birlikte Python programlama diline genel bir giriş yapıyor olacağız ve ilerledikçe daha da kompleks yapıları inceliyor olacağız. Bu yazı dizisine başlamamın amacı aslında türkçe kaynak eksikliğini bir nebze de olsa gidermek. Elimden geldiğince açıklayıcı ve bilgilendirici bir yazı sunmak istiyor ve isterseniz lafı çok fazla uzatmadan başlayalım diyorum :)

## Python

Python, **Guido Van Rossum** tarafından Amsterdam'da bir hobi projesi olarak 1990 yılında geliştirilmeye başlanmıştır. Piyasaya ilk olarak 1991 yılında sürülmüştür. Adını sanılanın aksine bir yılandan değil Guido van Rossum’un çok sevdiği, Monty Python adlı bir İngiliz komedi grubunun Monty Python’s Flying Circus adlı gösterisinden almıştır. Nesne yönelimli(Object Oriented), dinamik tipli(Dynamic-typed) ve yüksek seviyeli(High-Level) açık kaynak bir programlama dili olarak karşımıza çıkmaktadır. Piyasada kullanılan en popüler programlama dilleri arasındadır. 
[Buradan](http://pypl.github.io/PYPL.html) daha detaylı olarak inceleyebilirsiniz.

**Python yorumlanan mı yoksa derlenen bir dil midir?**

Eğer C veya C++ gibi bir dil ile program yazarsanız programınızı derlemek zorunda kalırsınız. Bu Derleme işlemi yazdığınız kodun makine tarafından anlaşılabilir olmasını sağlar yani makine koduna çevirir. Makine kodu ise, CPU tarafından doğrudan çalıştırılan talimatların temel düzeydeki bir formudur diyebiliriz. Başarılı bir derleme sonrasında çalıştırılabilir(executable) bir dosya oluşturulur. Bu dosyanın execute edilmesi durumunda ise kodunuz adım adım çalıştırılır. 

Derleme süreci 4 aşamadan oluşur:
  1. Ön işleme (Pre processing)
  2. Derleme (Compilation)
  3. Çevirme (Assembly)
  4. Bağlama (Linking)
 
Şimdi Python'ın nasıl bir dil ve genelde kafa karıştıran bu duruma açıklık getirelim. Python aslında her iki işlemi de yapar yani hem compile eder hem de yorumlar. Peki, ama nasıl? Python'a kodumuzu çalıştırmasını söylediğimizde source code bir kaç adımdan geçecektir.

1. Önce Bytecode'a derlenir.
2. Derlemeden sonra sanal makineye(Python Virtual Machine) yönlendirilir.
  
**Python Virtual Machine(PVM)**, Bytecode üzerindeki talimatların tek tek çalıştırılmasını sağlayan büyük bir döngüdür. Yani Python'ın runtime engine'idir. Kodumuzu gerçek anlamda çalıştıran bileşendir. Teknik olarak python yorumlayıcısının son adımıdır.

```python
def foo(x):
  return(x + 5)
foo(3)
```
Yukarıdaki gibi bir kaynak kodumuz olduğunu varsayarsak çalışma sırası şu şekilde olacaktır:
  
**source code**(.py)  **->**   **bytecode**(.pyc)  **->**    **Execution**(pvm)
 
Peki Bytecode nedir? **Bytecode**, kaynak kodumuzun düşük seviyeli ve platform bağımsız(low-level platform-independent) temsilidir. (Not: **Python Bytecode binary machine code değildir.**) Bytecode, orijinal source code'dan çok daha hızlı bir şekilde çalıştırılabilmektedir. Python bunun için **.pyc** uzantılı bir dosya oluşturur. Ve programımızı bir sonraki çalıştırmamızda Python bu **.pyc** dosyasını yükleyecek ve kaynak kodumuzda herhangi bir değişiklik olmadığı sürece de derleme(compilation) aşamasını atlayacaktır. Python bunu anlamak için otomatik olarak kaynak kodun zaman bilgisini(timestamp) ve bytecode'u kontrol eder. Eğer kaynak kodu tekrar kaydederseniz(resave) otomatik olarak bytecode'a çevirecektir ve daha sonra çalıştırmak istediğinizde bu bytecode üzerinden çalıştıracaktır. Ayrıca Python bu bytecode'u otomatik olarak sistem hafızasına(system memory) yazacaktır ve derlenen bytecode memory'den yorumlanacaktır.

Özetlemek gerekirse, aslında python önce kodumuzu bytecode'a derleyecektir daha sonra bu bytecode'u yorumlayacaktır. Kodda yapılan her değişiklik sonrası tekrar bytecode generate edecektir. Bu kısmın artık biraz daha iyi anlaşılacağını düşünüyorum. ve Bu bölümü burada bitiriyorum. Bir sonraki yazımızda görüşmek üzere. :)

