# myAPI-terraform 馃椉

Repositorio que contiene las configuraciones terraform para:

 1. Proveedor Terraform: 

 - terraform.tf
    - Configura el proveedor de Terraform para Docker: kreuzwerker/docker

---

 2. Container Jenkins: 

 - jenkins.tf: 
    - Crea la image y container de Jenkins, mediante la construcci贸n del Dockerfile en /jenkins-docker/Dockerfile.
    - Crea los volumes correspondientes para persistir las configuraciones y datos de Jenkins.
    - Ejecuta comando para dar permisos necesarios al archivo /var/run/docker.sock
- Dockerfile
    - Se utiliza Dockerfile en /jenkins-docker/Dockerfile para la creaci贸n del container, en este
    a su vez estan las instrucciones para instalar dentro del container de Jenkins las herramientas de Docker y Terraform, tambi茅n se dan los permisos necesarios para el archivo /var/run/docker.sock para la comunicaci贸n transparente.
---

3. Container MySQL

- mysql.tf:
    - Crea la image y container de MySQL
---

Images que se crear谩n:
- mysql
- jbd

Containers que se crear谩n:
- mysql
- jenkins

---

BEDU: Developer Engineering
* Sesi贸n #7: Postwork
* M贸dulo #1: Desarrollo de software 谩gil
* Tema #6: Jenkins como herramienta b谩sica

## Evidencias 馃梻锔?

sonarqube-server
![sonarqube-server](./images/sonarqube-server.png)

report-sonar
![report-sonar](./images/report-sonar.png)

build-success-pet-clinic
![build-success-pet-clinic](./images/build-success-pet-clinic.png)

output-console-pet-clinic
![output-console-pet-clinic](./images/output-console-pet-clinic.png)

jenkins-dashboard
![jenkins-dashboard](./images/jenkins-dashboard.png)

jenkins-repo-with-credentials
![repo-with-credentials](./images/repo-with-credentials.png)

execute-pipeline-automatic-with-cron
![execute-pipeline-automatic-with-cron](./images/execute-pipeline-automatic-with-cron.png)

owasp
![owasp-output](./images/owasp1.png)  

![owasp-report](./images/owasp2.png)  

![owasp3-github-pomxml](./images/owasp3-github-pomxml.png)  

![owasp4-github-jenkinsfile](./images/owasp4-github-jenkinsfile.png)  

## Comandos

Consultar el archivo "comandos terraform.txt" para ver las lista que comando utilizados.

> terraform init

> terraform fmt

> terraform validate

> terraform plan

> terraform apply

> terraform destroy


## Configuraciones Jenkins

1. Contrase帽a inicial de Jenkins

- Dentro de la terminal del container
> cat /var/jenkins_home/secrets/initialAdminPassword

- Fuera del container
> docker exec nombre-container cat /var/jenkins_home/secrets/initialAdminPassword

> docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword

2. Plugins a instalar

- Pipeline
- Docker
- Docker Pipeline
- Environment Injector
- Git
- GitHub
- GitHub Authenticator

> jenkins-plugin-cli --plugins workflow-aggregator:590.v6a_d052e5a_a_b_5

> jenkins-plugin-cli --plugins docker-plugin:1.2.10

> jenkins-plugin-cli --plugins docker-workflow:528.v7c193a_0b_e67c

> jenkins-plugin-cli --plugins envinject:2.881.v37c62073ff97

> jenkins-plugin-cli --plugins git:4.14.0

> jenkins-plugin-cli --plugins github:1.36.0

> jenkins-plugin-cli --plugins github-oauth:0.39

3. Dar permisos para comunicaci贸n Jenkins con Docker mediante socket file

- Abre una consola en modo root en el contenedor:
> docker exec -it -u root jenkins /bin/bash

- Ejecuta el cambio de due帽o para el socket:
> chown jenkins:jenkins /var/run/docker.sock

- Verifica con:
> ls -lah /var/run/docker.sock

> docker container list

4. Configurar variables de entorno en Jenkins (Administrar Jenkins/Configurar el Sistema/Variables de entorno)

- nombre: MYSQL_IP
- valor: 172.17.0.2 / 172.17.0.3
---
- nombre: MYSQL_PASSWORD
- valor: abcD_1234
---
- nombre: MYSQL_USER
- valor: root
---

5. Crear pipeline

- Nueva Tarea
- Escribir un nombre del pipeline > "accounts"
- Seleccionar "Pipeline"
- Secci贸n Peline > poner datos del repo de GitHub donde esta el c贸digo del microservicio y la ubicaci贸n del Jenkinsfile
---
- ip = "MYSQL_IP=172.17.0.3"
- jenkins_ip = "JENKINS_IP=172.17.0.2"
---

6. MySQL container

- Conectarse a la BD MySQL desde terminal de container
> mysql -h localhost -u root -p

- Ver bases de datos
> mysql> show databases;

- Usar BD
> mysql> use myapi-accounts;

- Mostrar tablas de la BD
> mysql> show tables;


- Mostrar datos de la tabla accounts
> mysql> select * from accounts;

## Construido con 馃洜锔?

* [Jenkins]() CI/CD
* [GitHub]() SCM
* [Tarraform]() Infraestructura como c贸digo (IaC)
* [Docker]() Servidor de contenedores
* [Visual Studio Code]() Editor utilizado

## Autor 鉁掞笍

* **Carlos Jaimez** - *C贸digo inicial* - [carlosjz18](https://github.com/carlosjz18)