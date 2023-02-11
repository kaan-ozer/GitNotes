

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