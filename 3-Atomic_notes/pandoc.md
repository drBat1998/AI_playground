Title: pandoc
tags: #atomic_note


# Notes
``` shell
pandoc "path/to/input.md" --citeproc --bibliography "~/Documents/My Library.bib" --csl "~/Documents/elsevier-harvard.csl" -o "path/to/output.docx" 
```

``` shell
pandoc ~/my_second_brain/3-Atomic_notes/AIF.md \
  --citeproc \
  --bibliography ~/Documents/My\ Library.bib \
  --csl ~/Documents/elsevier-harvard.csl \
  -o ~/my_second_brain/5-Output/AIF.docx
 
```

``` shell
#!/bin/bash

# === Налаштування (змінити під себе) ===
INPUT_MD="$1"
OUTPUT_DOCX="${2:-$(basename "${INPUT_MD%.*}").docx}"
BIBLIO_PATH="$HOME/Documents/My Library.bib"
CSL_PATH="$HOME/Documents/elsevier-harvard.csl"

# === Перевірка наявності вхідного файлу ===
if [ ! -f "$INPUT_MD" ]; then
  echo "❌ Файл '$INPUT_MD' не знайдено."
  exit 1
fi

# === Створення docx з цитуванням ===
pandoc "$INPUT_MD" \
  --citeproc \
  --bibliography "$BIBLIO_PATH" \
  --csl "$CSL_PATH" \
  -o "$OUTPUT_DOCX"

# === Повідомлення про успіх ===
if [ $? -eq 0 ]; then
  echo "✅ Експорт завершено: $OUTPUT_DOCX"
else
  echo "❌ Сталася помилка при експорті."
fi

```
make it executable
``` shell
chmod +x export_md_to_docx.sh
```

``` shell
./export_md_to_docx.sh path/to/your_note.md

```
# Links
https://youtu.be/p5Cs5XsDErE?si=TN59PgJyrhHSNOPs


