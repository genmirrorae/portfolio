# DECISIONS — portfolio

## Ждёт решения
_(пусто)_

---

## Решено (архив)

### 2026-07-10 — Хостинг: GitHub Pages (переезд с Netlify) ✅
- **Причина:** Netlify (AWS CDN) не грузил медиа в РФ без VPN; GitHub Pages работает
- **Прод:** https://roman-pro.com ← GitHub Pages из репо `genmirrorae/portfolio` (публичный, ветка main, корень)
- **Как деплоить обновления:** просто `git add -A && git commit && git push origin main` из ~/portfolio — Pages пересобирается сам за 1–2 мин
- DNS на GoDaddy: 4 A-записи @ → 185.199.108–111.153, CNAME www → genmirrorae.github.io; HTTPS enforced
- Netlify оставлен как запасной (https://roman-pronin.netlify.app, деплой: `netlify deploy --prod --dir ~/Desktop/portfolio-deploy --site e9dc859a-...`); папка ~/Desktop/portfolio-deploy больше не источник правды

### 2026-07-08 — Конвертация видео: только avconvert для HDR-исходников
- **Проблема:** HDR-видео с iPhone (HEVC 10-bit HLG) при конвертации через ffmpeg/libx264 без флагов дают 10-битный H.264 (High 10) — Chrome его не играет (чёрный плеер)
- **Решение:** конвертировать через `avconvert --preset Preset1280x720 --source in.MOV --output out.mp4` — родной тонмаппинг HDR→SDR, на выходе 8-битный H.264 Main
- Если всё же ffmpeg — обязательно добавлять `-pix_fmt yuv420p` (но цвета будут блёклые без тонмаппинга)
