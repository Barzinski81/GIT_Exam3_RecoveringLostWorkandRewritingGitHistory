```
mkdir lost-work
cd lost-work/
git init

echo "Intial desing" > index.html
git add index.html
git commit -m "Initial Design"

git remote add origin git@github.com:Barzinski81/GIT_Exam3_RecoveringLostWorkandRewritingGitHistory.git

git push -u origin main

git checkout -b development

echo "Work done on Monday" > index.html
git add index.html
git commit -m "Work done on Monday"

echo "Work done on Tuesday" >> index.html
git add index.html
git commit -m "Work done on Tuesday"

echo "Work done on Wednesday" >> index.html
git add index.html
git commit -m "Work done on Wednesday"

echo "Work done on Thursday" >> index.html
git add index.html
git commit -m "Work done on Thursday"

echo "Work done on Friday" >> index.html
git add index.html
git commit -m "Work done on Friday"

$ git log --oneline
dfe0997 (HEAD -> development) Work done on Friday
920962e Work done on Thursday
2059aa4 Work done on Wednesday
f8ea7cf Work done on Tuesday
84ec212 Work done on Monday
d1ad1d2 (main) Initial Design

git push -u origin development

$ git reset --hard f8ea7cf
HEAD is now at f8ea7cf Work done on Tuesday

$ git push origin development --force
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To github.com:Barzinski81/GIT_Exam3_RecoveringLostWorkandRewritingGitHistory.git
 + dfe0997...f8ea7cf development -> development (forced update)

$ git reflog
f8ea7cf (HEAD -> development, origin/development) HEAD@{0}: reset: moving to f8ea7cf
dfe0997 HEAD@{1}: commit: Work done on Friday
920962e HEAD@{2}: commit: Work done on Thursday
2059aa4 HEAD@{3}: commit: Work done on Wednesday
f8ea7cf (HEAD -> development, origin/development) HEAD@{4}: commit: Work done on Tuesday
84ec212 HEAD@{5}: commit: Work done on Monday
d1ad1d2 (origin/main, main) HEAD@{6}: checkout: moving from main to development
d1ad1d2 (origin/main, main) HEAD@{7}: commit (initial): Initial Design

$ git reset --hard dfe0997
HEAD is now at dfe0997 Work done on Friday

$ git reflog
dfe0997 (HEAD -> development) HEAD@{0}: reset: moving to dfe0997
f8ea7cf (origin/development) HEAD@{1}: reset: moving to f8ea7cf
dfe0997 (HEAD -> development) HEAD@{2}: commit: Work done on Friday
920962e HEAD@{3}: commit: Work done on Thursday
2059aa4 HEAD@{4}: commit: Work done on Wednesday
f8ea7cf (origin/development) HEAD@{5}: commit: Work done on Tuesday
84ec212 HEAD@{6}: commit: Work done on Monday
d1ad1d2 (origin/main, main) HEAD@{7}: checkout: moving from main to development
d1ad1d2 (origin/main, main) HEAD@{8}: commit (initial): Initial Design


$ cat index.html
Work done on Monday
Work done on Tuesday
Work done on Wednesday
Work done on Thursday
Work done on Friday

git rebase -i HEAD~5
```

<img width="634" height="151" alt="image" src="https://github.com/user-attachments/assets/c926a285-f948-4de0-9760-4b62282f8c0e" />

<img width="617" height="150" alt="image" src="https://github.com/user-attachments/assets/ffd91150-81bc-4f31-937c-e084b2ee90f7" />

<img width="446" height="432" alt="image" src="https://github.com/user-attachments/assets/81a60c95-e555-49ff-8bf3-b10409372cf4" />

```
[detached HEAD a4a88e1] Weekly work
 Date: Sun Jul 27 12:03:42 2025 +0300
 1 file changed, 5 insertions(+), 1 deletion(-)
Successfully rebased and updated refs/heads/development.

$ git log --oneline
a4a88e1 (HEAD -> development) Weekly work
d1ad1d2 (origin/main, main) Initial Design

$ git push origin development --force-with-lease
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 16 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 305 bytes | 305.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To github.com:Barzinski81/GIT_Exam3_RecoveringLostWorkandRewritingGitHistory.git
 + f8ea7cf...a4a88e1 development -> development (forced update)
```
