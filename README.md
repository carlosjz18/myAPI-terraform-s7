# myAPI-terraform

Repositorio que contiene las configuraciones terraform para:

 1. Proveedor Terraform: 

 - terraform.tf
    - Configura el proveedor de Terraform para Docker: kreuzwerker/docker

---

 2. Container Jenkins: 

 - jenkins.tf: 
    - Crea la image y container de Jenkins, mediante la construcción del Dockerfile en /jenkins-docker/Dockerfile.
    - Crea los volumes correspondientes para persistir las configuraciones y datos de Jenkins.
    - Ejecuta comando para dar permisos necesarios al archivo /var/run/docker.sock
- Dockerfile
    - Se utiliza Dockerfile en /jenkins-docker/Dockerfile para la creación del container, en este
    a su vez estan las instrucciones para instalar dentro del container de Jenkins las herramientas de Docker y Terraform, también se dan los permisos necesarios para el archivo /var/run/docker.sock para la comunicación transparente.
---

3. Container MySQL

- mysql.tf:
    - Crea la image y container de MySQL
---

Images que se crearán:
- mysql
- jbd

Containers que se crearán:
- mysql
- jenkins

---

BEDU: Developer Engineering
* Sesión #7: Postwork
* Módulo #1: Desarrollo de software ágil
* Tema #6: Jenkins como herramienta básica

## Comandos

Consultar el archivo "comandos terraform.txt" para ver las lista que comando utilizados.


## Construido con 🛠️

* [Tarraform]() Infraestructura como código (IaC)
* [Docker]() Servidor de contenedores
* [Visual Studio Code]() Editor utilizado

## Autor ✒️

* **Carlos Jaimez** - *Código inicial* - [carlosjz18](https://github.com/carlosjz18)