# Personal Knowledge Hub

> 一个基于Vue 3 + Express + MongoDB的现代化个人知识库系统

## 📖 项目简介

这是一个前后端分离的个人博客系统（可扩展为知识库），采用现代化技术栈构建。项目从原有的云开发架构重构为独立部署架构，具有更高的灵活性和可控性。

### ✨ 核心特性

- 🚀 **现代化技术栈** - Vue 3 + Vite + Element Plus + Express + MongoDB
- 🎨 **优雅的UI设计** - 基于Element Plus的企业级组件库
- 📝 **Markdown支持** - 文章内容支持Markdown格式
- 🗂️ **多级分类** - 支持多级分类管理
- 💬 **评论系统** - 完整的评论审核机制
- 🔐 **JWT认证** - 基于JWT的安全认证
- 📊 **访问统计** - 文章浏览量统计
- 🐳 **容器化部署** - Docker一键部署

---

## 🛠️ 技术栈

### 前端

- **框架**: Vue 3.4+ (Composition API)
- **构建工具**: Vite 5.x
- **UI组件**: Element Plus 2.x
- **状态管理**: Pinia 2.x
- **路由**: Vue Router 4.x
- **HTTP客户端**: Axios
- **样式**: SCSS

### 后端

- **运行时**: Node.js 18+
- **框架**: Express.js 4.x
- **数据库**: MongoDB 7.x
- **认证**: JWT (jsonwebtoken)
- **密码加密**: bcryptjs
- **文件上传**: Multer

### 部署

- **容器化**: Docker + Docker Compose
- **反向代理**: Nginx
- **数据库**: MongoDB (Docker)

---

## 📦 项目结构

```
Personal Knowledge Hub/
├── backend/                # 后端代码
│   ├── src/
│   │   ├── config/        # 配置文件
│   │   ├── controllers/   # 控制器
│   │   ├── middlewares/   # 中间件
│   │   ├── models/        # 数据模型
│   │   ├── routes/        # 路由
│   │   ├── services/      # 业务逻辑
│   │   ├── utils/         # 工具函数
│   │   ├── app.js         # Express应用
│   │   └── server.js      # 服务器入口
│   ├── uploads/           # 上传文件目录
│   ├── .env.example       # 环境变量模板
│   ├── package.json
│   └── Dockerfile
│
├── frontend/               # 前端代码
│   ├── src/
│   │   ├── api/           # API服务
│   │   ├── assets/        # 静态资源
│   │   ├── components/    # 公共组件
│   │   ├── router/        # 路由配置
│   │   ├── store/         # 状态管理
│   │   ├── styles/        # 样式文件
│   │   ├── views/         # 页面组件
│   │   ├── App.vue        # 根组件
│   │   └── main.js        # 应用入口
│   ├── index.html
│   ├── vite.config.js
│   ├── package.json
│   ├── Dockerfile
│   └── nginx.conf
│
├── docs/                   # 文档目录
│   └── 重构/              # 重构相关文档
│
├── scripts/                # 工具脚本
│   ├── migrate-data.js    # 数据迁移脚本
│   └── cleanup-old-files.js
│
├── .env.example            # 环境变量模板
├── docker-compose.yml      # Docker编排配置
└── package.json

```

---

## 🚀 快速开始

### 方式一：本地开发

#### 1. 克隆项目

```bash
git clone <repository-url>
cd Personal\ Knowledge\ Hub
```

#### 2. 启动MongoDB

```bash
# 使用Docker启动MongoDB
docker run -d -p 27017:27017 --name mongodb \
  -e MONGO_INITDB_ROOT_USERNAME=admin \
  -e MONGO_INITDB_ROOT_PASSWORD=admin123 \
  mongo:7
```

#### 3. 配置后端

```bash
cd backend

# 安装依赖
npm install

# 配置环境变量
cp .env.example .env
# 编辑 .env 文件，配置数据库连接等

# 启动开发服务器
npm run dev
```

#### 4. 配置前端

```bash
cd frontend

# 安装依赖
npm install

# 启动开发服务器
npm run dev
```

#### 5. 访问应用

- 前端开发服务器: http://localhost:5173
- 后端API服务器: http://localhost:3000
- API文档: http://localhost:3000/api/docs

