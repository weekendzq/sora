# 🔥 Sora2发布不到24小时，我用半小时做出国内首款开源套壳应用！

> **"当所有人还在讨论Sora2有多强时，我已经把它做成了可用的产品。"**
> 从API测试到应用上线，完整记录一个开源项目的诞生过程。

---

## 📖 故事的开始

2025年10月1日上午，当我刷着朋友圈看到OpenAI发布Sora2的消息时，手机都差点没拿稳。

**Sora2 —— 不仅能生成电影级视频，还支持实时对话！**

这不就是我一直想玩的技术吗？作为一个"喜欢折腾"的开发者，我脑海中立刻浮现出一个想法：

> **"如果能把Sora2的API包装成一个好用的Web应用，岂不是很酷？"**

说干就干！打开VS Code，开始了我的"半小时极限挑战"。

### ⏰ 开发时间轴

让我们来看看这个项目是如何在极短时间内诞生的：

| 时间 | 事件 | 心情 |
|------|------|------|
| 🕐 **09:00** | Sora2正式发布，全网刷屏 | 😮 震惊 |
| 💻 **09:30** | 注册MaynorAPIPro，获取API密钥 | 🤔 思考 |
| ⚡ **10:00** | 搭建项目框架，测试API | 💪 干劲十足 |
| 🎨 **10:15** | 实现前端界面和流式对话 | 😎 渐入佳境 |
| 🐛 **10:25** | 修复各种Bug，优化体验 | 😅 抓狂中 |
| 🎉 **10:30** | 部署到Vercel，大功告成！ | 🎊 成就感爆棚 |

**没错，从想法到上线，真的只用了半小时！**

## 🎯 为什么要做这个项目？

你可能会问："为什么要这么着急做出来？"原因很简单：

### 1. **抢占先机** 🏃‍♂️
Sora2刚发布，此时正是：
- 关注度最高的时候
- 相关资源最少的时候
- **最容易出圈的时候**

### 2. **实战学习** 📚
看再多教程，不如动手做一个：
- 真实的API调用经验
- 流式数据处理实践
- 生产环境部署经验

### 3. **开源精神** 💝
分享代码，帮助他人：
- 降低Sora2的使用门槛
- 让更多人体验AI魔法
- 收获社区反馈和Star

### 4. **证明可能** 🚀
用实际行动告诉大家：
> **"从想法到产品，可以很快！"**

## 🛠️ 技术栈

- **前端**: 原生 JavaScript + Tailwind CSS
- **后端**: Node.js + Express
- **API**: Sora2 API (通过MaynorAPIPro平台)
- **部署**: Vercel
- **版本控制**: Git + GitHub

## 🎨 产品功能一览

### 功能1：智能对话，行云流水 💬

**"就像和ChatGPT聊天一样丝滑！"**

