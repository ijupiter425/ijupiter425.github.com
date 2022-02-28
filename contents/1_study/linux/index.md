# linux

source: `{{ page.path }}`

 __하드디스크 용량 확인__
 ```bash
df -h
du -h --max-depth=1
du -hs *
```

 __time zone__
 ```bash
timedatectl set-timezone America/Atikokan
timedatectl set-timezone America/Atikokan
timedatectl set-timezone Asia/Seoul
```

 __file에서 정보 추출 예제__
 ```bash
cat shop | grep NetmarbleSIAPVerify | awk -F '[ =&"]' '{ for (i=2; i<=NF; i++)   if ($i =="transactionId") {print "[verify] " $1,$2,$8,$(i+2)}}' > verify
cat shop3 | awk -F '[ =&,"]' '{ for (i=2; i<=NF; i++) if ($i =="transactionId") {print "[IAP] " $1,$2,$24,$(i+2)}}' > iap
cat verify iap | sort -k 2 | awk '{print $4,$5}' |  uniq -dc | sort -k 1 > result
cat result | awk '{print $4,$5}' | sort | uniq -c | sort
```

 __version 확인__
```bash
cat /etc/*-release | uniq
```

 __트정 패턴 파일 전부 삭제__
```bash
$ find . -name '*.tmp' -exec rm {} \;
```

 __현재 디렉토리 내에 있는 디렉토리 또는 파일 개수__
```bash
ls -l | grep ^d | wc -l
ls -l | grep ^- | wc -l
```

 __커널에서 프로세스 죽일 경우 남기는 로그__
```bash
/var/log/messages
```

 __최대 소켓 수__
```bash
sysctl fs.file-max
```
