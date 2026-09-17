\# Домашнее задание к занятию «Что такое DevOps. CI/CD»

\*\*Ларионов Александр\*\*



\---



\## Задание 1 — Jenkins Freestyle Project



\### Что сделано

1\. Установлен Jenkins (WAR, Java 21) на VM (Ubuntu 18.04, IP 192.168.56.20) без Docker.

2\. Установлены Go и Docker на ту же машину.

3\. Форкнут репозиторий `netology-code/sdvps-materials` → `TheTimeLarson/devops-ci-hw`.

4\. Создан Freestyle Project, подключён репозиторий, запущены `go test .` и `docker build .`.



\### Скриншоты

!\[Конфигурация Freestyle](img/task1\_config.png)

!\[Результат сборки](img/task1\_build.png)



\---



\## Задание 2 — Jenkins Pipeline (declarative)



\### Что сделано

Создан pipeline-проект, сборка из Задания 1 переписана на declarative.



\### Код pipeline

```groovy

pipeline {

&#x20;   agent any

&#x20;   stages {

&#x20;       stage('Checkout') { steps { git branch: 'main', url: '...' } }

&#x20;       stage('Test')     { steps { sh 'go test .' } }

&#x20;       stage('Build')    { steps { sh 'docker build .' } }

&#x20;   }

}

