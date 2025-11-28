### 2) Удалить уже загруженные PDF из репозитория, но оставить их на диске

В корне `wiki` выполни:

`git rm --cached -r -- 'lesson/**/*.pdf' git add .gitignore git commit -m "Ignore PDFs in lesson and remove tracked PDFs" git push`

- `--cached` — удалит из Git, **но файлы останутся локально**
    
- кавычки и `--` важны (особенно на Windows и с пробелами в именах файлов)
    

Проверка:

`git check-ignore -v lesson/linux/Lesson_linux_pdf/1/Linux\ Basic\ Commands.pdf git ls-files 'lesson/**/*.pdf'   # после удаления должен ничего не вывести`

### Важно про “запретить загрузку”

`.gitignore` **не блокирует** ручную загрузку/коммит (в т.ч. через веб-интерфейс GitHub) — он лишь скрывает файлы от `git status`/`git add .`.  
Если хочешь именно “запрет”, можно сделать проверку (pre-commit hook или GitHub Action), которая будет падать, если в `lesson/` есть `.pdf`.