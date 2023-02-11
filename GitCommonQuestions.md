

# Git'e İlişkin Sorular ve Yanıtları.

##### 1.Soru: Remote repositoryde bulunan commitler nasıl geri alınır

> Bir commit'i geri almak için $ git'te "$ git revert" komutunu kullanabilirsiniz. Bu komut, verilen commit'in tüm değişikliklerini geri alır ve aynı zamanda bir yeni commit oluşturur, bu sayede geri alınan değişikliklerin geçmişte kaydedilmiş olduğu görülebilir.

>Aşağıdaki adımları takip ederek, bir remote repository'deki bir commit'i geri alabilirsiniz:
>
 ```bash
 1-) Local repository'nizi güncelleştirin: 
 $ git fetch 
 ```

 ```bash
 2-) Geri almak istediğiniz commit'e giden branch'i checkout edin: 
 $ git checkout <branch-name>
 ```


 ```bash
 3-) Commit'i geri alın: 
 $ git revert <commit-hash>
 ```
 ```bash
 4-) Değişiklikleri remote repository'ye gönderin:
 $ git push origin <branch-name>
 ```

>Bu adımlar, remote repository'deki bir commit'i geri almanıza olanak tanır.

---


#####  2.Soru:  Git de Head kavramı neyi ifade eder.

 
 >  "HEAD"  git terminolojisinde bir pointer olarak tanımlanır ve şu anda işlenen branch'in en son commit noktasını gösterir. HEAD her zaman işlenen branch'in en son commit noktasına işaret etmelidir ve branch değiştiğinde HEAD de değişir.

 >  HEAD, aynı zamanda, bir  git repository'sinde bulunan tüm branch'ler arasında geçiş yapmanıza olanak tanır. Eğer başka bir branch'e geçmek isterseniz, sadece  git checkout komutunu kullanarak branch ismi vermeniz yeterlidir ve HEAD otomatik olarak en son commit noktasına işaret etmek üzere güncellenecektir.

 >  Özet olarak, HEAD, git terminolojisinde, şu anda işlenen branch'in en son commit noktasını gösterir ve repository'deki tüm branch'ler arasında geçiş yapmanıza olanak tanır.

---

#####  3.Soru: Git de Amend komutu kullanıldıktan sonra gelen ekrandan nasıl çıkılır


>  git amend komutunu kullandıktan sonra, düzenleme ekranından çıkmak için aşağıdaki adımları izleyin:


- Düzenlemelerinizi yapın ve  git veritabanına ekleyin.


- Değişiklikleri kaydetmek istiyorsanız, dosyayı kaydedin ve :wq veya :x komutunu kullanın. Bu, nano veya vim gibi bir metin düzenleyici kullanıyorsanız, düzenleme ekranından çıkmanıza olanak tanır.

- Değişiklikleri kaydetmeden çıkmak istiyorsanız, :q! komutunu kullanın. Bu, $ git veritabanındaki son commit mesajını veya dosyalarını değiştirmeye çalıştığınız değişiklikleri yok sayar.


>  Not:  git amend komutunu kullanarak değiştirmeye çalıştığınız veritabanının herhangi bir branch'ına push edilmemiş olması önemlidir, aksi takdirde çalışmayabilir ve hata mesajı alabilirsiniz


#####  4.Soru: Değişikliklerim Stage'e geçmiyor

> Bulunduğunuz dizini kontrol ediniz.


#####  5.Soru: Remote Repository ile Local Repository farklı histor'e sahipse ne yapılabilir.

Yöntem 1:

```bash 
$ git pull origin master --allow-unrelated-histories
```

>"git pull origin master --allow-unrelated-histories" komutu, remote repository'deki "origin" adındaki depo ile yerel repository arasındaki "master" branch'ini birleştirmeye çalışır. "--allow-unrelated-histories" seçeneği, Git'in normal olarak iki farklı repository arasında birleştirme yaparken, repository'lerin bağlantısız olduğu veya birbirine benzer bir geçmişe sahip olmadığı durumlarda hata vermesini engellemeyi amaçlar.

>Bu komut, repository'lerin ilk kez birleştirilmeye çalışıldığı veya repository'ler arasında çok fazla farklılık olduğu durumlarda kullanılabilir. Ancak, "allow-unrelated-histories" seçeneği kullanılması, repository'ler arasındaki çatlamaları veya konflikleri ortaya çıkarabilir, bu nedenle kullanılmadan önce dikkatli bir şekilde düşünülmelidir. Eğer mümkünse, repository'ler arasında aynı branch adı kullanılması ve branch'ler arasındaki aynı dosyaların birleştirilmesi önerilir.

Yöntem 2 :

```bash 
$ git push origin -f
```

