# Git Nasıl Kullanılır
----

Git bir versiyon kontrol sistemidir ve GitHub ile aynı şey değildir. 
Projenizde ne zaman ve nerde değişiklikler yaptığınızı görebilirsiniz.
İstediğiniz zaman projenizin eönceki versiyonlarına dönebilirsiniz.
Takım çalışmasında kolaylık sağlar.
Proje farklı dallara ve bölümlere ayrılabilir.

### Git vs. GitHub

* Git ile kaynak kodunuzda yaptığınız değişiklerin geçmişini takip eder ve versiyonlarınızı yönetmenizi sağlar.
* Github projelerin depolandığı uzak sunucudur.

[İndirme linki](https://git-scm.com/downloads)

## Temel Git Komutları
----

![](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fqph.fs.quoracdn.net%2Fmain-qimg-3aa29f29ede6a8245b6964f663c60339&f=1&nofb=1)

***Stage area** geçiş/index bölgesi olarak geçer. Yapılan değişikliklerin repoya gönderilmeden önce kaydedildiği yerdir. Buraya projenizdeki istediğiniz dosyayı ekleyenilirsiniz. 
Göndermek istediğiniz tüm değişiklikler buraya eklenmelidir.*
<br/><br/>

Öncelikle git yapılandırmasını yapalım. Bu yapılan değişikliklerin kimin tarafından yapıldığını anlamakta yardımcı olur. <br/>

`  git config --global user.name "Ad Soyad/Kullanıcı adı"  ` <br/>
`git config --global user.email "blabla@gmail.com"` <br/>

<br/>

Bunları görebilmek için  `git config --list`  komutunu kullanabilirsiniz. <br/>

Sıra local repository oluşturmakta. Önce projeyi oluşturmak istediğiniz dizine geçin, klasörüsünüzü oluşturun ve bu klasöre gidin. Git Bash ile yapabilirsiniz: <br/>
`cd Dizin ` <br/>
` mkdir Proje` <br/>
`cd Proje` <br/>
<br/>

Bu klasörün bir git projesi olduğunu belirtmeliyiz: <br/>
`git init` <br/>
Bundan sonra .git adında gizli bir klasör eklenmiş olacaktır. <br/>
Dosyalar ekleyip üzerinde değişiklikler yaptıktan sonra bu dosyaların durumunu `git status` diyerek görebilirsiniz.  <br/>









































