### 〇、开头
- **下载**：官网 `git-scm.com` 下载对应系统的版本，下一步\*n
- **配置**：重要，后续要找到操作者
```bash
git --version # 显示版本号 → 验证安装完成
git config --global user.name "你的名字" # 全局配置用户名
git config --global user.email "你的邮箱" # 全局配置邮箱
```
### 一、本地操作
#### 1. 初始化
- 初始化：在当前项目目录创建`.git`目录（包含项目历史版本，误删）
- 确认完成：检查是否存在`.git`文件（`ls -a`或`dir -a`）
#### 2. 记录修改
- 标记：`add`，在本目录git中添加要追踪的项目
- 重捕：`commit`，记录修改情况
```bash
git init # 初始化
git add [文件|目录|.] # 标记, "."表示整个当前目录
git commit -m [描述修改内容(主观)] # 重捕
git log # 看本地commit历史
git status # 看本地有没有未commit的改动
```
### 二、云端操作
#### 0. 云端操作目的
- 避免本地硬件损坏导致项目丢失 → 云端备份
- 常用云端：国内有Gitee（码云）、GitCode（CSDN的）国外有GitHub、GitLab
#### 1. 云端初始化
- 在云端上新建一个仓库（==不要==初始化`README`）
- 仓库地址：形如 `https://gitee.com/你的用户名/仓库名.git`
- 远程添加指定代号（默认`origin`）的仓库，并验证是否关联成功
#### 2. 本地与云端的传输（云端→云→比我们的位置高）
- 本地→云端：`push`（`main`是元首分支名字，老版本可能是`master`）
- 云端→本地：`pull`（获取+合并到本地，建议`push`前先`pull`）
```bash
git remote add origin [仓库地址] # 关联远程仓库和本地项目
git remote -v # 看到fetch和push两行地址，说明关联上了
git push -u origin main # 第一次 push → 建立本地和远程的关联
git push origin main # 之后的 push
git pull origin main # 每次pull
git pull origin master --allow-unrelated-histories # pull(允许合并不相关历史，解决冲突)
```
### 三、分支操作（留着本地）
#### 0. 分支目的（开发过程）
- 元首分支 → 影响当前功能
- 新分支 + 开发完毕后合并 → 开发过程当前功能正常使用
#### 1. 基本命令
```bash
git branch # 查看所有分支（*号表示当前所在分支）
git branch feature-xxx # 新建分支
git checkout feature-xxx # 切换分支
git checkout -b feature-xxx # 新建并切换（常用）
git merge feature-xxx # 把feature-xxx合并到当前分支
git branch -d feature-xxx # 删除分支
```
#### 2. 使用规则
1. 保持main分支干净，不在`main`上开发
2. 功能分支命名规范$$\begin{cases}\text{feature}\to新功能\\\text{bugfix}\to修\space\text{bug}\\\text{hotfix}\to\text{线上紧急修复}\end{cases}$$
3. 合并前先pull：在合并分支或`push`之前，先`pull`到`main`，把远程最新的更新拉到本地，避免多人`push`导致的冲突
4. 冲突解决方法
	1. 找到冲突文件（Git会告诉你）
	2. 打开文件，找到类似`3.`的标记
	3. `<<<<<<< HEAD 你的代码 ======= 别人的代码 >>>>>>> branch-name`
	4. 删除标记，保留你想要的代码（或者两边的都保留一部分）
	5. 重新 `add`、`commit`、`push`
### 四、结语（实践）
- 打开终端，创建新目录，跑一遍今天学到的命令
- 犯错没关系，出了问题 `rm -rf .git` 重新来过。
- 本文参考[Git操作-半小时从入门到精通](https://zhuanlan.zhihu.com/p/2031653489152112069)