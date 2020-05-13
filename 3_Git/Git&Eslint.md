# 学git的知识点汇总
git对象
树对象
提交对象

工作区
暂存区
版本库

本地分支
远程跟踪分支
远程分支
### Git远程仓库
本地分支
远程跟踪分支
远程分支

#### 协同合作
场景:push的时候会建立一个远程跟踪分支
git branch -u 分支名 :建立当前分支与远程跟踪分支的关联
git pull 拉取分支内容


git branch -vv  :查看远程跟踪分支
如果是本地没有分支
git checkout --track 跟踪分支名

冲突处理:
场景:两个人同时更新同一个文件
报冲突:
	pull 拉取内容;
	修改文件内容
	git add 解决冲突
### 新建分支
git checkout -b iss53
#### Fork
如果想调试别人的代码,Fork到自己本地仓库
### Eslint
代码格式检查工具
#### 使用Eslint
npm init 创建项目
npm i -D eslint 安装
配置package.json文件
    "scripts": {
    "lint:create": "eslint --init"
    "lint": "eslint src",
    "lint:fix": "eslint src --fix"
    
   }
    eslint src : 自动检查项目下src目录
    eslint --init:生成 .eslintrc.js 文件。提供编码规
    eslint src --fix :自动修复基础问题
新建src和src下js文件
npm run lint 检查文件
#### 配置eslintrc和editorConfig配置文件
.eslintrc.js 自定义eslint规则
.eslintignore :忽略eslint规则的文件
.editorconfig 配合eslint的编辑规则;vscode下载插件EditorConfig for VS Code

//.eslintrc.js
  rules: {
    "object-shorthand": 2,
    "prefer-arrow-callback":1,
    "no-trailing-spaces":2,
    "no-shadow": 1
  }

### husky与Git结合
    Git hooks 钩子
    让代码在没有通过Eslint的情况下禁止提交。
#### 使用
在当前项目目录下:
git init在Git仓库初始化后安装(必须是之后)
npm install -D husky
添加package.json文件
{
  "husky": {
    "hooks": {
      "pre-commit": "npm test",
      "pre-push": "npm test",
      "...": "..."
    }
  }
}
配置 .gitignore ; 填写无需纳入 Git 的管理的目录和文件名
测试:git commit如果没有通过eslint检测无法提交


