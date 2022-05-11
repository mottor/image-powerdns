# How to update Docker Hub's version

1. Собрать новую версию:

       docker build -t mottor1/powerdns .

2. Залогиниться на docker hub:

       docker login 
       ## Enter login and pass

3. Увеличить номер версии в файле VERSION.md

4. Запустить команду:

       for i in $(cat VERSION.md | head -n 1) "latest"; do \
       echo "pushing ${i}"; \
       docker tag mottor1/powerdns "mottor1/powerdns:${i}"; \
       docker push "mottor1/powerdns:${i}"; \
       done
