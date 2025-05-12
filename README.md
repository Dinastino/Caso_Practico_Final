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




# Paso 2: Capa Física – Cálculos y Selección de Tecnologías

## Cálculo de la Capacidad de los Enlaces

Se utiliza la fórmula de Shannon:  

$$Donde: C = B * log_2(1+SNR)$$  

Ancho de banda (B)  

SNR: relación señal a ruido determinada.   
La relación señal a ruido se mide en dB en un ancho de banda es:    

$$𝑆𝑁𝑅 = 10 𝑙𝑜𝑔_{10}(𝑆𝑁𝑅) = 10^{\frac{SNR}{10}} [dB]$$  

