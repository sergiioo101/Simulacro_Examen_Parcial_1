# Simulacro_Examen_Parcial_1
https://github.com/sergiioo101/Simulacro_Examen_Parcial_1.git

A continuación tienes una versión en Markdown que puede verse correctamente en un README de GitHub. Todas las fórmulas se han convertido en texto o se han encapsulado en bloques de código para evitar problemas de visualización. Si tu repositorio cuenta con alguna extensión que renderice LaTeX, puedes reintroducir la notación típica de LaTeX; de lo contrario, lo más seguro es usar texto y bloques de código tal y como se muestra aquí.

---

# PARTE I

---

## Pregunta 1 A)

A partir de los apuntes proporcionados, podemos extraer las siguientes diferencias principales entre el modelo **OSI** y el modelo **TCP/IP**:

1. **Número de capas**  
   - **Modelo OSI**: Consta de **siete capas** (Física, Enlace de Datos, Red, Transporte, Sesión, Presentación y Aplicación).  
   - **Modelo TCP/IP**: Agrupa las capas Física y de Enlace en una sola (llamada “Enlace” o “Acceso a la red”) y fusiona las capas de Sesión, Presentación y Aplicación en una sola capa de Aplicación, quedando en **cuatro capas** (Enlace/Acceso, Internet, Transporte y Aplicación).

2. **Orientación (teórica vs. práctica)**  
   - **Modelo OSI**: Fue desarrollado como un **modelo general** por la ISO (International Organization for Standardization), definiendo con detalle las funciones de cada capa, los servicios y las interfaces.  
   - **Modelo TCP/IP**: Surge de la **implementación práctica** en redes (Internet), enfatizando el uso real de protocolos como IP en la capa de Internet y TCP/UDP en la capa de Transporte.

3. **Manejo de la capa de aplicación**  
   - En el **modelo OSI**, existen tres capas por encima de Transporte (Sesión, Presentación y Aplicación), cada una con funciones específicas (administración de sesión, conversión de formatos de datos, etc.).  
   - En el **modelo TCP/IP**, todas esas funciones se concentran en **una sola capa de Aplicación**, en la cual residen protocolos como TELNET, FTP, SMTP y DNS.

Estas diferencias reflejan principalmente que el modelo OSI ofrece una **separación más detallada** de funciones en siete capas, mientras que el modelo TCP/IP agrupa varias de esas capas en niveles más amplios, basándose en la implementación real de las redes.

---

## Pregunta 1 B)

A partir del texto proporcionado, podemos resumir las **ventajas y limitaciones** de cada modelo de la siguiente manera:

### Modelo OSI

- **Ventajas**:  
  - Descripción muy clara y detallada de funciones en cada una de las siete capas.  
  - Permite cambiar protocolos sin afectar a otras capas, siempre que se mantenga el servicio definido.

- **Limitaciones**:  
  - Su separación tan detallada (por ejemplo, capas de Sesión y Presentación) a veces no coincide con la práctica real de las redes.  
  - Puede resultar más complejo en la implementación.

### Modelo TCP/IP

- **Ventajas**:  
  - Agrupa capas y simplifica la implementación (por ejemplo, combina las capas Física y de Enlace, y reúne Sesión, Presentación y Aplicación).  
  - Ofrece dos protocolos de transporte (TCP y UDP) que cubren necesidades distintas (fiabilidad vs. rapidez).

- **Limitaciones**:  
  - No expone tan claramente las funciones de Sesión y Presentación, pues las integra en la capa de Aplicación.  
  - La capa de Internet (IP) no está orientada a conexión, por lo que parte de la fiabilidad depende de la capa de Transporte o de la aplicación.

---

## Pregunta 2

**Capa de Transporte en el modelo OSI**  
La capa de transporte se ocupa de **segmentar** los datos recibidos de la capa de red y de enviarlos de **extremo a extremo**. En este modelo, puede ofrecer un servicio **libre de errores** (con confirmaciones y entrega ordenada) o **mensajes aislados** (sin garantía de orden ni confirmación). De esta forma, protege a las capas superiores de los detalles y variaciones en las capas inferiores.

**Capa de Transporte en el modelo TCP/IP**  
Esta capa también proporciona **comunicación extremo a extremo**, pero basa sus funciones en dos protocolos principales:

- **TCP (Transmission Control Protocol)**: ofrece fiabilidad, está orientado a conexión y asegura la entrega ordenada de los datos.  
- **UDP (User Data Protocol)**: es más simple, no garantiza confirmaciones ni orden de entrega, siendo útil en aplicaciones donde la pérdida de algunos paquetes no afecta críticamente al servicio.

---

## Pregunta 3

1. **Orientación a conexión**  
   - **TCP**: Orientado a conexión (establece una sesión antes de enviar datos).  
   - **UDP**: No orientado a conexión (envía datos sin sesión previa).