>"git push origin -f" komutu, Git'in yerel repository'nin remote repository'ye güncellemesine izin verdiği ancak remote repository'nin eski verilerini silip yerine yerel repository'nin verilerini koymasına izin verir. "f" seçeneği "force" anlamına gelir ve Git'in remote repository'nin eski verilerinin bozulmamasını veya kayıp olmamasını garanti etmemesine izin verir.

>Bu komutun kullanımı genellikle tehlikeli ve kullanılmamalıdır, çünkü remote repository'deki eski veriler tamamen kaybedilebilir ve geri alınamaz. Eğer bir branch'in içeriği değiştirildi ve bu değişiklik remote repository'deki branch ile eşleşmezse, bu komut kullanılabilir. Ancak, bu durumda diğer geliştiricilerin çalışmasının etkilenebileceği veya kolayca takip edilemeyen bir durum ortaya çıkabilir.

>Bu nedenle, "git push origin -f" komutunu sadece bilgi sahibi olduğunuz ve ne yaptığınızı anladığınız durumlarda kullanın ve genelde "git push --force-with-lease" komutunu tercih edin.


#####  6.Soru: Stash ne zaman lazım olur.

>Git versiyon kontrol sisteminde, "commit etmek" ve "stash etmek" arasındaki fark, değişikliklerin nasıl saklandığı ve ne zaman geri kullanılabileceğidir.

>"Commit etmek", değişikliklerin git veritabanına kaydedilmesi ve bu değişikliklerin geçmişinin sürekli olarak tutulması anlamına gelir. "Stash etmek" ise, değişikliklerin geçici olarak saklanması anlamına gelir ve daha sonra geri yüklenerek kullanılabilir.

>Örneğin, bir projede çalışırken, aynı anda başka bir branch'e geçmek isteyebilirsiniz. Ancak, mevcut branch'deki değişiklikler henüz kaydedilmedi ve "commit" etmek istemeyebilirsiniz. Bu durumda, değişiklikleri "stash" etmek, çalışma dizinini temiz hale getirmenizi ve başka bir branch'e geçmenizi sağlar. Daha sonra, "stash" edilen değişiklikler "git stash apply" komutu ile geri yüklenebilir.



#####  7.Soru: remote branchi nasıl senkronize edebilirim.

>Remote repository'deki bir branch'ı yerel repository'ye senkronize etmek için aşağıdaki adımları izleyebilirsiniz:

1- Remote repository'nin en son durumunu çekin:

```bash 
$ git fetch origin
```
2- Yerel repository'de remote branch'ın bir kopyasını oluşturun:

```bash 
$ git checkout -b <local-branch-name> origin/<remote-branch-name>
```
<local-branch-name>: Yerel olarak oluşturmak istediğiniz branch'ın adıdır.
<origin/<remote-branch-name>: Kopyalanmasını istediğiniz remote branch'ın adıdır. origin burada remote repository'nin adıdır.

3- Yerel repository'deki değişiklikleri remote repository'ye gönderin:

```bash 
$ git push origin <local-branch-name>
```

>Bu adımlar, remote repository'deki remote-branch-name branch'ını yerel repository'deki local-branch-name branch'ına senkronize etmenizi sağlar. Senkronizasyon esnasında remote repository'deki değişiklikler yerel repository'ye aktarılır ve yerel repository'deki değişiklikler remote repository'ye gönderilir.


#####  8.Soru: git branch master upstreambranch -f   ne anlama gelir?

>git branch master upstreambranch -f komutu, master branch'ını upstreambranch branch'ına senkronize etmenizi sağlar ve -f seçeneği bu senkronizasyonu zorunlu hale getirir.

>Bu komut, master branch'ını upstreambranch branch'ındaki en son değişikliklerle güncellemenizi sağlar. Eğer master branch'ında değişiklikler varsa, bu değişiklikler silinecektir ve upstreambranch branch'ındaki değişiklikler master branch'ına eklenecektir.

>-f seçeneği, mevcut branch'daki değişiklikleri zorla güncellemenizi sağlar. Eğer branch'deki değişiklikleri kaydetmek istiyorsanız, bu seçeneği kullanmamanız önerilir.

#####  9.Soru: git rebase   ne anlama gelir?

>Git rebase, Git veritabanındaki bir branch'ın tarihçesini değiştirmek ve diğer branch'lar ile daha uyumlu hale getirmek için kullanılan bir işlemdir. Bu işlem, branch'ın başlangıç noktasını değiştirerek veya branch'ın tarihçesindeki bazı commit'leri silmek, değiştirmek veya taşımak suretiyle branch'ın tarihçesini yeniden oluşturur.

