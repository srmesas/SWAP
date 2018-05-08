# Ejercicios #

## Universidad de Granada - ETSIIT ##
### Servidores Web de Altas Prestaciones ###

##### Manuel Mesas Gutiérrez

### Índice ###

- [Tema 1](#id1)
- [Tema 2](#id2)
- [Tema 3](#id3)
- [Tema 4](#id4)
- [Tema 5](#id5)
- [Tema 6](#id6)
- [Tema 7](#id7)
---

### Tema 1 <a name="id1"></a>
#### Ejercicio:
##### Buscar información sobre las tareas o servicios web para los que se usan más los programas que comentamos al principio de la sesión:

**Apache:** es usado principalmente para servir páginas web estáticas y dinámicas en la web. Muchas aplicaciones web están diseñadas asumiendo como ambiente de implantación a Apache, o que utilizarán características propias de este servidor web.

**Nginx:** se puede implementar para servir contenido HTTP dinámico en la red utilizando FastCGI, controladores SCGI para scripts, servidores de aplicaciones WSGI o módulos Phusion Passenger, y puede servir como un equilibrador de carga de software.

**thttpd:** El uso apropiado de esta herramienta es obtener velocidad en la transferencia de archivos y reducción de gastos innecesarios para funciones que no son requeridas en el servidor. Si bien se puede utilizar como un reemplazo simplificado para servidores con más funciones, _es especialmente adecuado para atender solicitudes de gran volumen de datos estáticos_, por ejemplo, como servidor de alojamiento de imágenes. Además, thttpd tiene una característica de aceleración del ancho de banda que permite al administrador del servidor limitar la tasa de bits máxima a la que se pueden transferir ciertos tipos de archivos

**Cherokee:** ha sido adoptado por numerosos fabricantes de dispositivos electrónicos y fabricantes de tecnología del "Internet de las Cosas", debido a que es un servidor web liviano,  de alto rendimiento / proxy inverso.

**Node.js:** Node.js se usa principalmente para construir programas de red como servidores web. Los desarrolladores pueden crear servidores altamente escalables sin utilizar el uso de subprocesos, mediante el uso de un modelo simplificado de programación basada en eventos que utiliza devoluciones de llamadas para indicar la finalización de una tarea. Node.js conecta la facilidad de un lenguaje de scripting (JavaScript) con el poder de la programación en red de Unix.

___

### Tema 2<a name="id2"></a>

#### Ejercicio T2.1:
##### Calcular la disponibilidad del sistema si tenemos dos réplicas de cada elemento (en total 3 elementos en cada subsistema).

Partimos de un sistema formado por Web, Applications, Database, DNS, Firewall, Switch, un Data Center e ISP con las siguientes disponibilidades:

- Web: 85%
- Applications: 90%
- Database: 99.9%
- DNS: 98%
- Firewall: 85%
- Switch: 99%
- Data Center: 99.99%
- ISP: 95%

Utilizamos la fórmula **As = Ac1 + (1-Ac1) * Ac2** que mide el porcentaje de mejora en la disponibilidad que se alcanza al replicar un elemento. Tenemos la siguiente disponibilidad al replicar por primera vez cada elemento:

- Web: 0.85 + (1-0.85) \* 0.85 = **0.9775** = **97.75%**
- Applications: 0.9 + (1-0.9) \* 0.9 = **0.99** = **99%**
- Database: 0.999 + (1-0.999) \* 0.999 = **0.9999999** = **99.99999%**
- DNS: 0.98 + (1-0.98) \* 0.98 = **0.9996** = **99.96%**
- Firewall: 0.85 + (1-0.85) \* 0.85 = **0.9775** = **97.75%**
- Switch: 0.99 + (1-0.99) \* 0.99 = **0.9999** = **99.99%**
- Data Center: 0.9999 + (1-0.9999) \* 0.9999 = **0.9999999** = **99.99999%**
- ISP: 0.95 + (1-0.95) \* 0.95 = **0.9975** = **99.75%**

**As = Ac1 \* Ac2 \* Ac3 \* ... * Acn**  mide la disponibilidad final de sistema con respecto a los compoentes que la forman. Replicando cada elemento una sola vez se obtiene la siguiente disponibilidad:
(0.9775 \* 0.99 \* 0.9999999 \* 0.9996 \* 0.9775 \* 0.9999 \* 0.9999999 \* 0.9975) \* 100 = **94.3%**

Si añadimos otra réplica tendremos:
- Web: 0.0.9775 + (1-0.9775) \* 0.85 = **0.996625** = **99.6625%**
- Applications: 0.99 + (1-0.99) \* 0.9 = **0.999** = **99.9%**
- Database: 0.9999999 + (1-0.9999999) \* 0.999 = **0.9999999999** = **99.99999999%**
- DNS: 0.9996 + (1-0.9996)\ * 0.98 = **0.999992** = **99.9992%**
- Firewall: 0.0.9775 + (1-0.9775) \* 0.85 = **0.996625** = **99.6625%**
- Switch: 0.9999 + (1-0.9999) \* 0.99 = **0.999999** = **99.9999%**
- Data Center: 0.9999999 + (1-0.9999999) \* 0.9999 = **0.9999999999** = **99.99999999%**
- ISP: 0.9975 + (1-0.9975) \* 0.95 = **0.999875** = **99.9875%**

Replicando cada elemento por segunda vez, finalmente tenemos una disponibilidad del:
(0.996625 \* 0.999 \* 0.9999999999 \* 0.999992 \* 0.996625 \* 0.999999 \* 0.9999999999 \* 0.999875) \* 100 =**99.213%**

#### Ejercicio T2.2:
##### Buscar frameworks y librerías para diferentes lenguajes que permitan hacer aplicaciones altamente disponibles con relativa facilidad.


- **Microsoft Operations Framework (MOF)** para conseguir alta disponibilidad en productos y tecnologías de Microsoft.

- **IBM High Availability Cluster Multiprocessing** está orientado a correr en clusters con SO AIX Unix e IBM System p (Sistemas Operativos creados por IBM) y conseguir un cluster de multiprocesamiento de alta disponibilidad.
- **Linux-HA** es un framework para clusters de alta disponibilidad que usen Linux.

___

### Tema 3<a name="id3"></a>

#### Ejercicio T3.1:
##### Buscar con qué órdenes de terminal o herramientas gráficas  podemos configurar bajo Windows y bajo Linux el enrutamiento del tráfico de un servidor para pasar el tráfico desde una subred a otra.

- **Terminal**
  - **Linux:** [iptables](https://blog.desdelinux.net/redireccionar-trafico-iptables/).
  - **Windows:** [route](https://www.howtogeek.com/howto/windows/adding-a-tcpip-route-to-the-windows-routing-table/).

- **Herramienta gráfica**
 - **Linux:** [FirewallBuilder](https://www.howtoforge.com/configuring-source-and-destination-nat-with-firewall-builder).
 - **Windows:** [Servicios de enrutamiento](http://blogs.itpro.es/readyplayerone/2015/10/03/servicios-de-enrutamiento-en-windows-server-2016/).

#### Ejercicio T3.2:
##### Buscar con qué órdenes de terminal o herramientas gráficas  podemos configurar bajo Windows y bajo Linux el filtrado y bloqueo de paquetes.

- **Terminal**
  - **Linux:** [iptables](https://www.redeszone.net/gnu-linux/iptables-configuracion-del-firewall-en-linux-con-iptables/), [ufw](https://es.wikipedia.org/wiki/Uncomplicated_Firewall).
  - **Windows:** [netsh advfirewall firewall, netsh firewall](https://support.microsoft.com/es-es/help/947709/how-to-use-the-netsh-advfirewall-firewall-context-instead-of-the-netsh).

- **Herramienta gráfica**
- **Linux:** [Gufw](https://www.redeszone.net/gnu-linux/como-usar-gufw-el-firewall-de-linux/), [FirewallBuilder](http://rm-rf.es/gestion-grafica-de-firewalls-con-firewall-builder/).
- **Windows:** [Windows Firewall Defender --> Configuración avanzada](https://www.solvetic.com/tutoriales/article/3070-como-crear-reglas-firewall-windows-server-2016/). También se abre si ejecutamos en el terminal `wf.msc`.

### Tema 4<a name="id4"></a>
#### Ejercicio T4.1:
##### Buscar información sobre cuánto costaría en la actualidad un mainframe. Comparar precio y potencia entre esa máquina y una granja web de unas prestaciones similares
El último mainframe lanzado por IBM es el z14 y se estima un precio de 100.000$. El desembolso inicial sería mayor que el necesario para una granja web, aunque el gasto energético y el espacio ocupado será menor. IBM nos promete una disponibilidad del 99,999%. Además cifra el 100% de los datos de bases de datos y aplicaciones. Por contra, es más difícilmente escalable y un fallo en la máquina nos dejaría sin poder servir a los clientes.

La conclusión final sería que para empresas grandes, los mainframes pueden ser muy útiles (sin despreciar las granjas web), pero para una mediana y pequeña empresa no tiene ningún sentido pagar por un mainframe, pues una granja web es suficientemente _"potente"_.

#### Ejercicio T4.2:
##### Buscar información sobre precio y características de balanceadores hardware específicos. Compara las prestaciones que ofrecen unos y otros.

  - **TP-Link TL-R470T+**
    - **Precio:** 44.15$
    - **Puertos:**
      - 1 puerto fijo WAN Ethernet
      - 1 puerto fijo LAN Ethernet
      - 3 Puertos cambiables Ethernet WAN / LAN
    - **Memoria:** 128MB
    - **Concurrencia:** 10,000 sesiones

  - **TP-LINK TL-R480T**
    - **Precio:** 75.59$
    - **Puertos:**
      - 1 puerto fijo WAN Ethernet
      - 1 puerto fijo LAN Ethernet
      - 3 Puertos cambiables Ethernet WAN / LAN
    - **Memoria:** 128MB
    - **Concurrencia:** 30,000 sesiones

  - **TL-ER6020**
    - **Precio:** 152.07$
    - **Puertos:**
      -  1 Puerto Gigabit WAN
      -  3 Puertos Gigabit LAN/WAN
      -  1 Puerto Gigabit LAN
    - **Memoria:** 256MB
    - **Concurrencia:** 40,000 sesiones

  - **F5 Networks LTM-2000s**
    - **Precio:** 17,995.00$
    - **Puertos:**
      - 8 puertos LAN
      - 2 puertos Fibra
    - **Memoria:** 8 GB
    - **Concurrencia:** 500,000 sesiones

  - **Citrix NetScaler MPX 10500 Enterprise Edition**
      - **Precio:** 46,020.00
      - **Puertos:**
      - 2 puertos 10GBASE-X SFP+ AND
      - 8 puertos 1000BASE-X SFP (fiber or copper)
    - **Memoria:** 16 GB
    - **Concurrencia:** 500,000

    - **Citrix NetScaler MPX 10500 Platinum Edition**
      - **Precio:** 71,500.00$
      - Las mismas características que el anterior, solo cambian software y soporte.

###### Especificaciones completas:

- **[TP-Link TL-R470T+](https://www.tp-link.com/es/products/details/cat-4910_TL-R470T+.html#specifications)**
- **[TP-LINK TL-R480T](https://www.tp-link.com/es/products/details/cat-4910_TL-R480T+.html#specifications)**
- **[TL-ER6020](https://www.tp-link.com/es/products/details/cat-4909_TL-ER6020.html#specifications)**
- **[F5 Networks LTM-2000s &&  F5 Networks LTM-2200s](https://worldtechit.com/f5-products/f5-big-ip-2000s-2200s-hardware-datasheet/)**
- **[Citrix NetScaler](https://www.citrix.com/content/dam/citrix/en_us/documents/data-sheet/netscaler-data-sheet.pdf)**

#### Ejercicio T4.3:
##### Buscar información sobre los métodos de balanceo que implementan los dispositivos recogidos en el ejercicio 4.2

_No hay datos disponibles._

#### Ejercicio T4.7:
##### Buscar información sobre métodos y herramientas para implementar GSLB

**Métodos:** DNS Proxy y DNS Server.

___

### Tema 5<a name="id5"></a>

#### Ejercicio T5.1:
##### Buscar información sobre cómo calcular el número de conexiones por segundo.

Podemos comprobarlo con la siguiente orden:

- Para **HTTP**:


    netstat | grep http | wc -l

- Para **HTTPS**:


    netstat | grep :443 | wc -l

En ambos casos, debemos dividir el resultado entre el resultado del siguiente comando:

    netstat -s | grep connections\ established

Para hacer la comprobación en **apache** basta con ejecutar:

    apache2ctl status | grep request/sec

En **Nginx** tenemos que activar la recopilación de estadísticas en el fichero `nginx.conf`. Para ello debemos agregar el siguiente contenido:

    location /nginx_status {
        # Turn on stats
        stub_status on;
        access_log   off;
        # only allow access from 192.168.56.100;
        allow 192.168.56.100;
        # allow all;
        deny all;
    }

Donde `192.1685.56.100` es la IP a la que le permitimos el acceso a las estadísticas del servidor Nginx, en nuestro caso, la máquina administradora.

A continuación recargamos Nginx con el comando:

    service nginx reload

Ahora si en nuestro navegador ponemos:

    192.168.56.125/nginx_status

Entonces tendremos disponible en el navegador el número de conexiones abiertas, de conexiones aceptadas, manejadas, y peticiones manejadas. Si dividimos el número de peticiones manejadas entre el número de conexiones manejadas, tendremos el número de conexiones abiertas por segundo.

`Requests per connection = handles requests / handled connections`

#### Ejercicio T5.2:

##### Instalar wireshark y observar cómo fluye el tráfico de red en uno de los servidores web mientras se le hacen peticiones HTTP.

En este caso,

[Trabajo Wireshark](SWAP/blob/master/Trabajo Wireshark/Wireshark.pdf)

___

### Tema 6<a name="id6"></a>

___

### Tema 7<a name="id7"></a>

___