2. **Fiabilidad y control de errores**  
   - **TCP**: Confiable, usa confirmaciones y retransmisiones para asegurar entrega y orden.  
   - **UDP**: No confiable, no garantiza llegada ni orden de los datos.

3. **Velocidad y orden de entrega**  
   - **TCP**: Más lento debido a controles de fiabilidad, asegura el orden.  
   - **UDP**: Más rápido, sin orden garantizado.

4. **Ejemplos de uso**  
   - **TCP**: Cuando es crítica la entrega sin pérdidas (ejemplo: aplicaciones con datos sensibles).  
   - **UDP**: Escenarios donde se prioriza la rapidez y se toleran pérdidas (ejemplo: transmisión de datos en tiempo real).

---

## Pregunta 4

**a) Protocolo tradicional para transferencia de archivos**  
El protocolo más habitual en la capa de Aplicación para este fin es **FTP (File Transfer Protocol)**, que permite subir, descargar, renombrar y manipular archivos entre un cliente y un servidor.

**b) Alternativas en seguridad y funcionalidad**  
- **SFTP (SSH File Transfer Protocol)**: Utiliza cifrado y autenticación por SSH (puerto 22), de modo que todos los datos y credenciales viajan protegidos en un canal único.  
- **FTPS (FTP sobre SSL/TLS)**: Agrega cifrado SSL/TLS a FTP, protegiendo información y credenciales. Conserva la estructura de canales de FTP, por lo que suele requerir configuraciones adicionales en cortafuegos y routers.

---

## Pregunta 5

Cuando el usuario escribe una URL en el navegador, primero se revisa la **caché** del sistema (o del propio navegador) para ver si ya se conoce la dirección IP asociada. Si no está en caché, la petición se envía al **servidor DNS local**, que puede hacer consultas recursivas a otros servidores para encontrar la IP.

Si el servidor DNS local no tiene la respuesta, primero consulta a uno de los **servidores raíz**. Estos servidores raíz indican cuál es el servidor encargado de manejar el **dominio de nivel superior** (por ejemplo, `.com`). A continuación, se consulta al servidor TLD correspondiente, que señala el **servidor autoritativo** para el dominio específico (por ejemplo, `ejemplo.com`). Este último servidor responde con la dirección IP del host requerido (por ejemplo, `www.ejemplo.com`).

Finalmente, el servidor DNS local guarda esa información en su caché y la remite al cliente, que ahora sabe a qué IP conectarse. Con la dirección IP resuelta, el navegador establece la conexión (por lo general TCP) con el servidor web y empieza la transferencia de datos.

---

## Pregunta 6

En el **modelo TCP/IP**, la comunicación entre dos dispositivos se basa en el proceso de **encapsulación** de datos a través de cuatro capas:

1. **Capa de Aplicación**  
   Aquí se generan o consumen los datos que manejan las aplicaciones de usuario (como un navegador web o un cliente de correo). Protocolos como HTTP, FTP o SMTP determinan cómo se formatea y procesa la información. Al enviar datos, esta capa produce el contenido que se entregará a la capa de Transporte.

2. **Capa de Transporte**  
   Recibe los datos de la capa de Aplicación y los segmenta en unidades más pequeñas (por ejemplo, segmentos en TCP). De acuerdo con el protocolo utilizado (TCP o UDP), se añaden cabeceras con puertos de origen/destino y, en el caso de TCP, números de secuencia y confirmaciones que garantizan una entrega fiable.

   - **TCP**: orientado a conexión, comprueba la entrega y el orden.  
   - **UDP**: no orientado a conexión, no asegura el orden ni las confirmaciones.

3. **Capa de Internet (IP)**  
   Encapsula los datos de Transporte en **paquetes IP**, añadiendo direcciones IP de origen y destino. Su objetivo principal es **encaminar** esos paquetes de un nodo al otro a través de la red, gestionando posibles saltos intermedios (routers). Esta capa no garantiza fiabilidad; se limita a intentar entregar los paquetes a la dirección destino.

4. **Capa de Acceso a Red (Enlace + Física)**  
   Adapta los paquetes IP para que viajen por el medio físico de la red local (Ethernet, Wi-Fi, etc.). Añade una cabecera y, a menudo, un tráiler que contiene direcciones MAC y datos de verificación (CRC). La parte Física finalmente se encarga de la transmisión de los bits (señales) por cables o medios inalámbricos.

**Recepción**: En el dispositivo receptor, el proceso se realiza a la inversa. Desde la capa Física, los bits se agrupan en tramas de la capa de Enlace, se extrae el paquete IP para la capa de Internet, y luego el segmento para la capa de Transporte. Finalmente, los datos llegan a la capa de Aplicación, donde la información se interpreta por el software correspondiente.

