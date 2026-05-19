# 銷售智慧儀表板

## 網址
https://pinklinktw-beep.github.io/sales-dashboard/

## 檔案結構
```
├── index.html          ← 儀表板（不用動）
├── data/
│   ├── biz_data.json   ← 銷售資料（每月更新這個）
│   └── org_data.json   ← 組織架構（人員異動時更新）
└── uploader.html       ← 資料轉換工具（本機使用）
```

## 每月更新流程

### 方法：GitHub 網頁直接上傳（最簡單，不需要任何工具）

1. 打開 https://github.com/pinklinktw-beep/sales-dashboard
2. 點進 `data/` 資料夾
3. 點 `biz_data.json`
4. 點右上角鉛筆圖示「Edit this file」
5. 全選清空，貼上新的 JSON 內容
6. 點「Commit changes」
7. 約 1 分鐘後網站自動更新

### 取得新的 JSON 內容
把當月 Excel 上傳給 Claude，請他更新資料並產生新的 `biz_data.json`

## 第一次設定 GitHub Pages

1. 進入 repo → Settings → Pages
2. Source 選「Deploy from a branch」
3. Branch 選「main」，資料夾選「/ (root)」
4. 點 Save
5. 約 2 分鐘後網址生效
