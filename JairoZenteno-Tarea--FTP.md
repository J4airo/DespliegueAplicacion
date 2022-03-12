---
title:Tarea- FTP
author:Jairo Zenteno Flores
---

# Tarea FTP-Despliegue de Aplicación 

[TOC]

## Pasos para instalación BackEnd:

Para poder desplegar nuestra aplicación tenemos que tener instalado:

- Java
- Mysql
- Apache
- Vsftpd

Clonamos los recursos del repositorio, en nuestra maquina anfitrión:

`https://github.com/cavanosa/virtualBACK`

`https://github.com/cavanosa/virtualFRONT`

una vez hecho esto tenemos que pasar el recurso de virtualBACK a nuestro equipo linux haciendo uso de Filezilla

![image-20220312142636807](C:/Users/usuario/AppData/Roaming/Typora/typora-user-images/image-20220312142636807.png)

Una vez tenemos la aplicación modificamos el pom.xml

![image-20220312142843146](C:/Users/usuario/AppData/Roaming/Typora/typora-user-images/image-20220312142843146.png)

añadimos el paso 1, luego ejecutamos 

```bash
mvn install
```

Si al ejecutar este comando nos lanza un error del tipo `org.apache.maven.plugins:maven-surefire-plugin:2.22.2:test(default-test)`  tenemos que añadir el paso **2**.

una vez realizado estos pasos nos generará un carpeta `target`

![image-20220312143303417](C:/Users/usuario/AppData/Roaming/Typora/typora-user-images/image-20220312143303417.png)

ejecutamos el virtual.jar

```bash
java -jar target/virtual.jar
```

Si al ejecutar este comando nos lanza un error tipo `public Key Retrieval is not allowed`, tendremos que añadir en el properties de nuestro proyecto los siguientes argumentos

`jdbc:mysql://localhost:3306/db?allowPublicKeyRetrieval=true&useSSL=false`

y con esto tendríamos la parte del back finalizada.

## Pasos para la instalación del FrontEnd

Tenemos que tener instalado angular, para poder comprimir el FrontEnd y de esta manera poder subirlo a producción.

Tenemos que dar permisos al usuario de linux para que pueda escribir y ejecutar en el directorio `/var/www/html`

Configuramos los directorios de apache.

`Configuracion 000-default.conf`

![image-20220312152508363](C:/Users/usuario/AppData/Roaming/Typora/typora-user-images/image-20220312152508363.png)



`Configuracion de apache.conf`

![image-20220312152640789](C:/Users/usuario/AppData/Roaming/Typora/typora-user-images/image-20220312152640789.png)

Ponemos todo a All.

Por ultimo tenemos que crear en nuestro proyecto un fichero `.htaccess`, con la siguiente configuración:

![image-20220312152802278](C:/Users/usuario/AppData/Roaming/Typora/typora-user-images/image-20220312152802278.png)

Y por ultimo reiniciamos el servicio de apache, y ya tendríamos desplegado una aplicación.

![image-20220312152910977](C:/Users/usuario/AppData/Roaming/Typora/typora-user-images/image-20220312152910977.png)



### Recursos:

https://www.loom.com/share/6e0a7d69f219440a91070b7ed323a3e8?sharedAppSource=personal_library

https://github.com/J4airo/DespliegueAplicacion