---

# PARTE II

---

## Pregunta 7 (Fórmula de Shannon)

La **Fórmula de Shannon** se expresa así:

```
C = B * log2(1 + SNR_lineal)
```

Donde:  
- `C` es la capacidad o tasa máxima de transmisión.  
- `B` es el ancho de banda.  
- `SNR_lineal` es la relación señal/ruido en escala lineal.

Datos del problema:  
- Ancho de banda: B = 500 MHz = 500 × 10^6 Hz  
- SNR = 20 dB

1. **Conversión de SNR de dB a escala lineal**  

   Una SNR de 20 dB se convierte a escala lineal como:
   ```
   SNR_lineal = 10^(20/10) = 10^2 = 100
   ```

2. **Cálculo de la capacidad**  

   ```
   C = 500 × 10^6 * log2(1 + 100)
   ```
   Dado que 1 + 100 = 101,  
   ```
   log2(101) ≈ 6.66
   ```
   Por lo tanto,  
   ```
   C ≈ 500 × 10^6 × 6.66
     = 3.33 × 10^9 bps
     = 3.33 Gbps
   ```

**Respuesta**:  
La tasa de transmisión máxima aproximada para un canal con 500 MHz de ancho de banda y 20 dB de SNR es de **3.33 Gbps**.

---

## Pregunta 8 (Ubicación de portadoras)

Se dispone de una primera portadora a 1.2 GHz y cada canal tiene un ancho de banda en banda base de 300 MHz. Se pide calcular la portadora anterior y posterior:

1. **Frecuencia de la portadora anterior**  
   ```
   1.2 GHz - 300 MHz = 0.9 GHz
   ```

2. **Frecuencia de la portadora posterior**  
   ```
   1.2 GHz + 300 MHz = 1.5 GHz
   ```

**Justificación e importancia**  
Estas frecuencias se separan en al menos 300 MHz para evitar solapamientos entre canales y, por tanto, interferencias. Una correcta ubicación de las portadoras en el espectro permite un uso más eficiente del ancho de banda, asegurando que cada canal disponga del espacio necesario para su transmisión sin interferir con los demás.

---

## Pregunta 9 (Orden de modulaciones según robustez)

Ordenar las modulaciones de mayor a menor robustez ante el ruido (para una misma SNR). Cuanto más símbolos posee la constelación, más sensible es al ruido:

1. BPSK (2-QAM)  
2. QPSK (4 símbolos)  
3. 16-QAM  
4. 64-QAM  
5. 256-QAM

**Justificación**  
- BPSK, con solo 2 símbolos, presenta la mayor distancia entre constelaciones y, por tanto, mayor tolerancia al ruido.  
- A medida que crece el número de símbolos (QPSK, 16-QAM, 64-QAM, 256-QAM), aumenta la eficiencia espectral pero disminuye la robustez frente al ruido debido a la menor distancia entre puntos de constelación.

---

## Pregunta 10 (Encapsulamiento y eficiencia)

1. **(a) Tamaño del mensaje tras agregar cabeceras de capas 4 y 3**  
   - Bloque original (Capa 5):  
     1.5 Kbytes = 1.5 × 1024 = 1536 bytes  
   - Suma de cabeceras (Capas 4 y 3): 40 + 40 = 80 bytes  
   - Total: 1536 + 80 = 1616 bytes

2. **(b) Fragmentación en tramas de 400 bytes (Capa 2)**  
   ```
   1616 bytes / 400 bytes/trama ≈ 4.04 → 5 tramas
   ```

3. **(c) Sobrecarga de la Capa 1**  
   - Se añaden 3 bytes de sobrecarga por cada 2 bytes de datos (1 byte de inicio, 1 de parada y 1 de CRC).  
   - En una trama de 400 bytes:  
     ```
     400 bytes / 2 bytes/segmento = 200 segmentos
     200 segmentos × 3 bytes = 600 bytes de sobrecarga
     ```
   - Cada trama pasa de 400 bytes a 1000 bytes totales en la capa física (400 + 600).

4. **(d) Eficiencia del sistema**  
   - Total de datos transmitidos:  
     ```
     5 tramas × 1000 bytes/trama = 5000 bytes
     ```
   - Datos útiles: 1536 bytes del bloque original (Capa 5).  
   - Eficiencia:
     ```
     (1536 / 5000) × 100% ≈ 30.72%
     ```

**Conclusión**  
- El bloque final (Capa 5) es de 1616 bytes.  
- Se requieren 5 tramas de 400 bytes cada una en Capa 2.  
- Cada trama añade 600 bytes de sobrecarga en Capa 1, resultando 1000 bytes por trama.  
- En total se transmiten 5000 bytes, de los cuales 1536 son datos útiles.  
- La eficiencia aproximada es **30.72%**.

