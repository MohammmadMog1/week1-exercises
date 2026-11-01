# Git Merge vs. Rebase: Summary Analysis

في هذه التجربة، قمت بلمس الفرق بين أمرين أساسيين في نظام Git وهما الـ merge والـ rebase باستخدام فرعين تجريبيين:

اولاً انشات فرعين هما merge-branch و rebase-branch وتم انشاء داخل كل فرع منهم ملفات للتجربة وهي merge-file.txt و rebase-file.txt.

**عملية الدمج (Merge)**: عند دمج الفرع merge-branch في فرع main الرئيسي، لم يتم تغيير تاريخ الـ commit بل انشا commit جديد (merge commit)

**عملية الـ Rebase**: في المقابل، عند إجراء rebase للفرع rebase-branch على الـ main، اعاد تطبيق فرق الـ commits الفرق بين الفرعين فوق احدث commit في الـ main.

التعليمات المستخدمة:

```
for merge:
git merge merge-branch

for rebase:
git checkout rebase-branch
git rebase main
git checkout main
```
