###ЗАДАНИЕ 1

## Описание выполненной работы
## Посылаю файл на сервер
```
scp /c/Users/Gleb-Mark/dump.fasta.gz nechaev@212.109.195.132:/students/nechaev
```
## Вхожу на сервер 
```
ssh -i C:\Users\Gleb-Mark\.ssh nechaev@212.109.195.132
```
## Создаю группу
```
sudo groupadd senior
```
## делаю так, чтобы в папке fastafiles только пользователи группы senior могли удалять/создавать/редактировать FASTA файлы, а все остальные могли только читать их
```
sudo chown :senior ./fastafiles
sudo chmod 770 ./fastafiles
sudo find fastafiles --tepe d -- exac chmod 770 {} ;
sudo find fastafiles --type f - exac chmod 640 {} ;
```
## Разархивирую dump.fasta.gz
```
gunzip dump.fasta.gz
```
## разделяю dump.fasta на двустрочные файлы формата fasta_001
```
split -l 2 -a 3 -d ./dump.fasta fasta_
```
## Превращаю файла формата fasta_001 в файлы формата fasta_001.fa
```
for file in ./fasta_*; do
    mv "$file" "$file.fa" 
```
## Сортирую файлы по папкам protein, mRNA и reference. Делаю это через cp для сохранности файлов
```
for file in /students/nechaev/ustal/fasta*; do 
     if grep -q 'mRNA' "$file"; then
        cp "$file" /students/nechaev/kgc_students_hw1/nechaev/Task_1/fastafiles/mRNA/
     elif grep -q 'protein' "$file"; then
        cp "$file" /students/nechaev/kgc_students_hw1/nechaev/Task_1/fastafiles/protein/
    elif grep -q 'complete' "$file"; then
        cp "$file" /students/nechaev/kgc_students_hw1/nechaev/Task_1/fastafiles/reference/
    fi
done
```

## Архивирую отсортированные файлы 
```
gzip students/nechaev/kgc_students_hw1/nechaev/Task_1/fastafiles/*/*.fa
```
## Записываю историю
```
history > history.log
```


###ЗАДАНИЕ 2

Наиболее энергоёмкий процесс — java и я бы его завершил с помощью команды — pkill, так как она завершает процесс аккуратно, и не требует pid. 
Для принудительного завершения я бы воспользовался командой pkill -9

Что такое PID, USER, PR, N,I VIRT, RES, SHR, S:
PID — идентификатор процесса.
USER — пользователь, которому принадлежит процесс.
PR — приоритет процесса.
NI — значение nice (приоритет пользовательского процесса).
VIRT — виртуальная память, используемая процессом.
RES — резидентная память (физическая память, используемая процессом).
SHR — общая память, используемая с другими процессами.
S — состояние процесса (например, R - выполняется, S - спит).

Как изменить МБ на ГБ и т.д.?
Это меняется с помощью клавиши Е. 

Что такое Swap? 
Swap — это пространство на диске, которое используется для хранения данных, когда оперативная память (RAM) заполняется. Это позволяет системе работать даже при нехватке оперативной памяти, но доступ к данным в Swap значительно медленнее, чем к данным в RAM.

Какие состояния бывают?  
Состояния бывают следующие: R, S, D, Z,T:
R (Running) — процесс выполняется или готов к выполнению.
S (Sleeping) — процесс не выполняется и ожидает события (например, ввода/вывода).
D (Uninterruptible Sleep) — процесс не может быть прерван (обычно ждет ввода/вывода).
Z (Zombie) — завершенный процесс, который еще не был очищен родительским процессом.
T (Stopped) — процесс остановлен (например, с помощью сигнала)