>Rebase işlemi, branch'ın tarihçesi güncellendiğinde ve diğer branch'lar ile daha uyumlu hale geldiğinde, merge işlemi yapmak için daha kolay hale gelir. Rebasing ayrıca branch'ın tarihçesi daha okunabilir ve daha kolay anlaşılır hale gelir.

>Rebase işleminin nasıl yapılacağı ve ne zaman kullanılması gerektiği konusunda dikkatli olunması gerekir, çünkü bu işlem veritabanının geçmişini değiştirebilir ve diğer branch'larla oluşabilecek çakışma sorunlarına yol açabilir. Ayrıca, rebase işlemi yapıldıktan sonra, branch'ın tarihçesi değiştiği için push etmek veya diğer branch'larla paylaşmak için dikkatli olunması gerekir.

#####  10.Soru: git rebase yapıldıktan sonra yapılan önceki commitler silinir mi?

>Hayır, Git rebase işleminde yapılan önceki commit'ler silinmez. Ancak, branch'ın tarihçesi değiştirilir ve branch'ın başlangıç noktası değişebilir. Bu, branch'ın tarihçesindeki bazı commit'lerin silinmiş, değiştirilmiş veya taşınmış görünebilmesine neden olabilir.

>Rebase işlemi sırasında, branch'ın tarihçesi yeniden oluşturulur ve branch'ın başlangıç noktası değiştirilir. Bu, branch'ın tarihçesindeki bazı commit'lerin silinmiş, değiştirilmiş veya taşınmış görünebilmesine neden olabilir. Ancak, aslında yapılan şey branch'ın tarihçesinin yeniden oluşturulmasıdır ve bu işlem branch'ın tarihçesindeki bazı commit'lerin silinmesine neden olmaz.

>Rebase işlemi, branch'ın tarihçesini daha okunabilir ve daha kolay anlaşılır hale getirmek için kullanılabilir, ancak veritabanının geçmişini değiştirebilir ve diğer branch'larla oluşabilecek çakışma sorunlarına yol açabilir. Bu nedenle, rebasing yapmadan önce dikkatli bir şekilde düşünülmesi ve yapılması gerekir.

#####  10.Soru: bir den fazla merge geri alınır mı ?

>Evet, Git'te bir veya daha fazla merge işlemini geri almak mümkündür. Bunu yapmak için aşağıdaki adımları izleyebilirsiniz:

- Git log komutunu kullanarak merge işleminin yapıldığı commit'in hash değerini bulun.

- git revert <commit-hash> komutunu kullanarak merge işlemini geri alın. Bu, merge işleminin tersini yapar ve önceki duruma döner.

- Eğer bir veya daha fazla merge işlemini geri almak istiyorsanız, adım 1 ve 2'yi tekrar edin ve istediğiniz merge işlemlerinin tüm hash değerlerini girin.

>Not: Git revert komutu sadece son değişiklikleri geri alır ve veritabanının geçmişini değiştirmez. Ayrıca, geri alınan merge işlemlerinin yapıldığı branch'lar ve diğer branch'lar arasındaki ilişkiler de değişmeyebilir. Git'te merge işlemlerini tamamen geri almak ve veritabanının geçmişini değiştirmek istiyorsanız, git reset veya git rebase gibi diğer komutlar kullanabilirsiniz.



#####  11.Soru: remote repository commit geçmişi nasıl değiştirilir ?

>Remote depo commit geçmişini değiştirmek, yapılan bir işlem olarak görülebilir ve biraz riskli olabilir. Bunun yanı sıra, yapılan bir değişiklik genellikle diğerlerinin çalışmasını etkileyebilir. Bu nedenle, bu işlemleri yapmadan önce dikkatli bir şekilde düşünmeniz ve gereken önlemleri almanız önerilir.

- İlgili remote depoyu klonlayın:

```bash 
$ git clone <url>
```

- Değiştirmek istediğiniz commitin öncesine gitin:

```bash 
$ git checkout <commit-sha>
```

- Yeni bir branch oluşturun ve bu branch'e geçin:

```bash 
$ git checkout -b <new-branch-name>
```

-Değiştirmek istediğiniz commitin içeriğini değiştirin ve yeni bir commit yapın:
```bash 
$ git commit --amend
```

- Değiştirdiğiniz branch'i remote depoya push edin:
```bash 
$ git push origin <new-branch-name>
```
-Remote depodaki orijinal branch'e yeni branch'inizi merge edin veya pull request yapın.

>Bu işlemleri yaparken, git reflog ve git rebase gibi diğer git araçlarını da kullanabilirsiniz. Ancak, bu araçlar daha ileri seviye git kullanımını gerektirir ve kullanmadan önce açık bir şekilde anlamanız gerekir. Ayrıca, bu işlemlerin yanlış yapılması durumunda verilerinizin kaybına neden olabileceği için çok dikkatli olmanız gerekir.