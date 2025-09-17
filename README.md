# Git 提交指南

## 提交信息格式规范

### 标准格式
```
<type>(<scope>): <subject>

<body>

<footer>
```

### 基本示例
```bash
git commit -m "🚀 feat(auth): add user login functionality"
git commit -m "🐞 fix(api): resolve null pointer exception in user service"
git commit -m "📚 docs(readme): update installation instructions"
```

## Type 类型说明

### 主要类型
| Type | 图标 | 说明 | 示例 |
|------|------|------|------|
| **feat** | 🚀 | 新功能 | `feat(user): add password reset feature` |
| **fix** | 🐞 | Bug 修复 | `fix(login): resolve authentication timeout` |
| **docs** | 📚 | 文档更新 | `docs(api): update endpoint documentation` |
| **style** | 💄 | 代码格式化（不影响功能） | `style(css): format button styles` |
| **refactor** | ♻️ | 重构（既不新增功能，也不修复bug） | `refactor(utils): simplify date formatting` |
| **perf** | ⚡ | 性能优化 | `perf(query): optimize database queries` |
| **test** | 🧪 | 测试相关 | `test(auth): add unit tests for login` |
| **chore** | 🔧 | 构建过程或辅助工具的变动 | `chore(deps): update dependencies` |

### 扩展类型
| Type | 图标 | 说明 | 示例 |
|------|------|------|------|
| **build** | 📦 | 构建系统或外部依赖变更 | `build(webpack): update configuration` |
| **ci** | 👷 | CI 配置文件和脚本变更 | `ci(github): add automated testing workflow` |
| **revert** | ⏪ | 回滚之前的提交 | `revert: feat(auth): add user login` |
| **merge** | 🔀 | 合并分支 | `merge: dev into main` |

## Scope 范围说明

### 常见范围
- **组件名称**: `header`, `sidebar`, `navbar`
- **功能模块**: `auth`, `user`, `payment`, `order`
- **文件类型**: `api`, `db`, `config`, `utils`
- **平台**: `ios`, `android`, `web`

### 示例
```bash
🚀 feat(auth): add OAuth2 integration
🐞 fix(payment): resolve credit card validation
📚 docs(api): update user endpoints documentation
💄 style(header): improve mobile responsiveness
```

## Subject 主题行规范

### 书写规则
- 使用动词原形开头
- 首字母小写
- 结尾不加句号
- 限制在 50 字符以内
- 使用英文（推荐）

### 良好示例
```bash
✅ add user authentication
✅ fix memory leak in image processing
✅ update API documentation
✅ remove deprecated methods
✅ optimize database queries
```

### 避免的写法
```bash
❌ Added user authentication    # 不使用过去时
❌ Fix Memory Leak             # 不要首字母大写
❌ update api documentation.   # 不要结尾句号
❌ fixed the bug that caused the application to crash when users try to login # 太长
```

## 详细格式规范

### 完整提交信息示例
```
✨ feat(auth): add JWT token authentication

- Implement JWT token generation and validation
- Add middleware for protected routes
- Update user model to include token refresh
- Add logout functionality with token invalidation

Closes #123
Breaks: changes authentication API endpoints
```

### Body 正文规范
- 解释**为什么**做这个改动，而不是**做了什么**
- 每行限制在 72 字符以内
- 可以包含多个段落
- 使用列表说明具体变更

### Footer 脚注规范
```
# 关闭 Issue
Closes #123
Closes #456, #789

# 不兼容变更
BREAKING CHANGE: authentication API has been redesigned

# 相关 Issue
Related to #456
Fixes #123
Resolves #789
```

## 实用提交命令

### 基本提交流程
```bash
# 1. 查看文件状态
git status

# 2. 添加文件到暂存区
git add .                    # 添加所有文件
git add src/auth.js         # 添加特定文件
git add *.js               # 添加所有 js 文件

# 3. 提交更改
git commit -m "✨ feat(auth): add user login functionality"

# 4. 推送到远程
git push origin main
```

### 高级提交技巧

#### 1. 交互式添加
```bash
# 部分添加文件内容
git add -p filename.js

# 交互式选择文件
git add -i
```

#### 2. 修改提交信息
```bash
# 修改最后一次提交信息
git commit --amend -m "new commit message"

# 修改最后一次提交并添加文件
git add forgotten-file.js
git commit --amend --no-edit
```

#### 3. 多行提交信息
```bash
# 方法一：使用编辑器
git commit

# 方法二：命令行多行
git commit -m "feat(auth): add user authentication" \
           -m "- Add login/logout functionality" \
           -m "- Implement JWT token handling"
```

#### 4. 临时提交（WIP）
```bash
# 工作进行中的提交
git commit -m "wip(feature): work in progress on user dashboard"

# 后续可以使用 rebase 整理提交历史
```

## 提交最佳实践

