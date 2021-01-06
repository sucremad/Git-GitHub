# Git Nasıl Kullanılır


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


![](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fqph.fs.quoracdn.net%2Fmain-qimg-3aa29f29ede6a8245b6964f663c60339&f=1&nofb=1)

***Stage area** geçiş/index bölgesi olarak geçer. Yapılan değişikliklerin repoya gönderilmeden önce kaydedildiği yerdir. Buraya projenizdeki istediğiniz dosyayı ekleyenilirsiniz. 
Göndermek istediğiniz tüm değişiklikler buraya eklenmelidir.*
<br/><br/>

Öncelikle git yapılandırmasını yapalım. Bu yapılan değişikliklerin kimin tarafından yapıldığını anlamakta yardımcı olur. <br/>


```
git config --global user.name "Ad Soyad/Kullanıcı adı"  
git config --global user.email "blabla@gmail.com"
```


Bunları görebilmek için  `git config --list`  komutunu kullanabilirsiniz. <br/>

Sıra local repository oluşturmakta. Önce projeyi oluşturmak istediğiniz dizine geçin, klasörüsünüzü oluşturun ve bu klasöre gidin. Git Bash ile yapabilirsiniz: <br/>

```
cd Dizin 
mkdir Proje
cd Proje
```


Bu klasörün bir git projesi olduğunu belirtmeliyiz: <br/><br/>
`git init` <br/><br/>
Bundan sonra .git adında gizli bir klasör eklenmiş olacaktır. <br/><br/>
Dosyalar ekleyip üzerinde değişiklikler yaptıktan sonra bu dosyaların durumunu `git status` diyerek görebilirsiniz.  <br/> <br/>

![](https://media.discordapp.net/attachments/694610695752515656/796119934090215484/unknown.png) <br/>

Görüldüğü gibi geçiş bölgesine eklenmemiş dosyalar var. Bunları geçiş bölgesine ekleyelim.

<br/>

Belirli bir dosyayı eklemek istiyorsanız dosyayı belirtmelisiniz. <br/>

`git add <file>` <br/>

Eğer hepsini eklemek istiyorsanız şu komut bunu sağlayacaktır. <br/>

`git add .` <br/>

Bu komutları girip tekrar `git status` dersek commit edilmeye hazır dosyaları görürüz. <br/> <br/>

![](https://cybling.files.wordpress.com/2021/01/image-2.png) <br/><br/>

Eğer değişiklikleri geçiş bölgesinden geri almak isterseniz: <br/><br/>
`git restore --stage <file>` <br/>

Peki commit ne demek? Commit işlemiyle stage bölgesindeki dosyaları kalıcı olarak git veri tabanına ekleriz. <br/>

`-m` ile yapacağınız bu değişiklerin ne olduğunu kısaca tanımlayabilirsiniz. Bu gerçekten kullanışlı olacaktır. <br/>

`git commit -m "Bazı hatalar düzeltildi."
` <br/><br/>
![](https://cybling.files.wordpress.com/2021/01/image-3.png) <br/><br/>
Yaptığınız tüm değişiklikleri git log komutu ile görebilirsiniz. <br/><br/>
![](https://cybling.files.wordpress.com/2021/01/image-4.png) <br/><br/>

`--oneline` ile kısaltılmış bir şekile dönüşsün. <br/><br/>
![](https://cybling.files.wordpress.com/2021/01/image-5.png) <br/>

Son n tane logu görmek isterseniz `git log -p -2` <br/>

Değişikliklerden vazgeçtiyseniz ve önceki versiyonlara dönmek istiyorsanız eğer commitlere atanan hash numarasını kullanarak bunu yapabilirsiniz. <br/>


```
git checkout <hash_value>
git checkout c44c02e
```
 <br/>

Kalıcı olarak commitleri geri almak isterseniz: <br/>

```
git revert <hash_value>
git revert af5bc51
```


Projenizde yapılan değişiklerin projenize nasıl etki edeceğini bilmiyorsunuz ve riskli bir durum içerisindesiniz. Asıl kodun bozulmasını istemiyorsunuz. İşte burada devreye branch denilen kavram giriyor. Branchlar pojenizi dallandırmaya yarar. Yani yaptığınız değişiklikleri A branchına yaparsanız, projede ekli olan diğer branchlardaki kod etkilenmeyecektir. <br/>

Projede var olan branchları listeyelim ve hangi brancta olduğumuzu görelim: <br/>


`git branch` <br/>

Yeni bir branch ekleyelim: <br/>

```
git branch <branchname>
git branch newbranch
```
<br/>
Başka bir brancha geçelim: <br/>

`git checkout newbranch` <br/><br/>
![](https://cybling.files.wordpress.com/2021/01/image-6.png) <br/> <br/>

Eğer başka bir branchtaki değişiklikleri bulunduğunuz branchla birleştirmek istiyorsanız merge işleminin vakti gelmiş demektir. <br/>

Önce değişiklikleri aktarmak istediğiniz branche geçiniz. Komutta değişiklikleri alacağımız branchları kullanacağız. <br/>

```
git merge <branch> <branch2>
git merge newbranch
```

<br/>

![](https://cybling.files.wordpress.com/2021/01/image-7.png) <br/><br/>

Uzak branchteki değişiklikleri indirmek için (Kodunuzda değişiklik olmaz sadece güncellemeleri görürsünüz.): <br/>


``` git fetch <remote>
git fetch <remote> <branch>

git fetch origin newbranch
git fetch blog master 
```
<br/>

_remote_: Remote bağlantı. Nasıl kurulur: <br/>

```
git remote add <isimlendir> <bağlantı>
git remote add blog https://github.com/user/Repo.git
```

### GitHub için nasıl kullanılır
GitHub’dan bir repoyu bilgisayarınıza kopyalamak isterseniz: 

```
git clone <repolinki.git>
```
Repository linkini GitHub’da repositorye geldikten sonra Code butonuna tıklayarak alabilirsiniz. <br/><br/>
![](https://cybling.files.wordpress.com/2021/01/image-8.png) <br/>

Repo bulunduğunuz dizine kopyalanacaktır.<br/>

Proje üzerinde çalışıp işlemlerini tamamladıktan sonra şu komutla güncel hali Github’a yükleyebilirsiniz: <br/>

```
git push <remote> <branch>
git push blog newbranch
```
Bu işlemden sonra GitHub’ta ‘newbranch’ ın altında projenizin güncellediğiniz hali görünecektir. <br/>


`git fetch` ve `git merge` komutlarını tek bir komuta sığdırabiliriz: `git pull`

`git pull` ile uzak repo ile local repodaki farklılıklar kontrol edilir ve değişiklik varsa bu değişiklikler local reponuza yani bilgisayarınıza indirilir.


----

[:link: Blog](https://cybling.wordpress.com/2021/01/05/git-nasil-kullanilir/)
