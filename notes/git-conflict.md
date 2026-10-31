# Git Merge Conflict

## 1. Overview

هذا المستند يشرح تجربتي العملية مع تعارضات الدمج (Merge Conflicts) في Git.

2. How the Conflict Happened

الإعداد الأولي: بدأت العمل من الفرع الرئيسي (main).
وانشات الملفات المطلوبة في التمرين.

التعلميات:

```
 git init
  git status

  C:\Users\ASUS\OneDrive\Desktop\BackEnd-InterShip\Week1\git-history (master)
 git branch -m master main

C:\Users\ASUS\OneDrive\Desktop\BackEnd-InterShip\Week1\git-history (main)
git remote add origin https://github.com/MohammmadMog1/week1-Exercises.git


 touch README.md
 git add README.md
 git commit -m "Added README.md File"
git push -u origin main

mkdir notes
C:\Users\ASUS\OneDrive\Desktop\BackEnd-InterShip\Week1\git-history (main -> origin)
ls
notes/  README.md

cd notes\
touch http.md
cd ..
git add  notes\http.md
git commit -m "Added notes/http.md File"
git push

mkdir src
cd src
touch hello.js
cd ..
git add .
git commit -m "Added src/hello.js File"
 git push
```

إنشاء فرع جديد: قمت بإنشاء فرع جديد باسم feature/update-hello.js والانتقال إليه.

```
git checkout -b feature/update-hello.js
 git branch
* feature/update-hello.js
  main

  git push origin feature/update-hello.js
```

التعديل على الفرع الرئيسي: قمت بتعديل ملف hello.js على فرع main وأضفت الكود، ثم قمت بالحفظ ورفع التعديلات.

```js
const message = "hello";
console.log(message);
```

التعديل على الفرع الجديد: انتقلت إلى الفرع feature/update-hello.js وعدّلت على نفس الجزء من ملف hello.js بكود مختلف، ثم رفعت التعديلات.

```js
const message = "This line was added on a feature branch.";
console.log(message);
```

الدمج وحل التعارض: عند محاولة دمج الفرع feature/update-hello.js مع main حدث تعارض (Merge Conflict) بسبب تعديل نفس الملف في الفرعين.

```
C:\Users\ASUS\OneDrive\Desktop\BackEnd-InterShip\Week1\git-history\src (main -> origin)
λ git merge feature/update-hello.js
Auto-merging src/hello.js
CONFLICT (content): Merge conflict in src/hello.js
Automatic merge failed; fix conflicts and then commit the result.
```

الرفع النهائي: قمت بحل التعارضات يدوياً في ملف hello.js ثم قمت بحفظ التغييرات، وإنشاء التزام الدمج (Merge Commit)، ورفعه في النهاية إلى المستودع.

```
git add .
git commit -m "fix(hello): resolve message merge conflict
git push

```

حذف الـ branch: حذفت الفرع بعد بعد حل الـ conflict.

```
git branch -d feature/update-hello.js

 git branch
* main
```

**ملاحظة**: لم يتم حذف الـ branch من GitHub للمرحعة من قبل المشرف.
