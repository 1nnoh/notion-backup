# Notion backup

> Forked from https://github.com/darobin/notion-backup

由于GitHub Actions对于Actions secrets and variables的配置方法做了更新（增加了Environment这一项），
因此 `.github/workflows/backup.yml` 中或许环境变量如 `NOTION_TOKEN: ${{ secrets.NOTION_TOKEN }}` 时，
需要在前面指定所使用的环境。

如下注释位置：
```yml
...
jobs:
  backup:
    runs-on: ubuntu-latest
    name: Backup
    environment: NOTION   # 指定使用NOTION环境
    timeout-minutes: 15
    steps:
      - uses: actions/checkout@v3

      - uses: actions/setup-node@v2
...
```

TIPS：Debug时/手动执行Actions时，请从 `Actions` > `Your workflow` > `Run workflow` 去执行。不要在失败的Workflow中 `Re-run jobs`，因为相当于执行的还是之前失败的代码。
