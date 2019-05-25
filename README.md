# WinServer

**Organización de la empresa**

**DEPARTAMENTOS**
La empresa está organizada en tres departamentos los cuales son:
- Administracion
- Contabilidad
- Logística

**PERSONAL Y EQUIPOS**
Cada departamento tendrá mínimo un equipo y dos empleados (que solo podrán entrar al equipo que está en su departamento).
La empresa dispondrá de una impresora para todos.
Los usuarios solo podrán entrar al sistema de 9:00 a 15:00 de lunes a viernes. Quedando restringido en el resto de horas el acceso.

**RED**
Todo el sistema está en la red 192.168.1.0/24.

**SISTEMA**
El servidor correrá bajo Windows Server 2016.
Los clientes correrán bajo Windows 7 Pro.

**Configuración previa; Red y nombre del servidor**
Lo primero que haremos es establecer el nombre del equipo para diferenciar nuestro servidor de otros. También configuraremos la IP. Establecemos una estática para que todos los equipos de la red que accedan a él sepan donde deben “buscarlo”. Para ello:
En las propiedades del equipo establecemos el nombre:
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/1.png)
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/2.png)

En las propiedades de red configuramos la red. El DNS será él mismo.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/3.png)


**Instalación de Active Directory**
Desde el “Admnistrador de servidor, pinchamos en “Agregar roles y caracteristicas”.	 Avanzamos por el asistente hasta la página “roles” y ahí seleccionamos “Servicios de dominio de Active Directory” y agregamos las caracteristicas. 
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/4.png)
Seguimos el asistente hasta que nos de la opcion de instalar.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/5.png)

Ahora lo promovemos como controlador de dominio.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/6.png)
Escogeremos un nuevo bosque y  le daremos un nuevo nombre de dominio a nuestro servidor.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/7.png)
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/8.png)
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/9.png)
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/10.png)

**Creación de la unidad organizativa de la empresa**
Ahora crearremos la unidad organizativa. 
Pinchamos en herramientas->Administración de Active Directory. Pinchamos sobre servidor(local) con el boton derecho y seleccionamos crear una nueva unidad organizativa. 
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/11.png)
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/12.png)
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/13.png)
Repetimos el proceso con todos los departamentos.

Dentro de ellas registraremos los usuarios de cada departamento y su/s equipo/s.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/14.png)
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/15.png)
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/16.png)
Estableceremos a que los usuarios solo puedan entrar a sus equipos y departamento o departamentos correspondientes. Para ello pinchamos en “Herramientas” y vamos a “Usuarios y equipos de Active Directory”.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/18.png)
Pinchamos en el departamento correspondiente y con el boton derecho sobre el usuario que nos interesa entramos en sus propiedades. 
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/19.png)
Ahí iremos a “Cuenta”. Establecemos las caracteristicas necesarias a la conexión de cada usuario y las horas de acceso permitidas. Una vez terminado aplicamos los cambios.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/20.png)
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/21.png)
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/22.png)

**Agregar la impresora** 

Nos vamos a roles de servidor. Seguimos el asistente hasta llegar al selector de roles y pinchamos sobre “servicios de impresion y documentos” y seguimos el asistente para su instalacion.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/23.png)
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/24.png)
Ahora lo que haremos será añadir la impresora a nuestro servidor. Para ello vamos a “Herramientas→Adminsitracion de impresion”. Desplegamos el servidor y pinchamos con el boton derecho sobre “controlador” y despues “agregar controlador”.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/25.png)
Seleccionamos nuestra impresora.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/26.png)
Finalizamos y comprobamos que se ha añadido correctamente en la lista.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/27.png)

**Instalación de DHCP**
Por ultimo añadiremos a nuestro servidor la caracteristica de dar soporte de DHCP. Para ello pincharemos sobre “Panel” y en “agregar roles”. Avanzaremos hasta que se nos muestre la lista y seleccionamos “Servidor DHCP”.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/28.png)
Avanzamos por el asistente hasta que finalmente nos muestre la opcion de “Instalar”.

Una vez instalado añadimos el rango de IPs que asignará el servidor. Para ello agregamos un nuevo ámbito. Para ello vamos a “Herramientas->DCHP”.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/29.png)
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/30.png)
Modificamos los valores que queremos dar en nuestra red, así como si queremos limitar el tiempo maximo de asignacion. Tambien podemos asignar un enrutador en caso de disponer de él. Cuandon terminemos de configurarlo activamos el ambito.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/31.png)

**Configuracion equipo cliente
Pasos previos**
Primero cambiaremos el nombre del equipo por uno de los que hemos configurado en el servidor. Despues debemos cambiar el grupo de trabajo por el dominio del servidor. Una vez hecho eso nos pedirá la contraseña del administrador del sistema del servidor y ya se tendra acceso con los usuarios utilizados después de reiniciar el equipo.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/33.png)

Despues nos identificaremos con un usuario con privilegios, al ser la primera vez que conectamos para vincular el equipo con el servidor, lo hacemos con el administrador.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/34.png)
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/35.png)

Ahora, en el servidor deberemos habilitar al usuario o usuarios que pueden hacer "log in". Esto lo hacemos desde "Usuarios de AD" presionando con el boton derecho sobre el usuario y pinchando sobre la opcion de "habilitar".
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/38.png)

Ahora, volviendo a nuestro equipo cliente trataremos de hacer login con el usuario.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/37.png)

**RESTRICCION DE HORARIO**
Como vimos antes, limitamos el acceso al servidor a una franja horaria. Al tratar de autenticarnos con el usuario nos mostrará un error.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/39.png)

**LOG IN**
Cuando entramos con un usuario valido y que cumple con las restricciones se nos dará acceso a nuestro escritorio.
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/36.png)
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/40.png)

**DCHP**
Podemos comprobar que el DHCP de nuestro servidor está habilitado y funcionando si desde nuestro cliente, estando configurado paa recibir DHCP previamente, nos vamos a la consola de sistema y escribimos "ipconfig".
![Texto alternativo](https://github.com/SomaTherion/WinServer/blob/master/41.png)

Vemos que la IP asignada está dentro de los valores que establecimos en nuestro DHCP y que el sufijo DNS es nuestro servidor.










