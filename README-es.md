# Guía para el TFT LCD HiLetgo de 3.5"

Esta guía proporciona instrucciones detalladas sobre cómo configurar y utilizar el TFT LCD HiLetgo de 3.5" con una resolución de 480 x 320 píxeles. Creé esta guía porque esta pantalla específica puede ser un verdadero dolor de cabeza para configurar. Espero que esta guía te ahorre tiempo y frustración.

## Tabla de Contenidos

1. [Introducción](#introducción)
2. [Características](#características)
3. [Requisitos](#requisitos)
4. [Diagrama de Conexión](#diagrama-de-conexión)
5. [Instrucciones de Configuración](#instrucciones-de-configuración)
6. [Código de Ejemplo](#código-de-ejemplo)
7. [Solución de Problemas](#solución-de-problemas)
8. [Referencias](#referencias)
9. [Licencia](#licencia)

------

## Introducción

El TFT LCD HiLetgo de 3.5" es un módulo de pantalla versátil compatible con varios microcontroladores, incluyendo el Arduino Mega 2560. Esta guía se basa en mi experiencia con el Arduino Mega 2560 y tiene como objetivo ayudarte a configurar y utilizar la pantalla de manera efectiva.

## Características

- **Resolución**: 480 x 320 píxeles
- **Interfaz**: Paralela de 16 bits
- **Tamaño de la Pantalla**: 3.5 pulgadas
- **Controlador IC**: HX8357B, HX8357C, ILI9481 o ILI9486
- **Voltaje de Operación**: 3.3V/5V
- **Pantalla Táctil**: No

## Requisitos

### Hardware

- TFT LCD HiLetgo de 3.5"
- Arduino Mega 2560
- Cables de conexión (macho a macho)
- Protoboard (opcional)

### Software

- Arduino IDE
- Biblioteca **TFT_HX8357**

## Diagrama de Conexión

Debido a que esta pantalla utiliza una interfaz paralela de 16 bits, requiere múltiples conexiones al Arduino Mega 2560. A continuación, se muestra la asignación de pines:

### Pines de Control

| Pin del TFT LCD | Pin del Arduino Mega                               |
| --------------- | -------------------------------------------------- |
| VCC             | 5V                                                 |
| GND             | GND                                                |
| CS              | 40                                                 |
| RESET           | 38                                                 |
| RS (DC)         | 39                                                 |
| WR              | 41                                                 |
| RD              | 43                                                 |
| LED             | 3.3V (a través de una resistencia si es necesario) |

### Pines de Datos

| Pin del TFT LCD | Pin del Arduino Mega |
| --------------- | -------------------- |
| DB0             | 22                   |
| DB1             | 23                   |
| DB2             | 24                   |
| DB3             | 25                   |
| DB4             | 26                   |
| DB5             | 27                   |
| DB6             | 28                   |
| DB7             | 29                   |
| DB8             | 30                   |
| DB9             | 31                   |
| DB10            | 32                   |
| DB11            | 33                   |
| DB12            | 34                   |
| DB13            | 35                   |
| DB14            | 36                   |
| DB15            | 37                   |

**Nota**: Asegúrate de que todas las conexiones estén firmes y verifica dos veces los números de los pines.

## Instrucciones de Configuración

### 1. Conectar el Hardware

- Sigue el diagrama de conexión anterior para conectar tu TFT LCD HiLetgo de 3.5" al Arduino Mega 2560.
- Asegúrate de conectar todos los pines de datos y control correctamente.

### 2. Instalar la Biblioteca **TFT_HX8357**

- Descarga la biblioteca **TFT_HX8357** desde el [repositorio de GitHub](https://github.com/Bodmer/TFT_HX8357).
- Extrae el contenido del archivo ZIP.
- Copia la carpeta **TFT_HX8357** en tu directorio de bibliotecas de Arduino (generalmente `Documentos/Arduino/libraries`).
- Reinicia el Arduino IDE para que reconozca la nueva biblioteca.

### 3. Configurar la Biblioteca

- Navega hasta el archivo `User_Setup.h` dentro de la carpeta de la biblioteca **TFT_HX8357**.

- Abre `User_Setup.h` con un editor de texto.

- Selecciona el controlador adecuado para tu pantalla:

  Descomenta el controlador que corresponda y comenta los demás. Por ejemplo, si tu pantalla utiliza el controlador **HX8357B**:

  ```
  cpp
  
  
  Copy code
  #define HX8357B
  //#define HX8357C
  //#define ILI9481
  //#define ILI9486
  ```

- Establece las dimensiones de la pantalla:

  ```
  cpp
  
  
  Copy code
  #define HX8357_TFTWIDTH  320
  #define HX8357_TFTHEIGHT 480
  ```

- Configura las fuentes que deseas utilizar. Puedes comentar las que no necesites para ahorrar memoria:

  ```
  cpp
  
  
  Copy code
  #define LOAD_GLCD   // Fuente 1
  #define LOAD_FONT2  // Fuente 2
  #define LOAD_FONT4  // Fuente 4
  #define LOAD_FONT6  // Fuente 6
  #define LOAD_FONT7  // Fuente 7
  #define LOAD_FONT8  // Fuente 8
  #define LOAD_GFXFF  // Fuentes gratuitas de Adafruit
  ```

- Guarda los cambios en `User_Setup.h`.

### 4. Subir el Código de Ejemplo

- Abre el Arduino IDE.
- Navega a `Archivo` > `Ejemplos` > `TFT_HX8357` y selecciona un ejemplo como `graphicstest`.
- Verifica que el código se compile sin errores.
- Sube el código a tu Arduino Mega 2560.

## Código de Ejemplo

Aquí tienes un ejemplo sencillo que muestra texto y formas en la pantalla:

```
cpp


Copy code
#include <TFT_HX8357.h>  // Biblioteca específica del hardware

TFT_HX8357 tft = TFT_HX8357();  // Crear objeto de pantalla

void setup() {
  tft.init();
  tft.setRotation(1);  // Ajusta la rotación según sea necesario
  tft.fillScreen(TFT_BLACK);

  // Mostrar texto
  tft.setTextColor(TFT_WHITE, TFT_BLACK);
  tft.setTextSize(2);
  tft.setCursor(50, 50);
  tft.println("¡Hola, Mundo!");

  // Dibujar un círculo
  tft.drawCircle(160, 120, 50, TFT_RED);
}

void loop() {
  // Tu código aquí
}
```

**Explicación**:

- **tft.init()**: Inicializa la pantalla.
- **tft.setRotation(1)**: Establece la orientación de la pantalla.
- **tft.fillScreen(TFT_BLACK)**: Rellena la pantalla con color negro.
- **tft.setTextColor(TFT_WHITE, TFT_BLACK)**: Establece el color del texto y el fondo.
- **tft.setTextSize(2)**: Establece el tamaño del texto.
- **tft.setCursor(50, 50)**: Establece la posición del cursor.
- **tft.println("¡Hola, Mundo!")**: Muestra el texto en la pantalla.
- **tft.drawCircle(160, 120, 50, TFT_RED)**: Dibuja un círculo rojo.

## Solución de Problemas

- **Pantalla en blanco**: Verifica todas las conexiones y asegúrate de que el controlador correcto esté seleccionado en `User_Setup.h`.
- **Errores de compilación**: Asegúrate de que la biblioteca **TFT_HX8357** esté instalada correctamente y que no haya conflictos con otras bibliotecas.
- **Orientación incorrecta**: Ajusta el parámetro en `tft.setRotation()`.

## Referencias

- [Repositorio de la biblioteca TFT_HX8357](https://github.com/Bodmer/TFT_HX8357)
- [Página del producto TFT LCD HiLetgo de 3.5"](https://www.hiletgo.com/)