name: Update README dynamically

on:
  schedule:
    - cron: "0 */6 * * *"   # runs every 6 hours
  workflow_dispatch:

jobs:
  update-readme:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repo
        uses: actions/checkout@v4

      - name: Update README
        run: |
          echo "# Hi, I'm Rajitha 👋" > README.md
          echo "" >> README.md
          echo "## 👩‍💻 About Me" >> README.md
          echo "Manual Tester with 4+ years of experience in a leading MNC, specializing in software quality assurance with strong testing expertise and parallel development skills." >> README.md
          echo "" >> README.md
          echo "## ⏰ Last Updated" >> README.md
          date >> README.md
          echo "" >> README.md
          echo "## 📊 GitHub Stats" >> README.md
          echo "![Stats](https://github-readme-stats.vercel.app/api?username=YOUR_USERNAME&show_icons=true&theme=tokyonight)" >> README.md
          echo "" >> README.md
          echo "## 💡 Quote" >> README.md
          echo "![Quote](https://quotes-github-readme.vercel.app/api?type=horizontal&theme=dark)" >> README.md

      - name: Commit changes
        run: |
          git config --global user.name "github-bot"
          git config --global user.email "github-bot@users.noreply.github.com"
          git add README.md
          git commit -m "Auto update README"
          git push
