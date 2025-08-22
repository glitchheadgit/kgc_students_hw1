Привет, Устин! Если ты это читаешь, значит я заканчиваю работу!

и давай тогда быстро пробежимся по тому, что я наворотил...
я просто буду идти по списку: команда - что сделала
погнали
scp /c/Users/Gleb-Mark/dump.fasta.gz nechaev@212.109.195.132:/students/nechaev — перекинул файл
ssh -i C:\Users\Gleb-Mark\.ssh nechaev@212.109.195.132 — вошёл на сервер
split -l 2 -a 3 -d ./dump.fasta fasta_ — разделил файл на файлы формата fasta_001
for file in fasta_*; do
    mv  .fa
done — присобачила fa
for file in /students/nechaev/ustal/fasta*; do                                                                             if grep -q 'mRNA' ; then
        cp  /students/nechaev/kgc_students_hw1/nechaev/Task_1/fastafiles/mRNA/
    elif grep -q 'protein' ; then
        cp  /students/nechaev/kgc_students_hw1/nechaev/Task_1/fastafiles/protein/
    elif grep -q 'complete' ; then
        cp  /students/nechaev/kgc_students_hw1/nechaev/Task_1/fastafiles/reference/
    fi
done — рассортировал через греп. копирую т.к. боюсь налажать
 gzip students/nechaev/kgc_students_hw1/nechaev/Task_1/fastafiles/*/*.fa — сжал
history > history.log записал историю
 __________
< ustin/al >
 ----------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
