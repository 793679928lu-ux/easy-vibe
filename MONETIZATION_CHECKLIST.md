# 🚀 变现已部署 — 待办清单

## ✅ 已完成

| 项目 | 文件 | 状态 |
|------|------|:---:|
| 工具推荐页（中） | `docs/zh-cn/tools/index.md` | ✅ |
| 工具推荐页（英） | `docs/en/tools/index.md` | ✅ |
| 咨询落地页（中） | `docs/zh-cn/consulting/index.md` | ✅ |
| 咨询落地页（英） | `docs/en/consulting/index.md` | ✅ |
| ToolCard 组件 | `docs/.vitepress/theme/components/ToolCard.vue` | ✅ |
| CTA Banner 组件 | `docs/.vitepress/theme/components/MonetizationBanner.vue` | ✅ |
| 导航栏配置 | `config.mjs` — 新增 🛠️ 工具推荐 + 🎓 咨询服务 | ✅ |
| 组件注册 | `theme/index.js` — ToolCard + MonetizationBanner | ✅ |

---

## ⚠️ 部署前必须替换（搜索以下关键词）

### 1. 邮箱（2个文件）
```
搜索: your-email@example.com
替换为: 你的真实邮箱
文件: docs/zh-cn/consulting/index.md
      docs/en/consulting/index.md
```

### 2. 微信二维码
```
搜索: /assets/wechat.png
替换为: 你的真实微信二维码图片路径
文件: docs/zh-cn/consulting/index.md
      docs/en/consulting/index.md
```

### 3. 个人简介
```
文件: docs/zh-cn/consulting/index.md (关于我 section)
      docs/en/consulting/index.md (About Me section)
填写: 真实经历、辅导人数、案例数据
```

---

## 🔗 联盟计划开通指引

| 工具 | 申请地址 | 返佣 | 难度 | 优先级 |
|------|------|------|:---:|:---:|
| **Dify** | [PartnerStack](https://dify.ai/dify-affiliate-program-agreement) | 50% 终身 | ⭐ | 🔥🔥🔥 |
| **Zeabur** | [后台→推荐计划](https://zeabur.com/docs/zh-CN/rewards/referral) | 20-100% | ⭐ | 🔥🔥🔥 |
| **Canva** | [Impact Radius](https://www.canva.com/affiliate/) | $36/单 | ⭐⭐ | 🔥🔥 |
| **Global API** | [官网申请](https://globalapi.com/) | 8% 终身 | ⭐⭐ | 🔥🔥 |
| **Cursor** | [邀请制](https://cursor.com/dashboard/referrals) | $25 积分 | ⭐ | 🔥 |
| **Vercel v0** | 定向邀请 | 30%/6月 | ⭐⭐⭐ | 🔥 |

### 开通步骤（以 Dify 为例）
1. 访问 https://dify.ai/dify-affiliate-program-agreement
2. 通过 PartnerStack 注册
3. 获取你的专属推广链接
4. 将链接替换到 `docs/zh-cn/tools/index.md` 中 ToolCard 的 `url` 或新增 `affiliateLink` 字段

---

## 📊 预期收入测算

假设网站日均 5000 PV：

| 渠道 | 转化假设 | 月收入预期 |
|------|------|------|
| Zeabur 推荐 | 10人/月 × 平均$10消费 × 40%佣金 | ~$40/月 |
| Dify 推荐 | 5人/月 × $20/月 × 50% | ~$50/月 (累计增长) |
| Canva 推荐 | 3人/月 × $36 | ~$108/月 |
| 1v1 辅导 | 2人/月 × ¥299 | ~¥600/月 |
| **合计** | | **~$200 + ¥600/月** |

> 随着流量增长和返佣积累，6-12个月后有望达到 $500-2000/月

---

## 🚀 部署命令

```bash
cd easy-vibe
git add .
git commit -m "feat: monetization - tools & consulting pages, affiliate program integration"
git push
# Vercel 自动部署
```

---

## 📝 后续优化建议

- [ ] 每周在工具推荐页新增 1-2 个有联盟计划的工具
- [ ] 在课程相关章节底部添加对应的工具推荐（如 Stage 2 部署章节 → Zeabur 推荐链接）
- [ ] 收集学员案例，更新咨询页的 testimonial
- [ ] 创建邮件列表（ConvertKit/Substack），用免费资料引流
- [ ] 定期在即刻/小红书发工具测评文章引流到网站
