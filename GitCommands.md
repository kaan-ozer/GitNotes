# Git Notes

Local repository'i oluşturur (. git).
```bash 
$ git init
```

Yeni eklenen veya üzerinde değişiklik yapılan dosyaları staged ortamına göndermek için kullanılır.
```bash 
$ git add

```
 Tüm dosyaları toplu olarak staged ortamına göndermeye yarar.
```bash 
$ git add .
```
Commit, staged ortamına alınan dosyaların Local Repository’e gönderilmesidir.
```bash 
$ git commit -m 'message'
```
remote repository adresi tanımlamaya yarar.
```bash 
$ git remote add origin https://...
```

remote repository adresini güncellemeye yarar.
```bash 
$ git remote set-url origin https://...
```

Tüm tanımlı remote repository adresslerini gösterir.
```bash 
$ git remote -v
```

Tüm tanımlı branchleri gösterir.
```bash 
$ git branch
```

Tüm tanımlı branchleri gösterir, remote branchler dahil .
```bash 
$ git branch -a
```

Branch silmeye yarar.
```bash 
$ git branch -d <localBranchName>
```


Branch oluşturmayı sağlar.
```bash 
$ git branch <localBranchName>
```


Belli bir branche $ gitmeyi sağlar.
```bash 
$ git checkout <localBranchName>
```

Branch oluşturduktan sonra o branch'e $ gitmemizi sağlar (üstteki iki komutun birleşimi).
```bash 
$ git checkout -b <localBranchName>
```

Projenin güncel durumunu gösterir.
```bash 
$ git status
```

Commit geçmişini gösterir.
```bash 
$ git log
```

Son commiti gösterir.
```bash 
$ git log -n 1
```
İstenen branchin remote repository'e gönderilmesini sağlar(-u ilk  pushladığımızda kullanılır).
```bash 
$ git push -u origin <localBranch>
```

Dosya oluşturma komutudur.
```bash 
$ git >> README.md
```

"git pull" komutunu kullanarak, remote repository'deki en son değişiklikleri yerel repository'nize indirebilir ve mevcut branch'inize birleştirebilirsiniz.
```bash 
$ git pull <remote> <remoteBranch>
```

"git fetch" komutu, remote repository'deki değişiklikleri local repository'nize (yerel depo) indirir ve "git merge" komutu ile mevcut branch'inize birleştirilir. 
```bash 
$ git fetch <remote> <remoteBranch>
```

Son committe değişilik yapmamızı sağlar.
```bash 
$ git commit amend 
```

Son commit'in mesajını değiştirme olanağı sağlar.
```bash 
$ git commit --amend -m ''
```

Id si girilen commit'in etkilerini kaldırıp bunu yaptığını gösteren bir commit ekler.
```bash 
$ git revert ID
```

Bu id'li commite gidip yukarsını siler
```bash 
$ git reset --hard <CommitId>
```

Bu dosya için commitId1 ile commitId2 arasındaki değişiklikleri gösterir.
```bash 
$ git diff <commitId1> <commitId2> <fileName(like: index.html)>
```

En üstteki stashdeki değişikleri uygular ve stash listten o stashi kaldırır.
```bash 
$ Git stash pop 
```

En üstteki stashdeki değişikleri uygular ve stash listten o stashi kaldırır.
```bash 
$ Git stash pop 
```


