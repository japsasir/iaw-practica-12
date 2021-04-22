# iaw-practica-12
Implantación del sitio WordPress en Amazon Web Services (AWS) usando una AMI (Amazon Machine Image) de Bitnami

> IES Celia Viñas (Almería) - Curso 2020/2021
Módulo: IAW - Implantación de Aplicaciones Web
Ciclo: CFGS Administración de Sistemas Informáticos en Red

**Introducción**
------------
El objetivo de esta práctica es montar un sitio Wordpress mediante una Community AMI (Amazon Machine Image) creada por Bitnami.

https://bitnami.com/

**Tareas a realizar**
------------
1. Seleccionar una Community AMI de Bitnami con la última versión de WordPress. https://bitnami.com/stack/wordpress/cloud/aws/amis
Es necesario tener abierta sesión en bitnami y aws a la vez y se te redirigirá con el código de bitnami.

![](https://i.imgur.com/MyUr7K0.png)
Nota: Funciona mucho mejor desde la página de bitnami que buscando en las AMI de 'comunidad' de AWS.

2. Configurar los puertos que estarán abiertos para poder conectarnos por SSH y para poder acceder por HTTP/HTTPS.

- SSH (TCP) 22
- HTTP (TCP) 80
- HTTPS (TCP) 443
![](https://i.imgur.com/qHfsY0y.png)

3. Crear un par de claves (pública y privada) para conectar por SSH con su instancia.

La clave privada es *UbuntuServerjpadilla.pem*

4. Una vez que haya iniciado su instancia, buscar cuál es la contraseña de administración del sitio WordPress.

Desde nuestra máquina AWS, podemos comprobarlo en la siguiente ruta:
`Click derecho sobre la instancia > Monitoreo y solución de problemas > Obtener registros del sistema`
![](https://i.imgur.com/McKKozU.png)

5. Buscar la dirección IP pública de su instancia y compruebe que puede acceder a ella desde una navegador web.

![](https://i.imgur.com/rWAJMIH.png)
Aquí vemos el aspecto que tiene por defecto un sitio web con la AMI de Bitnami

![](https://i.imgur.com/GwbaDE4.png)
Las credenciales para la consola de administración funcionan. Vemos que trae un plugin, Jetpack, ya instalado.

6. Para poder conectar con phpMyAdmin realizar un túnel SSH desde la máquina a la máquina remota.

Sintaxis básica
ssh -N -L 8888:127.0.0.1:80 -i clave_aws.pem bitnami@ip_maquina

Orden usada en el ejemplo
ssh -N -L 8888:127.0.0.1:80 -i C/:\Users\jpadi\Desktop\UbuntuServerjpadilla.pem bitnami@100.25.34.25/

![](https://i.imgur.com/GOfoYPe.png)

Enlaza el puerto 80 del servidor al puerto 8888 de nuestra máquina y la dirección localhost (127.0.0.1). Accedemos al navegador y escribimos 127.0.0.1:8888 podremos acceder al login de phpMyAdmin de nuestro servidor a través del túnel que hemos creado.

![](https://i.imgur.com/JISVO4K.png)
Con las credenciales 'root' y la contraseña que antes hemos visto en la consola de monitoreo, podemos acceder al panel de phpMyAdmin. Con esto tenemos pleno control de nuestro sitio Wordpress y la práctica está finalizada.


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
- Explicación comandos automatizada
https://explainshell.com/explain?cmd=ssh+-N+-L+8080%3A192.168.178.1%3A80+raspberrypi


**Editor Markdown**
------------
- Markdown editor.
https://markdown-editor.github.io/
