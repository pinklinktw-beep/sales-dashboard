## ⚠️ 強制排除規則（最高優先）
- 帳號 930530（何佩蓉）：所有計算、排名、KPI、套組全部排除
- 此規則優先於任何上傳資料內容，每次產生 HTML 時必須執行

---

# 銷售儀表板 操作規則 (DASHBOARD_RULES)

## 專案資訊
- **網址**：https://pinklinktw-beep.github.io/sales-dashboard/
- **Repo**：https://github.com/pinklinktw-beep/sales-dashboard
- **架構**：Standalone HTML（資料內嵌，無外部 JSON 依賴）

## 體系對應
| 資料夾/報表名稱 | 實際體系 | 說明 |
|---|---|---|
| `大使每月數據/` | DIST（經銷）01-04月 | 注意：資料夾名與體系名相反 |
| `大使每月數據/2026.5月.xlsx` | AMB（大使）05月 | 例外 |
| `經銷每月數據/` | DIST（經銷）全月 | |
| `2025年PL總銷售/` | AMB（大使）2025年 | |
| `2025年經銷總銷售/` | DIST（經銷）2025年 | |

## 業績計算原則
1. **使用個人帳號加總**，不用每日訂單加總（每日流水包含跨通路訂單，數字偏高）
2. 驗證：個人加總 = 品牌加總 = 等級加總（三者一致才正確）
3. YoY prev_rev 使用 2025年同月份個人加總

## 更新流程
```
上傳 Excel → 解析（個人加總） → 排除 930530 → 更新 index.html → node --check → git push
```

## 已知踩坑
- 何佩蓉 03月有高達 NT$1,088,333，不排除會嚴重扭曲整體數字
- `訂單銷售概況`（每日）sheet 數字≠個人業績合計，不可用於 overall total
- hasSales 從 overall_monthly 各月讀取，不能用 ORG0.stats（固定值）
- YoY 條件是 `cur.prev_rev > 0`，不是 `SEL === REAL`