### 1. 提交频率
- **经常提交** - 每完成一个小功能就提交
- **原子性提交** - 每次提交只包含一个逻辑变更
- **避免大提交** - 不要把多天的工作放在一次提交中

### 2. 提交内容
```bash
✅ 好的提交
✨ feat(login): add email validation
🐛 fix(api): handle empty response gracefully
📚 docs(readme): update installation steps

❌ 避免的提交
feat: add login, fix bugs, update docs
fix: various fixes
update: stuff
```

### 3. 提交时机
- 功能完成且测试通过后提交
- 修复 bug 后立即提交
- 重构完成后提交
- 文档更新后提交

## 团队协作规范

### 1. 提交信息模板
创建 `.gitmessage` 文件：
```
# <type>(<scope>): <subject>
#
# <body>
#
# <footer>

# Type: feat ✨, fix 🐛, docs 📚, style 💄, refactor ♻️, perf ⚡, test 🧪, chore 🔧
# Scope: 影响范围，如 auth, api, ui 等
# Subject: 简短描述，动词原形开头，首字母小写，不超过50字符
#
# Body: 详细描述变更内容，解释为什么做这个改动
#
# Footer: 关闭的 Issue 或不兼容变更说明
```

配置使用模板：
```bash
git config commit.template ~/.gitmessage
```

### 2. Git Hooks
创建 `commit-msg` hook 验证提交信息：
```bash
#!/bin/sh
commit_regex='^(feat|fix|docs|style|refactor|perf|test|chore)(\(.+\))?: .{1,50}'

if ! grep -qE "$commit_regex" "$1"; then
    echo "Invalid commit message format!"
    echo "Format: <type>(<scope>): <subject>"
    exit 1
fi
```

### 3. 提交信息检查工具

#### Commitizen
```bash
# 安装
npm install -g commitizen cz-conventional-changelog

# 配置
echo '{ "path": "cz-conventional-changelog" }' > ~/.czrc

# 使用
git cz  # 代替 git commit
```

#### Commitlint
```bash
# 安装
npm install --save-dev @commitlint/config-conventional @commitlint/cli

# 配置 commitlint.config.js
module.exports = {
  extends: ['@commitlint/config-conventional']
};

# Husky Hook
npx husky add .husky/commit-msg 'npx --no-install commitlint --edit $1'
```

## 提交历史管理

### 查看提交历史
```bash
# 查看提交日志
git log --oneline
git log --graph --oneline --all

# 查看特定文件的提交历史
git log --follow filename.js

# 查看某个作者的提交
git log --author="张三"

# 查看特定时间范围的提交
git log --since="2023-01-01" --until="2023-12-31"
```

### 整理提交历史
```bash
# 交互式 rebase 整理最近 3 次提交
git rebase -i HEAD~3

# 压缩提交
git reset --soft HEAD~3
git commit -m "feat(auth): complete user authentication system"
```

## 常见问题解决

### 1. 提交了错误的文件
```bash
# 撤销最后一次提交，保留文件更改
git reset --soft HEAD~1

# 移除错误添加的文件
git reset HEAD wrongfile.txt

# 重新提交
git commit -m "correct commit message"
```

### 2. 提交信息写错了
```bash
# 修改最后一次提交信息
git commit --amend -m "correct commit message"
```

### 3. 忘记添加文件
```bash
# 添加忘记的文件到最后一次提交
git add forgotten-file.js
git commit --amend --no-edit
```

## 自动化工具推荐

### VS Code 插件
- **Git Graph** - 可视化 Git 历史
- **GitLens** - 增强 Git 功能
- **Conventional Commits** - 提交信息助手

### 命令行工具
- **tig** - 文本界面的 Git 仓库浏览器
- **lazygit** - 简单的 Git 终端 UI
- **gh** - GitHub CLI 工具

## 图标版提交类型速查表

### 🎨 常用提交类型
- ✨ **feat**: 新功能
- 🐛 **fix**: 修复 Bug
- 📚 **docs**: 文档更新
- 💄 **style**: 代码格式化
- ♻️ **refactor**: 重构代码
- ⚡ **perf**: 性能优化
- 🧪 **test**: 测试相关
- 🔧 **chore**: 构建/工具变更

### 🛠️ 扩展类型
- 📦 **build**: 构建系统
- 👷 **ci**: CI/CD 配置
- ⏪ **revert**: 回滚提交
- 🔀 **merge**: 合并分支

### 💡 使用建议
可以选择以下任一格式：

**格式一：图标 + type**
```bash
git commit -m "✨ feat(auth): add user login"
```

**格式二：仅 type（传统格式）**  
```bash
git commit -m "feat(auth): add user login"
```

**格式三：仅图标**
```bash
git commit -m "✨ add user login functionality"
```

推荐使用**格式一**，既有视觉效果又保持了标准化。
