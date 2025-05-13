https://github.com/Dinastino/Caso_Practico_Final.git

# Caso_Practico_Final

edificio1 Vtp ;domain: 'gov' ;Vtp pasword: $c@alabazas$  
trasporte Vtp ;domain: 'transporte' ;VTP password: 'transp0rte'  

# Indice 

- [Paso 1](#paso-1-diseño-y-modelado-de-la-arquitectura-de-comunicación)
   - [Repaso de modelos](#repaso-de-modelos-osi-y-tcpip)
      - [Modelo OSI](#modelo-osi)
      - [Modelo TCP/IP](#modelo-tcpip)
- [Paso 2](#paso-2-capa-física--cálculos-y-selección-de-tecnologías)
   - [Cálculo de la Capacidad](#cálculo-de-la-capacidad-de-los-enlaces)
   - [Técnicas de modulacion](#selección-de-técnicas-de-modulación)
   - [Eficiencia del encapsulamiento](#evaluación-de-la-eficiencia-del-encapsulamiento)
- [Paso 3](#paso-3-capa-de-red--direccionamiento-subneteo-y-enrutamiento)
   - [Diseño de red](#diseño-del-esquema-de-direccionamiento-ip)
   - 

# Paso 1: Diseño y Modelado de la Arquitectura de Comunicación

## Repaso de modelos OSI y TCP/IP

### Modelo OSI

El **modelo OSI** consta de **siete capas** que estructuran el proceso de comunicación de datos entre sistemas, dividiendo funciones específicas para garantizar una comunicación clara, ordenada y estandarizada:

1. **Capa Física**  
   Responsable de la **transmisión de bits** a través de medios físicos como cables trenzados o fibra óptica. Define estándares mecánicos, eléctricos y ópticos como tensiones, tiempos de señal y tipos de conectores.  
   *Ejemplos*: Cables de red, conectores, tarjetas de red.

2. **Capa de Enlace de Datos**  
   Convierte el medio físico en una línea de comunicación confiable mediante la **detección y corrección de errores**, organizando los datos en tramas. Se divide en subcapas de acceso al medio y control de flujo.  
   *Ejemplos*: Switches, adaptadores de red, Ethernet.

3. **Capa de Red**  
   Encargada del **enrutamiento** de datos entre redes, gestionando direcciones IP, tablas de enrutamiento, congestión y calidad del servicio. Puede usar rutado estático o dinámico.  
   *Ejemplos*: Routers, direcciones IP.

4. **Capa de Transporte**  
   Ofrece **comunicación extremo a extremo confiable**, segmentando datos y asegurando entrega ordenada. Puede operar con protocolos orientados a conexión (TCP) o sin conexión (UDP).  
   *Ejemplos*: TCP, UDP.

5. **Capa de Sesión**  
   Establece, administra y finaliza sesiones entre aplicaciones, proporcionando sincronización y control de diálogos entre sistemas.

6. **Capa de Presentación**  
   Traduce y transforma los datos, asegurando que los sistemas con diferentes formatos puedan **interpretar la información correctamente**. Maneja compresión y cifrado.

7. **Capa de Aplicación**  
   Interactúa directamente con el **usuario final**, proporcionando servicios como transferencia de archivos, correo electrónico o navegación web.  
   *Ejemplos*: HTTP, FTP, SMTP.

---

### Modelo TCP/IP

El **modelo TCP/IP**, base de Internet, es un modelo más práctico y consta de **cuatro capas**, integrando funciones del modelo OSI para facilitar su implementación en sistemas reales:

1. **Capa de Acceso a la Red**  
   Equivalente a las capas Física y de Enlace del OSI. Maneja el hardware, controladores y protocolos de acceso al medio físico.

2. **Capa de Internet**  
   Similar a la Capa de Red del OSI. Administra direcciones IP, fragmentación y enrutamiento de paquetes entre redes.

3. **Capa de Transporte**  
   Igual que en OSI, se encarga del control de flujo, confiabilidad y segmentación de datos. Utiliza **TCP** (orientado a conexión) o **UDP** (sin conexión).

4. **Capa de Aplicación**  
   Agrupa las capas de Aplicación, Presentación y Sesión del OSI. Proporciona servicios de red al usuario y aplicaciones.  
   *Ejemplos*: HTTP, FTP, DNS.



 ***Comparación entre el Modelo OSI y el Modelo TCP/IP***

| **Capa**   | **Modelo OSI**             | **Modelo TCP/IP**              |
|-----------|-----------------------------|-------------------------------|
| Capa 1    | Física                      | Acceso a la Red               |
| Capa 2    | Enlace de Datos             | Acceso a la Red               |
| Capa 3    | Red                         | Internet                      |
| Capa 4    | Transporte                  | Transporte                    |
| Capa 5    | Sesión                      | Aplicación (combinada)        |
| Capa 6    | Presentación                | Aplicación (combinada)        |
| Capa 7    | Aplicación                  | Aplicación (combinada)        |


#### Diferencias Clave

- **Número de capas**: OSI tiene **7 capas**, TCP/IP solo **4**.
- **Enfoque**: OSI es un modelo **teórico**, mientras TCP/IP es **práctico y orientado a implementación**.
- **Definición de funciones**: TCP/IP **no distingue claramente** entre servicio, interfaz y protocolo.
- **Compatibilidad**: OSI no contemplaba **redes de difusión** en su diseño original.
- **Transporte**: OSI solo soporta **comunicación orientada a conexión**; TCP/IP admite ambas (conexión y sin conexión).
- **Redundancia**: OSI puede **repetir funciones** como control de flujo o detección de errores en varias capas, lo que puede reducir la eficiencia.

Ambos modelos permiten entender y diseñar redes, pero el **TCP/IP es el modelo adoptado globalmente** por su flexibilidad, escalabilidad y aplicación directa en redes como Internet.


## Diseño Lógico y Segmentación

### Diseño de red de la ciudad

![Diagrama sin título drawio](https://github.com/user-attachments/assets/2cf5d2b0-39ca-4f5b-a9d2-493416d0a45d)

#### 2. Segmentación por Zonas

- Zona Gubernamental
   - **Elemento:** Edificio Gubernamental
   - **Conectividad:**
     - Conectado mediante fibra al Edificio Genérico
     - Conexión directa a Transporte
   - **Función:** Gestión política, administración pública, servidores críticos del gobierno.

---

- Zona de Seguridad
   - **Elemento:** Central de Seguridad
   - **Conectividad:**
     - Fibra al Edificio Genérico
     - Enlace al Edificio Genérico 2
   - **Función:** Monitoreo urbano, vigilancia, control de emergencias y servicios de seguridad pública.

---

- Zona de Transporte
   - **Elemento:** Centro de Transporte
   - **Conectividad:**
     - Enlace a Edificio Gubernamental y Edificio Genérico 2
     - Acceso a Internet
   - **Función:** Gestión de flotas, tráfico inteligente, control de movilidad urbana.

---

- Zonas Genéricas
   - **Elementos:**
     - Edificio Genérico
     - Edificio Genérico 2
   - **Conectividad:**
     - Edificio Genérico enlaza con Gubernamental, Seguridad e Internet
     - Edificio Genérico 2 enlaza con Seguridad y Transporte
     - Los dos edificios se conectan entre ellos.

---

- Internet
   - **Elemento:** Nube de Internet
   - **Conectividad:**
     - Conectada al Edificio Genérico y Transporte
   - **Función:** Conectividad externa, servicios en la nube, acceso remoto.



#### 3. Tipos de Enlace
- **Fibra:** Alta velocidad y capacidad. Usado entre zonas críticas.
- **Serial:** Conexiones punto a punto o de respaldo.
- **Salidas al resto de red:** Interconexión general con otros sectores de la red metropolitana. Se presumen enlaces de fibra o seriales.


### Representacion en cisco packet tracer

- **Vista fisica**

![image](https://github.com/user-attachments/assets/02a48a6d-362c-4367-beeb-f8cf9464567a)

> **Nota:** Es posible que no aparezcan todos los servicios/dispositivos que existen en la ciudad dada la posibilidad de que la vista este demasiado congestionada para la visualización

### Dispositivos por zonas

Cada zona o red aislada cuenta con sus propios dispositivos, su propia red, sus propias Vlans y protocolo vtp

- Zona Gubernamental

   ![Gobierno drawio](https://github.com/user-attachments/assets/88009416-0a39-4d2a-a347-9d2558c8f11a)

   - **Elemento:** Edificio Gubernamental
   - **Dispositivos edificio**:
        - Router cisco 2911
        - X2 Firewall ASA 5506-X
        - X6 Server-PT:
             - DNS, HTTP/HTTPS, FTP, DHCP, EMAIL. IOT.
        - Switch L3 cisco 2650-24PS
        - X6 switch L2 cisco 22960-24TT
        - X4 Access point-PT
        - X20 PC-PT
        - X4 MCU
        - X4 Webcams
        - X8 Home Speaker
        - X4 Smoke detector
        - X4 Carbon monoxide detector
        - Una Cafetera
    

   - Cables de cobre cat 6 y Gb para conexione entre dispositivos
   - > **Nota:** Cada vlan excepto la 10 representa una planta diferente

   ![image](https://github.com/user-attachments/assets/79ae798c-0c65-4bf0-bc02-b86c164aa023)


---

- Zona de Seguridad
   - **Elemento:** Central de Seguridad
   - **Dispositivos:**
        - Router cisco 2911
        - Firewall Cisco ASA 5506-X
        - X5 Server-PT:
             - DNS, FTP, DHCP, IoT, Streaming
        - Central Office server
        - Switch L3 cisco 2650-24PS
        - X8 switch L2 cisco 22960-24TT
        - X3 Access point-PT
        - X11 PC-PT
        - Laptop-PT
        - X2 TV-PT
        - X8 IP-phone
        - X6 Webcams

---

- Zona de Transporte

![Transporte](https://github.com/user-attachments/assets/49f01f4b-2222-43c0-997a-9419c8713b97)

   - **Elemento:** Edificio de transporte y los semaforos
   - **Dispositivos edificio**:
       - Un router 2911
       - Dos firewall ASA 5506-X
       - Un firewall 5505
       - X6 Server-PT:
            - DNS, HTTP, FTP, DHCP, Email. IoT.
       - Switch L3 cisco 2650-24PS
       - X6 switch L2 2960-24TT
       - X14 PC-PT
       - X2 Webcams
       - X4 Home Speakers
       - X4 semaforos:
            - Un mcu(Micro controlador)
            - Tres Led-RGB
       - X5 Access-Point-PT
       - X2 Humiture monitor
       - X2 Carbon dioxide detector


   - Cables de cobre cat 6 y Gb para conexione entre dispositivos
   - > **Nota:** Cada vlan excepto la 11 es un piso diferente

![image](https://github.com/user-attachments/assets/d4745a5e-53bb-4a3d-b489-d53b8ffbade2)
![image](https://github.com/user-attachments/assets/cfd49024-8d63-4f26-836f-f01946bf51d0)



---

- Zonas Genéricas
   - **Elementos:**
     - Edificio Genérico: Un router 2911
     - Edificio Genérico 2: Un router 2911

---

- Internet
   - **Dispositivos:** Cloud-PT para simular conexion a internet.
  



# Paso 2: Capa Física – Cálculos y Selección de Tecnologías

## Cálculo de la Capacidad de los Enlaces

Se utiliza la fórmula de Shannon:  

$$Donde: C = B * log_2(1+SNR)$$  

Ancho de banda (B)  

SNR: relación señal a ruido determinada.   
La relación señal a ruido se mide en dB en un ancho de banda es:    

$$𝑆𝑁𝑅 = 10 𝑙𝑜𝑔_{10}(𝑆𝑁𝑅) = 10^{\frac{SNR}{10}} [dB]$$  

1. **Fa/Trenzado de 250Mb**  
    Cable de cobre categoría 6 con ancho de banda de 250 MHz. 

    $$C = 2,5 * 10^8 * log_2(1+1000) = 2,5 * 10^8 * log_2(1001) = 2,5 * 10^8 * 9.967 = 2.49 * 10^9bps = 2.49 Gbps$$

   *Este tipo de cable proporciona conexiones repidas entre switches-ordenadores *

2. **Acces-point/Inalámbrico**
   Enlaces inalambricos de wifi en cada access-point.


   $$C = B \cdot \log_2(1 + S/N) = 20 \times 10^6 \cdot \log_2(101) \approx 20 \times 10^6 \cdot 6.658 = 133.16 \text{ Mbps}$$

   >  **Nota:** Este valor es teórico. En redes Wi-Fi reales, la velocidad efectiva suele estar entre **40–80 Mbps** dependiendo de la interferencia, distancia y calidad del enlace.

4. **Entre switches/Cable de cobre de Gb**

    Cable de cobre con **ancho de banda de 1 GHz**, empleado para manejar mayor tráfico entre switches.

    $C = 1* 10^9 * log_2(1001) =  1 * 10^9 * 9.967 = 9,96710^9 bps = 9.97 Gbps$

   *Este tipo de enlace proporciona un **canal de alta capacidad** para interconexion entre la red y de la red al router.*

5. **Fibra Óptica**

   Fibra óptica utilizada como medio de transmisión troncal entre equipos principales.

   $$C = 50 \times 10^{12} \cdot \log_2(1 + 1000) = 50 \times 10^{12} \cdot \log_2(1001)$$

   $$\log_2(1001) \approx 9.967$$

   $$C \approx 50 \times 10^{12} \cdot 9.967 = 4.9835 \times 10^{14} \text{ bps} = 498.35 \text{ Tbps}$$

    *Aunque la fibra óptica permite **enormes capacidades teóricas**, en la práctica está limitada por los **componentes electrónicos**, especialmente los **conversores optoelectrónicos**, que actualmente permiten **hasta 100 Gbps por canal**.*


> Tener en cuenta que todo esto es teórico ya que el cisco packet pone limitaciones por el tipo de puerto ejm: el FastEthernet esta capado a 100Mbps
   

## Selección de Técnicas de Modulación
La modulación es el proceso mediante el cual se adapta una señal digital a una portadora analógica para poder ser transmitida eficientemente por un medio físico (cable, aire o fibra).  
A continuación, se describen las técnicas más relevantes según el tipo de medio:

- **Para enlaces de cobre**, como el trenzado Cat 6 y las conexiones entre switches, se utiliza la modulación **16-QAM**, ya que ofrece una buena relación entre **eficiencia espectral y confiabilidad** en medios con distancias cortas y buena calidad de señal.

- **Para enlaces de fibra óptica**, se utiliza **64-QAM**, ya que la fibra proporciona una **relación señal/ruido muy alta**, lo que permite el uso de modulaciones densas para **maximizar el rendimiento** y el aprovechamiento del enorme ancho de banda disponible.

- **Para enlaces inalámbricos**, se emplea una combinación de **OFDM** con modulacion de **QAM** adaptativa lo que permite cambiar entre numero de bits por simbolo dependiendo de la calidad de la transmision, esto es especificamente importante en las redes inalambricas de fuera de los edificios ya que estan en el exterior son mas suceptibles a los cambios.

 ## Evaluación de la Eficiencia del Encapsulamiento

En una red, los datos generados por la aplicación deben atravesar múltiples capas del modelo OSI o TCP/IP. Cada capa añade su propia **cabecera (header)**, lo que genera una **sobrecarga**. Esta sobrecarga reduce la **eficiencia real** del canal de transmisión.

---

##  Evaluación de la Eficiencia del Encapsulamiento:

Supongamos que se desea enviar **1000 bytes** de datos útiles (payload) usando una red Ethernet con IP y TCP.

#### Cabeceras involucradas:

| Capa       | Protocolo | Tamaño de Cabecera |
|------------|-----------|--------------------|
| Enlace     | Ethernet  | 18 bytes (14 de cabecera + 4 de CRC) |
| Red        | IP        | 20 bytes            |
| Transporte | TCP       | 20 bytes (sin opciones) |

**Tamaño total del paquete transmitido**:

$$\text{Total} = 1000\ \text{(datos)} + 20\ (\text{TCP}) + 20\ (\text{IP}) + 18\ (\text{Ethernet}) = 1058\ \text{bytes}$$

---

#### Cálculo de eficiencia


$$\text{Eficiencia} = \frac{\text{Datos útiles}}{\text{Datos totales transmitidos}} = \frac{1000}{1058} \approx 0.9452 = 94.52\%$$

 Esto significa que el 5.48% del ancho de banda se utiliza en **cabeceras**, no en datos reales.

---

####  Consideraciones

- En paquetes más pequeños, la **eficiencia disminuye**, ya que la proporción de cabecera es mayor.
- En tramas mínimas (por ejemplo, 46 bytes de datos en Ethernet), la eficiencia puede caer por debajo del 50%.
- Si se suman otras capas (SSL, VPN, encapsulamiento GRE, etc.), la sobrecarga crece aún más.



# Paso 3: Capa de Red – Direccionamiento, Subneteo y Enrutamiento

## Diseño del Esquema de Direccionamiento IP

### Zona Gubernamental
Red de la zona gubernamental incluyendo todos los servicios.

- La red interna es la 192.168.1.0/24:
    - **Rango de Hosts:** 192.168.1.2 – 192.168.1.254
    - **Default gateway:** 192.168.1.1
    - **Broadcast:** 192.168.1.256
    - **Total de Hosts Útiles:** 254  

- La dmz es la 176.20.20.0/26:
    - **Rango de Hosts:** 176.20.20.2 – 176.20.20.127
    - **Default gateway:** 176.20.20.1
    - **Broadcast:** 176.20.20.128
    - **Total de Hosts Útiles:** 126  

- La red externa es la 200.10.15.0/24:
    - **Rango de Hosts:** 200.10.15.2 – 200.1.1.254
    - **Default gateway:** 200.10.15.1
    - **Broadcast:** 200.10.15.256
    - **Total de Hosts Útiles:** 254

Aparte la red se divide en multiple vlans cada una con su propia IP, gateway y broadcast. 

| VLAN  | Descripción             | Red IP             | Gateway           | Broadcast           |
|-----|----------|----------|--------------------|----------------------|
| 100   | vlan 100     | 192.168.10.0/24   | 192.168.10.1      | 192.168.10.255      |
| 200      |  vlan 200      | 192.168.20.0/24   | 192.168.20.1      | 192.168.20.255      |
| 300      | vlan 300    | 192.168.30.0/24    | 192.168.30.1       | 192.168.30.255       |
| 400      | vlan 400    | 192.168.40.0/24    | 192.168.40.1       | 192.168.40.255       |



**VLAN 10 – 192.168.99.0/24** Servidores

- **Rango de Hosts:** 192.168.99.2 – 192.168.99.254
- **DDefault gateway:** 192.168.99.1
- **Broadcast:** 192.168.99.256
- **Total de Hosts Útiles:** 254


Cada VLAN tiene su propia subred /24 (máscara de subred 255.255.255.0), lo cual permite hasta 254 hosts por segmento, ideal para entornos académicos de tamaño medio.

**VLAN 100 – 192.168.10.0/24** Recepción

- **Rango de Hosts:** 192.168.10.2 – 192.168.10.254
- **DDefault gateway:** 192.168.10.1
- **Broadcast:** 192.168.10.256
- **Total de Hosts Útiles:** 254

**VLAN 200 – 192.168.20.0/24** Planta 1

- **Rango de Hosts:** 192.168.20.2 – 192.168.200.254
- **Default gateway:** 192.168.20.1
- **Broadcast:** 192.168.20.256
- **Total de Hosts Útiles:** 254

**VLAN 300 – 192.168.30.0/24** Planta 2

- **Rango de Hosts:** 192.168.30.2 – 192.168.30.254
- **DDefault gateway:** 192.168.30.1
- **Broadcast:** 192.168.30.256
- **Total de Hosts Útiles:** 254

**VLAN 400 – 192.168.40.0/24** Planta 3

- **Rango de Hosts:** 192.168.40.2 – 192.168.40.254
- **DDefault gateway:** 192.168.40.1
- **Broadcast:** 192.168.40.256
- **Total de Hosts Útiles:** 254


> **Nota:** Todas la Vlans y la red interna reciben sus IP's a traves del servidor de DHCP excepto los puntos/enlaces criticos.
---

- Zona de Seguridad
   

---

### Zona de Transporte
Red de la zona de transporte [Router]-----`Red externa`----[Firewall 1]-----`DMZ`-----[Firewall 2]-----`Red interna`----[Switch L3], y la red a la que se conectan los dispositivos de IoT como los semaforos o los sensores

- La red interna es la 192.168.3.0/24:
    - **Rango de Hosts:** 192.168.3.2 – 192.168.3.254
    - **Default gateway:** 192.168.3.1
    - **Broadcast:** 192.168.3.256
    - **Total de Hosts Útiles:** 254  

- La dmz es la 176.10.20.0/26:
    - **Rango de Hosts:** 176.10.20.2 – 176.10.20.127
    - **Default gateway:** 176.10.20.1
    - **Broadcast:** 176.10.20.128
    - **Total de Hosts Útiles:** 126  

- La red externa es la 200.4.4.0/24:
    - **Rango de Hosts:** 200.4.4.2 – 200.4.4.254
    - **Default gateway:** 200.4.4.1
    - **Broadcast:** 200.4.4.256
    - **Total de Hosts Útiles:** 254
 
- Red para los dispositivos de IoT externos -> 192.168.12.0/24:
    - **Rango de Hosts:** 192.168.12.2 – 192.168.12.2
    - **Default gateway:** 192.168.12.1
    - **Broadcast:** 192.168.12.256
    - **Total de Hosts Útiles:** 254

Aparte la red se divide en multiple vlans cada una con su propia IP, gateway y broadcast. 

| VLAN  | Descripción             | Red IP             | Gateway           | Broadcast           |
|-----|----------|----------|--------------------|----------------------|
| 100   | vlan 5     | 192.168.5.0/24   | 192.168.5.1      | 192.168.5.255      |
| 200      |  vlan 15      | 192.168.15.0/24   | 192.168.15.1      | 192.168.15.255      |
| 300      | vlan 25    | 192.168.25.0/24    | 192.168.25.1       | 192.168.25.255       |


**VLAN 11 – 192.168.11.0/24** Servidores

   - **Rango de Hosts:** 192.168.11.2 – 192.168.11.254
   - **DDefault gateway:** 192.168.11.1
   - **Broadcast:** 192.168.11.256
   - **Total de Hosts Útiles:** 254

Cada VLAN tiene su propia subred /24 (máscara de subred 255.255.255.0), lo cual permite hasta 254 hosts por segmento, ideal para entornos académicos de tamaño medio.

**VLAN 100 – 192.168.10.0/24** Recepción

   - **Rango de Hosts:** 192.168.10.2 – 192.168.10.254
   - **DDefault gateway:** 192.168.10.1
   - **Broadcast:** 192.168.10.256
   - **Total de Hosts Útiles:** 254

**VLAN 200 – 192.168.20.0/24** Planta 1

   - **Rango de Hosts:** 192.168.20.2 – 192.168.200.254
   - **Default gateway:** 192.168.20.1
   - **Broadcast:** 192.168.20.256
   - **Total de Hosts Útiles:** 254

**VLAN 300 – 192.168.30.0/24** Planta 2

- **Rango de Hosts:** 192.168.30.2 – 192.168.30.254
- **DDefault gateway:** 192.168.30.1
- **Broadcast:** 192.168.30.256
- **Total de Hosts Útiles:** 254

## Enrutamiento y Rutas Óptimas




### Enrutamiento por inundación en caso de error
El enrutamiento por inundacion debido a su gran carga sobre la red no se utiliza como un sistema principal viable, pero es util en caso de errores o conexiones caidas
- En caso de que se detecte una caida de la interfaz por la que deberia dirigirse el paquete, se imagina que el router no sabe otra ruta, se activaria el enrutamiento por inundacion:
   - Se envia el paquete por todas las interfaces conocidas
   - Se le asigna un TTL especifico para evitar un paquete infinito
   - Se espera que al enviarlo como un broadcas por todas partes se pueda aun llegar al destino

| Ventajas                        | Desventajas                           |
|----------------------------------|----------------------------------------|
| Garantiza entrega si hay camino | Genera tráfico redundante              |
| No requiere tabla de rutas      | Posibilidad de congestión en la red    |
| Resistente a fallos             | No escala bien en redes grandes        |



# Paso 4: Capa de Transporte – Selección de Protocolos y Cálculo del Tamaño de Ventana

## Selección de Protocolos

La elección del **protocolo de transporte** es esencial en el diseño de una red, ya que impacta directamente en la **eficiencia, fiabilidad y experiencia del usuario**. La selección se realiza según la **naturaleza del servicio** y los **requisitos del tráfico**.

### 1. Criterios Generales

- **TCP (Transmission Control Protocol)**  
  Se emplea en aplicaciones que requieren **transporte fiable**, con control de errores, confirmación de entrega y orden de paquetes. Es ideal para servicios donde la **integridad de los datos es crítica**, como transacciones financieras, acceso a plataformas administrativas o transferencia de archivos.

- **UDP (User Datagram Protocol)**  
  Se utiliza en servicios donde **la velocidad y la baja latencia** son más importantes que la fiabilidad, como **videoconferencias**, **telefonía IP** o **streaming en vivo**. UDP no garantiza entrega ni orden, pero permite que la transmisión continúe sin interrupciones si se pierden algunos paquetes, lo cual es aceptable en entornos en tiempo real.


### 2. Comparación según el tipo de tráfico

| Servicio / Aplicación                            | Protocolo usado | Justificación breve                                                  |
|:--------------------------------------------------|:----------------|:---------------------------------------------------------------------|
| Acceso a sistemas administrativos (ERP, Intranet, CRM) | **TCP**        | Requiere fiabilidad total en el transporte de datos.                |
| Transferencia de archivos (FTP, SFTP, SCP)       | **TCP**         | Necesita transmisión íntegra y segura de archivos.                  |
| Correo electrónico (SMTP, IMAP, POP3)            | **TCP**         | Garantiza entrega completa y ordenada de mensajes.                  |
| Navegación web (HTTP/HTTPS)                      | **TCP**         | Necesita fiabilidad en la entrega de páginas y datos.               |
| Cámaras IP de seguridad (streaming)              | **UDP**         | Prioriza la inmediatez de video frente a errores menores.           |
| Telefonía IP (VoIP)                              | **UDP**         | Baja latencia es más crítica que la corrección de errores.          |
| Sensores IoT (telemetría continua)               | **UDP**         | El envío constante de datos en tiempo real es prioritario.          |
| Videoconferencia en vivo (WebRTC, Zoom, etc.)    | **UDP**         | Necesita fluidez en tiempo real, aceptando posible pérdida mínima.  |

---

### 3. Consideraciones específicas

- Para **transferencia de archivos**, como documentos, proyectos o recursos digitales, se recomienda **TCP**.  
  Sus características como **control de flujo, retransmisión de paquetes, y corrección de errores** garantizan la **integridad** de la información, aunque introduzca una ligera latencia.

- Para **servicios en tiempo real**, como videollamadas, videovigilancia o transmisiones en vivo, se opta por **UDP**.  
  Su naturaleza sin conexión y sin necesidad de confirmaciones permite una **baja latencia** y mayor fluidez, incluso si hay pérdidas menores de datos, lo cual es aceptable en estos contextos.


## Cálculo del Tamaño de Ventana en TCP

#### Parámetros medidos:
Utilizando un ping de un ordenador a otro de la red se obtienen estos valores

- **RTT promedio observado en la simulación:** `1 ms`
- **RTT convertido a segundos:** `RTT = 1 ms = 0.001 segundos`
- **Ancho de banda simulado:** `100 Mbps`

####  Cálculo:

Se aplica la fórmula:


$$\text{Ventana (bytes)} = \frac{Ancho de Banda (bps) \times RTT (seg)}{8}$$



$$\text{Ventana (bytes)} = \frac{100,000,000 \times 0.001}{8} = \frac{100,000}{8} = 12,500 \text{ bytes}$$

Luego, calculamos cuántos segmentos TCP de tamaño estándar (MSS) se pueden enviar:

$$\text{Cálculo de segmentos TCP (MSS = 1460 bytes) }$$

$$
\text{Segmentos} = \frac{12,500}{1460} \approx 8 \text{ segmentos}
$$

$_\text{El ancho en de 100Mbps dado que ese es el maximo en cisco packet tracer}$

#### Resultado:

El tamaño óptimo de la ventana de transmisión TCP en los enlaces simulados es de aproximadamente **12,500 bytes**, lo que equivale a unos **8 segmentos TCP** de 1460 bytes. Este tamaño garantiza una transmisión eficiente, minimizando esperas por confirmaciones y aprovechando al máximo la capacidad del canal.


# Paso 5: Capa de Aplicación – Servicios, Multiplexación y Multimedia

## Implementación de Servicios y Resolución de Nombres
### 1. Diseño la configuración


### 2. Proceso de Resolución de Nombres

1. El cliente solicita un dominio (ej. `www.campus.edu`).
2. La consulta es enviada al servidor DNS local configurado.
3. Si no tiene la entrada en caché, consulta a servidores superiores.
4. Una vez resuelta, la IP se devuelve al cliente.
5. El cliente usa esa IP para conectarse al servidor correspondiente.

> **Caché de DNS**: mejora el rendimiento al guardar respuestas anteriores y reducir tráfico.


## Servicios Multimedia:

Se emplearán dos enfoques distintos, optimizados según la naturaleza del servicio:

#### 1. UDP Streaming (para Cámaras de Seguridad)

- Utiliza protocolos como **RTP (Real-time Transport Protocol)** sobre **UDP**.
- Se establece un flujo continuo de datos desde la cámara al servidor o cliente visualizador.
- **Ventajas**:
  - Baja latencia.
  - No se detiene si hay pérdida de paquetes.
- **Aplicación ideal**: monitoreo en vivo de cámaras IP, donde la fluidez es más importante que la precisión de cada fotograma.

#### 2. Adaptive HTTP Streaming (para Eventos Públicos)

- Se usará **DASH (Dynamic Adaptive Streaming over HTTP)** o **HLS (HTTP Live Streaming)**.
- El contenido se divide en fragmentos de video codificados en diferentes calidades.
- El cliente selecciona automáticamente la calidad adecuada según su ancho de banda.
- **Ventajas**:
  - Compatible con navegadores web estándar.
  - Escalable mediante servidores HTTP.
- **Aplicación ideal**: transmisión de conferencias, eventos públicos y contenido multimedia institucional.


### Adaptación de Calidad según Ancho de Banda

Para asegurar una experiencia óptima a todos los usuarios, independientemente de sus condiciones de red, se aplicarán las siguientes técnicas:

- **Detección de ancho de banda en tiempo real**: el cliente mide la velocidad de descarga y selecciona el nivel de calidad más adecuado.
- **Cambio dinámico de resolución**: el reproductor puede cambiar entre calidades (por ejemplo, de 1080p a 480p) durante la reproducción sin cortar la transmisión.
- **Codificación múltiple del contenido**: los servidores almacenarán y entregarán varias versiones del mismo contenido a diferentes tasas de bits.
- **Buffer adaptativo**: se gestiona un búfer inteligente para equilibrar entre fluidez y calidad.

> En enlaces críticos, se priorizará el tráfico multimedia mediante políticas de **Quality of Service (QoS)** para garantizar estabilidad y reducir la latencia.

