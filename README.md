# iaw-practica-12
implantación del sitio WordPress en Amazon Web Services (AWS) usando una AMI (Amazon Machine Image) de Bitnami

> IES Celia Viñas (Almería) - Curso 2020/2021
Módulo: IAW - Implantación de Aplicaciones Web
Ciclo: CFGS Administración de Sistemas Informáticos en Red

**Introducción**
------------
El objetivo de esta práctica es montar un sitio Wordpress mediante una Community AMI (Amazon Machine Image) creada por Bitnami.

https://bitnami.com/

**Tareas a realizar**
------------
1. Crear una máquina virtual en Amazon EC2. Buscamos una AMI de la comunidad, introducimos 'Bitnami Wordpress' y buscamos la última versión (

![](https://i.imgur.com/gU2pzHo.png)

2. Seleccionar una Community AMI de Bitnami con la última versión de WordPress. https://bitnami.com/stack/wordpress/cloud/aws/amis

![](https://i.imgur.com/eBsdeMY.png)
*Wordpress Versión 5.7.1*

7. Configurar los puertos que estarán abiertos para poder conectarnos por SSH y para poder acceder por HTTP/HTTPS.

- SSH (TCP) 22
- HTTP (TCP) 80
- HTTPS (TCP) 443
![](https://i.imgur.com/qHfsY0y.png)

4. Crear un par de claves (pública y privada) para conectar por SSH con su instancia.

La clave privada es *UbuntuServerjpadilla.pem*

5. Una vez que haya iniciado su instancia, buscar cuál es la contraseña de administración del sitio WordPress.

Desde nuestra máquina AWS, podemos comprobarlo en la siguiente ruta:
`Acciones > Monitoreo y solución de problemas > Obtener registros del sistema`

6. Buscar la dirección IP pública de su instancia y compruebe que puede acceder a ella desde una navegador web.

7. Para poder conectar con phpMyAdmin realizar un túnel SSH desde la máquina a la máquina remota.

((ssh -N -L 8888:127.0.0.1:80 -i clave_aws.pem bitnami@ip_maquina))
Enlaza el puerto 80 del servidor al puerto 8888 de nuestra máquina y la dirección localhost (127.0.0.1). Accedemos al navegador y escribimos 127.0.0.1:8888 podremos acceder al login de phpMyAdmin de nuestro servidor a través del túnel que hemos creado.

`NOTA: Desglosar las opciones -N -L -i`

**Archivos en el repositorio**
------------
1.**README.md** Documentación.

**Referencias**
------------
- Guía original para la práctica.
https://josejuansanchez.org/iaw/practica-12/index.html
- Lista de AMIs de Bitnami.
https://bitnami.com/stack/wordpress/cloud/aws/amis
- Tutorial Bitnami (en inglés)
https://docs.bitnami.com/aws/get-started-console/
- PhpMyAdmin vía túnel SSH
https://docs.bitnami.com/aws/faq/get-started/access-phpmyadmin/


**Editor Markdown**
------------
- Markdown editor.
https://markdown-editor.github.io/
