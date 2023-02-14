Eduardo Albano Carmona 2ºASIR  24/01/2023 

**Práctica 4.5 : Finalizar escenario Clúster web ![](Aspose.Words.3e9d5ea2-0216-468f-af47-8f9fd6b745b2.001.jpeg)**

[Arquitectura: ....................................................................................................................................... 3 ](#_page2_x82.00_y71.00)[Software: ............................................................................................................................................. 3 ](#_page2_x82.00_y492.00)[Base de datos: ..................................................................................................................................... 4 ](#_page3_x82.00_y71.00)[Configuración EC2 ............................................................................................................................... 4 ](#_page3_x82.00_y585.00)[Referencias: ......................................................................................................................................... 9 ](#_page8_x82.00_y294.00)

**Arquitectura:** 

Servidor base de datos RDS clusterrds de la práctica anterior: 

- Configuración de red y seguridad: 

Se le asigna que solo los que pertenezcan al grupo de seguridad sgweb de la práctica anterior pueda acceder  

![](Aspose.Words.3e9d5ea2-0216-468f-af47-8f9fd6b745b2.002.jpeg)

Servidor EC2 Windows de la práctica anterior: 

- Configuración de red y seguridad 

![](Aspose.Words.3e9d5ea2-0216-468f-af47-8f9fd6b745b2.003.png)

En este caso agregamos RDP para usar el control remoto , en este caso esta accesible para todas las ips 

**Software:** 

RDS: 

- Ofrecida por AWS 

EC2 Linux: 

- PHP 

**Base de datos:** 

Procedemos a crear la tabla con los siguientes valores: 

![](Aspose.Words.3e9d5ea2-0216-468f-af47-8f9fd6b745b2.004.jpeg)

Si hacemos una consulta simple al campo veremos que se almacenan los datos( una vez que completemos la práctica) 

![](Aspose.Words.3e9d5ea2-0216-468f-af47-8f9fd6b745b2.005.jpeg)

**Configuración EC2** 

Instalamos php en ambas maquinas EC2 linux con el siguiente comando: 

![](Aspose.Words.3e9d5ea2-0216-468f-af47-8f9fd6b745b2.006.jpeg)

A continuación modificaremos ciertos archivos dentro de nuestra ec2, al estar todos estos archivos en efs-mount se modificara en ambas maquinas. 

![](Aspose.Words.3e9d5ea2-0216-468f-af47-8f9fd6b745b2.007.jpeg)

Al archivo conexión.php se le ha añadido los datos para la base de datos 

![](Aspose.Words.3e9d5ea2-0216-468f-af47-8f9fd6b745b2.008.jpeg)

En nuestro formulario.php han sido añadidas los campos de la base de datos además de un estilo en css. 

![](Aspose.Words.3e9d5ea2-0216-468f-af47-8f9fd6b745b2.009.jpeg)

El siguiente archivo es grabar.php. que será el que se encargue de insertar los datos en nuestra base de datos 

![](Aspose.Words.3e9d5ea2-0216-468f-af47-8f9fd6b745b2.010.jpeg)

Accedemos a la web y vemos que con pruebas posteriores carga la cantidad de euros y dólares. 

![](Aspose.Words.3e9d5ea2-0216-468f-af47-8f9fd6b745b2.011.jpeg)

Insertamos 20 euros mas para hacer la prueba. 

![](Aspose.Words.3e9d5ea2-0216-468f-af47-8f9fd6b745b2.012.jpeg)

Nos indica que se ha grabado correctamente 

![](Aspose.Words.3e9d5ea2-0216-468f-af47-8f9fd6b745b2.013.jpeg)

Y el contador de euros subió en 20€ 

![](Aspose.Words.3e9d5ea2-0216-468f-af47-8f9fd6b745b2.014.jpeg)Es importante securizar , proporcionando solo http a través de la ip del proxy para que todo el que quiera acceder lo hará a  través del proxy. 

![](Aspose.Words.3e9d5ea2-0216-468f-af47-8f9fd6b745b2.015.jpeg)

**Referencias:** 

https://github.com/EduAlbanoCarmona/IAW-Arquitectura-3-niveles 
8 
