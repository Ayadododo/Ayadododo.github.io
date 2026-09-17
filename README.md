# ARAM 一图流 · 海克斯大乱斗自用攻略

移动端优化的 LOL 海克斯大乱斗 (ARAM) 英雄出装 + 海克斯强化速查工具。

## 功能

- 🎯 英雄搜索（支持中文、拼音首字母）
- 🏷️ 按定位筛选（法师/射手/坦克/刺客/战士/辅助）
- 📋 每个英雄多个流派出装推荐
- 💎 海克斯强化分级推荐（S/A/B）
- 💾 自动记忆上次选择
- 📱 移动端优先，单手可操作

## 数据扩展

编辑 `index.html` 中的 `CHAMPIONS` 数组即可添加新英雄，结构如下：

```javascript
{
    id: 'ChampionName',   // Data Dragon 英雄 ID
    name: '中文名',
    roles: ['mage'],      // 定位标签
    tier: 'A',            // 强度评级
    winRate: '52.0%',
    builds: [
        {
            name: '流派名',
            desc: '一句话说明',
            skillOrder: '主 Q 副 W',
            coreItems: [{ id: 3089, name: '灭世者的死帽', tip: '法强翻倍' }],
            optionalItems: [{ id: 3157, name: '中娅沙漏' }],
            augments: [{ tier: 'S', name: '强化名', desc: '效果', tip: '一句话' }]
        }
    ]
}
```

装备 ID 查询：https://ddragon.leagueoflegends.com

## 部署

推送至 `main` 分支后，GitHub Pages 自动部署。

```
https://Ayadododo.github.io
```