![image-20251001214738276](https://restname.oss-cn-hangzhou.aliyuncs.com/image-20251001214738276.png)

#### 🌟 用户体验亮点

<table>
<tr>
<td width="33%">

**⚡ 极速响应**
流式输出，0延迟
看到AI"打字"的过程
就像真人在聊天

</td>
<td width="33%">

**💎 精美设计**
参考ChatGPT设计语言
紫色渐变视觉冲击
现代化圆角卡片

</td>
<td width="33%">

**📝 富文本**
支持Markdown语法
代码高亮显示
表格、列表一应俱全

</td>
</tr>
</table>

#### 🔧 技术实现揭秘

```javascript
// 核心技术：Server-Sent Events (SSE) 流式传输
async function streamChat(message) {
    const response = await fetch('/api/chat/stream', {
        method: 'POST',
        body: JSON.stringify({ messages: [message] })
    });

    // 使用 ReadableStream 逐字接收
    const reader = response.body.getReader();
    const decoder = new TextDecoder();

    while (true) {
        const { done, value } = await reader.read();
        if (done) break;

        // 实时解析并更新UI，丝滑流畅
        const chunk = decoder.decode(value);
        updateMessageInRealtime(chunk);
    }
}
```

**💡 为什么选择流式传输？**
- ✅ 用户体验更好（不用干等）
- ✅ 降低了首字节时间（TTFB）
- ✅ 更符合人类阅读习惯

---

### 功能2：视频生成，所见即所得 🎬

**"输入文字，等待30秒，视频就来了！"**

![image-20251001214800669](https://restname.oss-cn-hangzhou.aliyuncs.com/image-20251001214800669.png)

#### 🎯 核心能力

| 功能 | 说明 | 用户价值 |
|------|------|----------|
| 🎨 **文字生成视频** | 描述你想要的画面，AI自动生成 | 无需任何视频制作经验 |
| 📊 **实时进度** | 动态进度条，每一步都看得见 | 不再焦虑等待 |
| 🎥 **即时预览** | 内置播放器，生成后立即观看 | 无需下载就能确认效果 |
| ⬇️ **一键下载** | 满意后点击下载，支持mp4格式 | 方便分享到社交媒体 |

#### 🎭 进度显示的魔法

当你提交视频请求后，会看到这样的画面：

```
┌──────────────────────────────────────────┐
│  ⌛️ 任务正在队列中，请耐心等待...          │
│                                           │
│  🏃 进度：36.0%                           │
│  ████████░░░░░░░░░░                      │
│                                           │
│  🏃 进度：52.3%                           │
│  ████████████░░░░░░                      │
│                                           │
│  🏃 进度：79.7%                           │
│  ██████████████████                      │
│                                           │
│  ✅ 视频生成成功！                         │
│  🎥 [点击播放]                            │
└──────────────────────────────────────────┘
```

**为什么要做得这么细致？**
> 因为等待也可以是一种享受。看着进度条一点点增长，期待感拉满！

---

### 功能3：多端适配，随时随地用 📱

**"电脑、手机、平板，想在哪用就在哪用！"**

<div align="center">

![PC端界面](https://restname.oss-cn-hangzhou.aliyuncs.com/image-20251001215900271.png)

*▲ PC端：大屏沉浸式体验*

![移动端界面](https://restname.oss-cn-hangzhou.aliyuncs.com/image-20251001215925821.png)

*▲ 移动端：随时随地使用*

</div>

#### 🎨 设计哲学

<table>
<tr>
<td>

**📱 移动优先**
- 触控友好的大按钮
- 适合单手操作的布局
- 流量优化的资源加载

</td>
<td>

**🎯 响应式布局**
- 320px - 2560px 全覆盖
- 断点精准，过渡自然
- 不同尺寸最优展示

</td>
<td>

**🌈 视觉美学**
- 紫色渐变，科技感满满
- 圆角卡片，温暖友好
- 动画流畅，60fps保证

</td>
</tr>
</table>

#### 💅 CSS魔法示例

```css
/* 渐变背景，让界面"活"起来 */
.gradient-bg {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

/* 消息卡片动画 */
.message {
    animation: fadeIn 0.3s ease-out;
}

@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(10px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}
```

## 🔥 技术难点与解决方案

### 难点1: 流式响应处理

**问题：** Sora2 API返回的是SSE（Server-Sent Events）格式，需要实时解析

**解决方案：**
```javascript
// 1. 服务端转发流式数据
response.data.on('data', (chunk) => {
    const formatted = `data: ${chunk}\n\n`;
    res.write(formatted);
});

// 2. 前端解析SSE流
buffer += decoder.decode(value);
const lines = buffer.split('\n');
for (const line of lines) {
    if (line.startsWith('data: ')) {
        const json = JSON.parse(line.slice(6));
        handleChunk(json);
    }
}
```

### 难点2: 进度显示优化

**问题：** 视频生成需要1-2分钟，如何让用户感知进度？

**解决方案：**
- 实时解析进度信息（36% → 52% → 79%）
- CSS动画进度条，视觉反馈
- Emoji状态提示（⌛️ → 🏃 → ✅）

### 难点3: 环境变量安全

**问题：** API密钥不能提交到GitHub

**解决方案：**
```bash
# .gitignore
.env
node_modules/

# .env.example（提供模板）
SORA_API_KEY=your-api-key-here
SORA_BASE_URL=https://apipro.maynor1024.live/
```

## 📊 项目数据

**开发数据：**
- ⏱️ 开发时间：8小时
- 💻 代码行数：~500行
- 📦 依赖包：4个（express、axios、cors、dotenv）
- 🎯 提交次数：5次
- ⭐ GitHub Stars：期待你的支持！

## 🚀 快速开始

### 本地运行

```bash
# 1. 克隆项目
git clone https://github.com/xianyu110/sora.git
cd sora

# 2. 安装依赖
npm install

# 3. 配置环境变量
cp .env.example .env
# 编辑.env，填入你的API密钥

# 4. 启动项目
npm run dev
```

访问 http://localhost:3000 即可使用！

### 在线体验

🌐 **在线地址：** https://sora-three-lake.vercel.app

（需要配置API密钥才能使用完整功能）

## 🚢 Vercel部署教程（手把手教学）

想要部署自己的Sora应用？跟着下面的步骤，5分钟搞定！

### 📋 准备工作

1. **GitHub账号** - 用于托管代码
2. **Vercel账号** - 访问 https://vercel.com 注册（可以直接用GitHub登录）
3. **MaynorAPIPro API密钥** - 访问 https://apipro.maynor1024.live/ 获取

### 🎬 详细步骤

#### 第一步：Fork项目到你的GitHub

1. 访问项目地址：https://github.com/xianyu110/sora
2. 点击右上角的 **"Fork"** 按钮
3. 等待几秒钟，项目就复制到你的账号下了



#### 第二步：导入项目到Vercel

1. 访问 https://vercel.com/new
2. 选择 **"Import Git Repository"**
3. 找到你刚刚Fork的 `sora` 项目
4. 点击 **"Import"** 按钮



#### 第三步：配置环境变量（最重要！）

在Vercel的配置页面：

1. 找到 **"Environment Variables"** 区域
2. 添加以下两个变量：

```
变量名: SORA_API_KEY
值: 你的API密钥（从MaynorAPIPro获取）

变量名: SORA_BASE_URL
值: https://apipro.maynor1024.live/
```

**配置截图示例：**
```
┌─────────────────────────────────────────┐
│ Environment Variables                    │
├─────────────────────────────────────────┤
│ SORA_API_KEY    │ sk-xxxxxxxxxxxxx      │
│ SORA_BASE_URL   │ https://apipro...     │
└─────────────────────────────────────────┘
```

3. 点击 **"Add"** 按钮保存每个变量



#### 第四步：部署项目

1. 确认配置无误后，点击 **"Deploy"** 按钮
2. 等待1-2分钟，Vercel会自动构建和部署
3. 看到 **"Congratulations!"** 页面就成功了！



#### 第五步：访问你的应用

1. Vercel会自动分配一个域名，类似：`your-project-name.vercel.app`
2. 点击 **"Visit"** 按钮访问你的应用
3. 开始使用吧！



### 🔧 常见问题解决

#### 问题1: 部署失败显示 "Cannot GET /"

**原因：** 缺少 `vercel.json` 配置文件

**解决：** 确保你的项目根目录有 `vercel.json` 文件（最新代码已包含）

#### 问题2: API请求失败

**原因：** 环境变量没有配置或配置错误

**解决步骤：**
1. 进入Vercel项目 → Settings → Environment Variables
2. 检查 `SORA_API_KEY` 和 `SORA_BASE_URL` 是否正确
3. 修改后点击项目页面的 **"Redeploy"** 按钮重新部署

#### 问题3: 部署后显示404

**原因：** 路由配置问题

**解决：** 确保 `vercel.json` 中的路由配置如下：
```json
{
  "routes": [
    {
      "src": "/(.*)",
      "dest": "server.js"
    }
  ]
}
```

### 🎯 部署后的优化建议

#### 1. 自定义域名

如果你有自己的域名：
1. 进入 Vercel 项目 → Settings → Domains
2. 添加你的域名
3. 按照提示配置DNS记录

#### 2. 查看实时日志

想看应用运行日志？
1. 进入 Vercel 项目 → Deployments
2. 点击最新的部署
3. 查看 **"Functions"** 标签页的日志

#### 3. 自动部署

配置完成后，每次你向GitHub推送代码，Vercel会自动重新部署！

```bash
# 本地修改代码后
git add .
git commit -m "更新功能"
git push origin main
# Vercel会自动检测并部署
```

### 📊 部署成功指标

✅ **成功标志：**
- Vercel显示绿色的 "Ready" 状态
- 访问域名能看到应用界面
- 能够正常发送消息并收到回复
- 浏览器控制台没有错误

### 💡 进阶技巧

#### 使用Vercel CLI（可选）

如果你喜欢命令行：

```bash
# 1. 安装Vercel CLI
npm i -g vercel

# 2. 登录
vercel login

# 3. 部署
vercel

# 4. 部署到生产环境
vercel --prod
```

#### 预览部署

每次推送代码，Vercel会创建预览部署：
- 主分支 → 生产环境
- 其他分支 → 预览环境

可以在合并代码前先测试！

### 🎉 恭喜！

如果你完成了以上步骤，说明你已经成功部署了自己的Sora应用！

**分享你的应用：**
- 把域名分享给朋友
- 在社交媒体展示
- 继续定制开发

---

## 📝 项目结构

```
sora/
├── public/              # 前端文件
│   ├── index.html      # 主页面
│   └── app.js          # 前端逻辑
├── server.js           # Express服务器
├── sora2.js            # Sora2 API客户端
├── .env.example        # 环境变量模板
├── package.json        # 项目配置
├── vercel.json         # Vercel部署配置
└── README.md           # 项目文档
```

## 🎓 学到了什么？

### 技术层面
1. **流式数据处理** - SSE协议、ReadableStream API
2. **API集成** - RESTful API、错误处理、重试机制
3. **前后端交互** - Express路由、CORS配置
4. **部署实践** - Vercel部署、环境变量配置

### 产品思维
1. **用户体验** - 加载状态、错误提示、动画反馈
2. **界面设计** - 参考优秀产品、色彩搭配
3. **文档编写** - README、代码注释、使用说明

### 开发效率
1. **快速原型** - MVP思维，先实现核心功能
2. **渐进增强** - 从基础到高级，逐步完善
3. **代码复用** - 封装工具函数，提高可维护性

## 💭 心得体会

### 为什么能在24小时内完成？

1. **目标明确** - 只做核心功能，不追求完美
2. **技术选型** - 选择熟悉的技术栈，减少学习成本
3. **快速迭代** - 边开发边测试，及时发现问题
4. **AI辅助** - 使用Claude Code提高开发效率

### 遇到的挑战

1. **API文档不全** - 通过实验和调试摸索接口
2. **流式响应调试** - 需要理解SSE协议和异步流处理
3. **前端状态管理** - 处理消息历史、加载状态等

### 未来优化方向

- [ ] 添加用户认证系统
- [ ] 支持多种视频分辨率
- [ ] 优化移动端交互体验
- [ ] 添加更多自定义选项
- [ ] 支持视频编辑功能

## 🌟 开源的意义

**为什么选择开源？**

1. **学习交流** - 帮助其他开发者快速上手Sora2
2. **社区贡献** - 让更多人参与完善项目
3. **技术分享** - 分享实践经验和技术方案
4. **个人成长** - 通过反馈不断提升技术能力

## 📢 特别说明

⚠️ **重要：本项目仅支持 MaynorAPIPro 平台的 API**

- 官网：https://apipro.maynor1024.live/
- 需要注册账号并获取API密钥
- 其他平台的API密钥将无法使用

## 🔗 相关链接

- 📦 **GitHub仓库**: https://github.com/xianyu110/sora
- 🌐 **在线演示**: https://sora-three-lake.vercel.app
- 📖 **详细文档**: [README.md](https://github.com/xianyu110/sora/blob/main/README.md)
- 💬 **问题反馈**: [GitHub Issues](https://github.com/xianyu110/sora/issues)

## 👨‍💻 关于作者

一个热爱技术的全栈开发者，喜欢尝试新技术，乐于分享经验。

- GitHub: [@xianyu110](https://github.com/xianyu110)
- 如果觉得项目有帮助，欢迎 ⭐️ Star 支持！

## 🎉 结语

从Sora2发布到项目上线，24小时的时间虽然紧张，但也充满了乐趣和成就感。这个项目证明了：**只要行动起来，任何想法都可以快速变成现实。**

希望这个开源项目能帮助到正在学习Sora2 API的开发者们！如果你有任何问题或建议，欢迎在GitHub上提Issue或PR。

**让我们一起探索AI的无限可能！** 🚀

---

⭐️ **如果这个项目对你有帮助，别忘了给个Star哦！** ⭐️

![image-20251001214816336](https://restname.oss-cn-hangzhou.aliyuncs.com/image-20251001214816336.png)

