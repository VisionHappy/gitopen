# GitFlowDemo
Git Flow实例演示

1. 在Github上创建一个项目，并设置好ssh

   https://github.com/sunwenquan/GitFlowDemo

2. clone项目

   ```
   git@github.com:sunwenquan/GitFlowDemo.git
   ```

3. 使用SourceTree打开项目

4. 仓库->Git flow->初始化仓库

   ![初始化仓库](images/2C152E29-D433-4D30-B3C4-E4F002D97469.png)

5. 创建develop分支

   ```
   git branch develop
   git push -u origin develop  
   ```

6. 在develp分支开发新功能——introduction

   ```bash
   git checkout -b introduction develop
   git push -u origin introduction
   ```

7. 在introduction分支下修改文件

   ```bash
   git checkout introduction
   touch introduction.md
   git add introduction.md
   git commit -m "add introduction.md"
   ```

8. 完成新功能的开发

   ```bash
   git pull origin develop
   git checkout develop
   git merge --no-ff introduction
   git commit -m "添加introduction"功能
   git push origin develop
   
   # 删除功能分支
   git branch -d some-feature
   # If you pushed branch to origin:
   git push origin --delete some-feature    
   ```

   此时查看Github上的分支，发现develop分支的内容变多了，master分支的内容并未改变，因为我们是在develop分支上做的变更。

9. 删除introduction分支

   ```bash
   git branch -d some-feature
   git push origin --delete introduction    
   ```

10. Release

    ```bash
    git checkout -b release-0.1.0 develop
    git commit -m "release 0.1.0"
    
    # 完成release后，把release版本合并到master
    git checkout master
    git merge --no-ff release-0.1.0
    git commit -m "添加introduction功能"
    git push
    # 完成release后，把release版本合并到develop
    git checkout develop
    git merge --no-ff release-0.1.0
    git commit -m "添加功能"
    git push
    # 删除release
    git branch -d release-0.1.0
    # If you pushed branch to origin:
    git push origin --delete release-0.1.0   
    
    # 为master打一个标签
    git tag -a v0.1.0 master
    git push --tags
    ```

    





