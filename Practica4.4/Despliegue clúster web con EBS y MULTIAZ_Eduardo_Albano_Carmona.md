Eduardo Albano Carmona 2ºASIR  24/01/2023 

**Despliegue cluster web con EBS y multiAZ ![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.001.jpeg)**

[Arquitectura: ....................................................................................................................................... 3 ](#_page2_x82.00_y71.00)[Software: ............................................................................................................................................. 4 ](#_page3_x82.00_y71.00)[Configuración RDS: .............................................................................................................................. 4 ](#_page3_x82.00_y254.00)[EC2 windows ....................................................................................................................................... 9 ](#_page8_x82.00_y71.00)[Referencias: ....................................................................................................................................... 16 ](#_page15_x82.00_y71.00)

**Arquitectura:** 

Servidor base de datos RDS clusterrds: 

- Motor: MYSQL 
- Almacenamiento: t2.micro 
- VPC: Misma VPC en toda la arquitectura 
- Configuración de red y seguridad: 

Se le asigna que solo los que pertenezcan al grupo de seguridad sgweb de la practica anterior pueda acceder  

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.002.jpeg)

Servidor EC2 Windows: 

- Sistema operativo: Windows Server 2022 capa gratuita 
- Almacenamiento: db.t3.micro 
- VPC: Misma VPC en toda la arquitectura 
- Configuración de red y seguridad 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.003.png)

En este caso agregamos RDP para usar el control remoto , en este caso esta accesible para todas las ips 

**Software:** 

RDS: 

- Ofrecida por AWS 

EC2 Windows: 

- HeidiSQL 

**Configuración RDS:** 

Comenzamos creando una nueva RDS y escogiendo como motor MySQL 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.004.jpeg)

Escogeremos la opción producción para una alta disponibilidad y rendimiento 

Escogeremos la opción de Instancia de base de datos multi-az que se refiere a una implementación de alta disponibilidad en la que se utiliza un segundo servidor como un respaldo automático en caso de una interrupción en el servidor primario. La base de datos se replica automáticamente entre los servidores, lo que garantiza que los datos estén siempre disponibles y protegidos ante posibles fallos de hardware o de software 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.005.jpeg)Clase con ráfagas es adecuada para aplicaciones que requieren una capacidad de CPU adicional para manejar picos de tráfico. La clase de ráfagas proporciona una capacidad adicional de CPU para manejar estos picos 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.006.jpeg)

Establecemos el almacenamiento mínimo posible para un menor consumo de presupuesto 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.007.jpeg)

Le damos a las opciones por defecto y estableceremos que sea de acceso publico temporalmente 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.008.jpeg)

Lanzamos para crear la base de datos, en la parte superior nos aparecerá un mensaje de permisos,  que por el momento ignoraremos ya que no nos afecta a la hora de realizar esta práctica 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.009.jpeg)

Una vez creada podemos comprobar que todo ha ido bien y el apartado Multi-AZ que nos permitirá conectarnos en diferentes regiones esta en “Sí” 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.010.png)

**EC2 windows** 

Accedemos al panel de EC2 y vamos a crear una maquina con Windows 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.011.jpeg)

Escogemos la versión de la capa gratuita Microsoft Windows Server 2022 Base 

Escogemos en el par de claves vockey y seleccionamos el grupo de seguridad anteriormente creado en practicas anteriores (señalizado en la parte superior de este documento) SGweb 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.012.jpeg)

Lanzamos la instancia ec2 

Le damos al apartado Conectar y la pestaña Cliente de RDP 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.013.jpeg)

En la parte inferior encontraremos la opción Obtener contraseña y nos guiara al siguiente menu 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.014.png)Vamos a nuestro apartado de AWS (fuera del laboratorio) en AWS Details y pulsamos en Download PEM, esto nos bajara nuestra clave necesaria para el siguiente paso

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.015.jpeg)

Continuamos y cargamos la clave privada recién descargada: Con esto obtendremos nuestra contraseña para acceder por un escritorio remoto a nuestro Windows 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.016.jpeg)

La contraseña aparecerá abajo , la copiamos y pulsamos en descargar archivo de escritorio remoto 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.017.jpeg)

Aceptamos y esperamos y estaremos en nuestro Windows 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.018.jpeg)

Accederemos a la web oficial de heidiSQL y lo descargaremos 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.019.jpeg)

Procedemos instalarlos dándole a siguiente hasta finalizar 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.020.jpeg)Lo ejecutamos y creamos una conexión con el hostname de nuestra rds incluyendo nombre de usuario y contraseña 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.021.jpeg)

En la siguiente practica partiremos de esta base de datos 

![](Aspose.Words.5d2580f0-7c28-40ff-8610-fb3d04c1fa44.022.jpeg)

**Referencias:** 

https://github.com/EduAlbanoCarmona/IAW-Arquitectura-3-niveles 
15 