---

### 方式二：Docker部署

#### 1. 配置环境变量

```bash
# 复制环境变量模板
cp .env.example .env

# 编辑 .env 文件
nano .env
```

#### 2. 一键启动

```bash
# 构建并启动所有服务
docker-compose up -d

# 查看服务状态
docker-compose ps

# 查看日志
docker-compose logs -f
```

#### 3. 访问应用

- 应用入口: http://localhost
- API接口: http://localhost/api

#### 4. 停止服务

```bash
docker-compose down
```

---

## 📝 API文档

### 认证接口

| 方法 | 路径 | 说明 |
|------|------|------|
| POST | /api/auth/register | 用户注册 |
| POST | /api/auth/login | 用户登录 |
| GET | /api/auth/info | 获取用户信息 |
| POST | /api/auth/change-password | 修改密码 |
| POST | /api/auth/logout | 退出登录 |

### 文章接口

| 方法 | 路径 | 说明 |
|------|------|------|
| GET | /api/article/list | 文章列表 |
| GET | /api/article/:id | 文章详情 |
| POST | /api/article/create | 创建文章 |
| PUT | /api/article/:id | 更新文章 |
| DELETE | /api/article/:id | 删除文章 |
| POST | /api/article/:id/like | 点赞文章 |

### 分类接口

| 方法 | 路径 | 说明 |
|------|------|------|
| GET | /api/category/list | 分类列表 |
| GET | /api/category/tree | 分类树 |
| POST | /api/category/create | 创建分类 |
| PUT | /api/category/:id | 更新分类 |
| DELETE | /api/category/:id | 删除分类 |

### 评论接口

| 方法 | 路径 | 说明 |
|------|------|------|
| GET | /api/comment/list | 评论列表 |
| POST | /api/comment/create | 创建评论 |
| POST | /api/comment/:id/check | 审核评论 |
| DELETE | /api/comment/:id | 删除评论 |

### 文件上传接口

| 方法 | 路径 | 说明 |
|------|------|------|
| POST | /api/upload/single | 单文件上传 |
| POST | /api/upload/multiple | 多文件上传 |
| DELETE | /api/upload | 删除文件 |

---

## 📚 完整文档

- [数据迁移指南](./docs/重构/数据迁移指南.md)
- [架构设计文档](./docs/重构/DESIGN_前后端分离架构.md)
- [重构完成报告](./docs/重构/FINAL_重构完成报告.md)

---

## 🔄 数据迁移

如果您从CloudBase云开发迁移，请参考：

```bash
# 1. 导出CloudBase数据
tcb db export -c user -o scripts/data/user.json
tcb db export -c article -o scripts/data/article.json
tcb db export -c category -o scripts/data/category.json
tcb db export -c comment -o scripts/data/comment.json

# 2. 运行迁移脚本
node scripts/migrate-data.js

# 3. 清理旧文件
node scripts/cleanup-old-files.js
```

详细步骤请参考 [数据迁移指南](./docs/重构/数据迁移指南.md)。

---

## 🧪 测试

```bash
# 后端测试
cd backend
npm test

# 前端测试
cd frontend
npm test
```

---

## 📦 构建生产版本

### 后端

```bash
cd backend
npm run build
```

### 前端

```bash
cd frontend
npm run build
# 构建产物在 dist/ 目录
```

---

## 🐛 常见问题

### Q1: 无法连接MongoDB

检查MongoDB是否运行：

```bash
docker ps | grep mongodb
```

检查连接字符串配置是否正确。

### Q2: 前端无法访问后端API

检查后端是否启动，确认API地址配置正确：

```javascript
// frontend/vite.config.js
proxy: {
  '/api': {
    target: 'http://localhost:3000',
    changeOrigin: true
  }
}
```

### Q3: 文件上传失败

检查uploads目录权限：

```bash
chmod -R 755 backend/uploads
```

---

## 🤝 贡献

欢迎提交Issue和Pull Request！

---

## 📄 许可证

MIT License

---

## 📞 联系方式

如有问题，请提交Issue或联系项目维护者。

---

**版本**: 2.0.0  
**更新时间**: 2026-02-14
