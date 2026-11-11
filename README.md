# 思思宝宝的专属加油站

[打开网站](https://web399.github.io/sisi-study/)

纯HTML/CSS/JavaScript，无CDN、无后端。两份题库独立刷题、独立考试，错题、收藏、历史和最高分分别保存。

| 题库 | 收录 | 可计分 | 简答 | 待确认 |
| --- | ---: | ---: | ---: | ---: |
| 消防安全 | 347 | 346 | 0 | 1 |
| 运营公司安全 | 451 | 408 | 42 | 1 |

导入修正、原文问题和核对范围见[题库核对说明](题库核对说明.md)。不确定答案不编造、不纳入考试。

## 文件与运行

- index.html：入口，直接打开或通过静态HTTP服务器运行。
- style.css、companions.png：原有可爱风格与陪伴插画。
- questions.json / questions.js：消防题库。
- operations-questions.json / operations-questions.js：运营题库。
- sample-questions.json / sample-questions.js：5题功能演示。
- legacy-questions.json / legacy-questions.js：修正前题目，仅供旧成绩回顾。
- core.js：判分、校验和迁移。
- app.js：基础页面、导航、音效和保存。
- banks.js：双题库独立记录、简答自评与待确认题目。
- .nojekyll：直接发布静态文件。GitHub Pages使用main分支根目录自动部署。

## 题目结构与扩展

id保持全局唯一且稳定；bankId为fire、operations、demo；type为single、multiple、boolean、short；question为题干，options为选项，answer为0起始下标数组。简答使用referenceAnswer；needsReview为true时只复习、不自动判分。sourceSheet/sourceRow或sourceSection/sourceNumber可追溯原题。

修改JSON后同步对应JS：window.FIRE_QUESTIONS、window.OPERATIONS_QUESTIONS。不能只改JSON而不改浏览器脚本；不要重排已有题目ID。改脚本时同步index.html中的版本参数。

## 考试与记录

每题等权，多选无部分分，未答计错；百分制四舍五入，正确率一位小数。两份试卷分别抽题、计时、评分。简答仅练习、自评。每份题库保留最近30场考试，分别导出JSON；当前没有导入入口。

所有记录留在当前浏览器localStorage，不跨设备同步。倒计时根据设备时钟计算，不具备防作弊能力。页面关闭或另一个题库打开期间，不执行该试卷交卷逻辑；再次打开该题库时补交超时试卷。
