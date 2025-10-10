# Organizers 展示使用指南

## 📋 概览

现在 `4-resources.md` 使用了一个响应式的3列布局来展示组织者信息。每个组织者都以卡片形式展示，包含照片、姓名、职位、机构和联系方式。

## 🎨 特性

- **3列布局**：桌面端显示3列
- **响应式设计**：
  - 平板设备（<800px）：2列
  - 手机设备（<600px）：1列
- **悬停效果**：鼠标悬停时卡片轻微上浮并显示阴影
- **圆形头像**：180x180px 圆形裁剪
- **可选链接**：Email 和个人网站链接

## 📝 使用方法

### 添加组织者

在 `4-resources.md` 中的 `<div class="organizers-grid">` 标签内添加：

```liquid
{% include organizer-card.html 
   img="photo.jpg" 
   name="张三" 
   title="教授" 
   affiliation="某某大学"
   email="zhangsan@example.com"
   website="https://example.com" %}
```

### 参数说明

| 参数 | 必填 | 说明 |
|------|------|------|
| `img` | ✅ | 图片文件名（放在 `images/` 目录） |
| `name` | ✅ | 组织者姓名 |
| `title` | ✅ | 职位/头衔 |
| `affiliation` | ✅ | 所属机构 |
| `email` | ❌ | 电子邮件（可选） |
| `website` | ❌ | 个人网站（可选） |

### 示例

#### 基本示例（无联系方式）
```liquid
{% include organizer-card.html 
   img="john.jpg" 
   name="John Doe" 
   title="Associate Professor" 
   affiliation="MIT" %}
```

#### 完整示例（含联系方式）
```liquid
{% include organizer-card.html 
   img="jane.jpg" 
   name="Jane Smith" 
   title="Research Scientist" 
   affiliation="Google Research"
   email="jane@google.com"
   website="https://janesmith.com" %}
```

## 🖼️ 准备图片

### 图片要求
- **格式**：JPG、PNG 或 GIF
- **建议尺寸**：至少 400x400px（会被裁剪为圆形）
- **比例**：正方形或接近正方形效果最佳
- **位置**：放在 `images/` 目录

### 图片处理建议
1. 使用正方形照片
2. 确保人脸居中
3. 建议背景简洁
4. 文件大小控制在 500KB 以内

### 添加图片步骤
1. 将照片复制到 `images/` 目录
2. 重命名为有意义的文件名（如：`aparna-bharati.jpg`）
3. 在 organizer-card 中引用文件名

## 🎨 样式自定义

如需修改样式，编辑 `_sass/_custom.scss` 文件：

### 修改头像大小
```scss
.organizer-photo img {
    width: 200px;    // 修改这里
    height: 200px;   // 修改这里
    border-radius: 50%;
}
```

### 修改卡片间距
```scss
.organizers-grid {
    gap: 50px;  // 修改间距
}
```

### 修改悬停效果
```scss
.organizer-card:hover {
    transform: translateY(-10px);  // 增加移动距离
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);  // 更深的阴影
}
```

### 修改列数
```scss
.organizers-grid {
    grid-template-columns: repeat(4, 1fr);  // 改为4列
}
```

## 📱 响应式断点

当前断点设置（在 `css/main.scss` 中定义）：

- **$on-palm**: 600px（手机）
- **$on-laptop**: 800px（平板/笔记本）

布局变化：
- **> 800px**：3列
- **600px - 800px**：2列
- **< 600px**：1列

## 🔧 故障排除

### 图片不显示
1. 检查图片是否在 `images/` 目录
2. 检查文件名是否正确（区分大小写）
3. 检查文件扩展名是否正确

### 布局错乱
1. 确保 `<div class="organizers-grid">` 标签完整
2. 检查每个 organizer-card 的语法是否正确
3. 清除浏览器缓存

### 样式未生效
1. 确保修改了 `_sass/_custom.scss`
2. 重新构建 Jekyll 站点
3. 强制刷新浏览器（Ctrl+Shift+R）

## 💡 最佳实践

1. **保持一致性**：所有组织者使用相同的图片尺寸和风格
2. **信息完整**：尽量填写所有可选字段
3. **顺序安排**：按重要性或字母顺序排列
4. **可访问性**：确保图片有合适的 alt 文本（组件已自动添加）

## 🌟 高级用法

### 添加更多组织者（4个或更多）

如果有4个或更多组织者，可以修改为4列布局：

```scss
// _sass/_custom.scss
.organizers-grid {
    grid-template-columns: repeat(4, 1fr);  // 4列
    
    @media screen and (max-width: $on-laptop) {
        grid-template-columns: repeat(2, 1fr);  // 平板2列
    }
    
    @media screen and (max-width: $on-palm) {
        grid-template-columns: 1fr;  // 手机1列
    }
}
```

### 添加社交媒体链接

修改 `_includes/organizer-card.html`，在现有链接后添加：

```html
{% if include.twitter %}
<p class="organizer-contact">
  <a href="https://twitter.com/{{ include.twitter }}" target="_blank">🐦 Twitter</a>
</p>
{% endif %}
```

使用时：
```liquid
{% include organizer-card.html 
   name="Name"
   twitter="username" %}
```

## 📚 相关文件

- `4-resources.md` - Organizers 页面内容
- `_includes/organizer-card.html` - 组织者卡片组件
- `_sass/_custom.scss` - 样式定义
- `images/` - 图片目录

---

**需要帮助？** 查看项目的 README.md 或提交 issue。
