## Tarea 1.1 Instalación de zonas mestras primarias.

## [Enlace al repositorio](https://github.com/a22jorgebb/tarea_1.1)

Para llevar a cabo esta tarea hubo que añadir volúmenes para cada
archivo a configurar en el servidor DNS BIND9:

![volúmenes compose](./images/tarea_1.1-capturas-archivos/2024-10-11_09-53-39.png)

### 1 - Instala el servidor BIND9 en el equipo Darthvader. Comprueba que ya esté funcionando como servidor DNS caché.
Salida del comando `dig @localhost www.edu.xunta.es`:

![comando dig xunta](./images/tarea_1.1-capturas-dig/2024-10-11_09-38-05.png)

### 2 - Configura el servidor BIND9 para utilizar 8.8.8.8 como **reenviador**.

Contenido del fichero **/etc/bind/named.conf.options**

![/named.conf.options](./images/tarea_1.1-capturas-archivos/2024-10-11_09-52-30.png)


Salida del comando ```dig @localhost www.mecd.gob.es```

![dig medc](./images/tarea_1.1-capturas-dig/2024-10-11_09-38-45.png)

### 3 - Instala una **zona primaria de resolución directa** llamada "starwars.lan", y añade los **registros de recursos** indicados (*además de los registros NS y SOA imprescindibles*)

Contenido del **archivo de zona**

![/named.conf.local](./images/tarea_1.1-capturas-archivos/2024-10-11_09-52-44.png)

Contenido del archivo **/etc/bind/named.conf.local**

![/named.conf.local](./images/tarea_1.1-capturas-archivos/2024-10-11_09-52-20.png)

### 4 -  Instalación de **zona inversa** que tenga que ver con la dirección del equipo darthvader y añade *registros PTR* para los registros tipo A del ejercicio anterior

Contenido del **archivo de zona**

![/named.conf.local](./images/tarea_1.1-capturas-archivos/2024-10-11_09-52-52.png)

Contenido del archivo **/etc/bind/named.conf.local**

![/named.conf.local](./images/tarea_1.1-capturas-archivos/2024-10-11_09-52-20.png)

### 5 - Comprueba que puedes resolver los distintos registros de recursos.

- `nslookup darthvader.starwars.lanlocalhost`
- `nslookup skywalker.starwars.lan localhost`
- `nslookup starwars.lan localhost`
- `nslookup -q=mx starwars.lan localhost`
- `nslookup -q=ns starwars.lan localhost`
- `nslookup -q=soa starwars.lan localhost`
- `nslookup -q=txt lenda.starwars.lan localhost`
- `nslookup 192.168.20.11 localhost`


![resolucion regs. recs.](./images/tarea_1.1-salida-comandos/2024-10-11_09-35-08.png)

![resolucion regs. recs.](./images/tarea_1.1-salida-comandos/2024-10-11_09-35-40.png)

## [Enlace al repositorio](https://github.com/a22jorgebb/tarea_1.1)