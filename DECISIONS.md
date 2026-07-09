# DECISIONS — portfolio

## Ждёт решения
_(пусто)_

---

## Решено (архив)

### 2026-07-08 — Хостинг: Netlify ✅
- **Решение Романа:** Netlify, сайт https://roman-pronin.netlify.app
- **2026-07-10:** привязан домен **https://roman-pro.com** (куплен на GoDaddy; A @ → 75.2.60.5, CNAME www → roman-pronin.netlify.app; SSL от Netlify/Let's Encrypt, www редиректит на apex)
- **Как деплоить обновления:** `cd ~/Desktop/portfolio-deploy && netlify deploy --prod --dir . --site e9dc859a-b3f7-4b55-b64c-a25ab5ca67a8` (CLI установлен через brew, авторизован)
- Папка деплоя: ~/Desktop/portfolio-deploy (копия index.html + photos + videos без .git и md)

### 2026-07-08 — Конвертация видео: только avconvert для HDR-исходников
- **Проблема:** HDR-видео с iPhone (HEVC 10-bit HLG) при конвертации через ffmpeg/libx264 без флагов дают 10-битный H.264 (High 10) — Chrome его не играет (чёрный плеер)
- **Решение:** конвертировать через `avconvert --preset Preset1280x720 --source in.MOV --output out.mp4` — родной тонмаппинг HDR→SDR, на выходе 8-битный H.264 Main
- Если всё же ffmpeg — обязательно добавлять `-pix_fmt yuv420p` (но цвета будут блёклые без тонмаппинга)
