#Программирование #DevOps 

[[Инструкции Dockerfile|Инструкции]] COPY и ADD выполняют одну функцию, но по разному работают с файлами. Например:

```dockerfile
FROM ubuntu:20.04

WORKDIR /zip
ADD archive.tar.xz .
COPY archive.tar.xz .
# ADD разархивирует архив, COPY - нет.

WORKDIR /url
ADD https://airflow.apache.org/docs/apache-airflow/2.4.0/docker-compose.yaml .
COPY https://airflow.apache.org/docs/apache-airflow/2.4.0/docker-compose.yaml .
# ADD скачает файл, COPY - нет.
```