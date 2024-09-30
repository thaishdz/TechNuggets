

# Codificación de texto

Aquí, cada byte contiene una parte de la información necesaria para representar un carácter.

![image](https://github.com/user-attachments/assets/02b9e950-38b7-4537-9c01-79050fe67322)


## ASCII vs Unicode

1. **Rango de caracteres:**
   - **ASCII**: Fue desarrollado en los años 60 y solo puede representar 128 caracteres. Incluye letras mayúsculas y minúsculas del alfabeto inglés, números, algunos símbolos comunes y caracteres de control (como el espacio y el retorno de carro). Funciona solo con caracteres latinos básicos.
     
   - **Unicode**: Es mucho más amplio. Puede representar **más de 143,000 caracteres** (en diferentes versiones) e incluye prácticamente todos los caracteres de todos los idiomas del mundo, además de emojis, símbolos matemáticos, etc.

2. **Tamaño de los caracteres:**
   - **ASCII**: Cada carácter está codificado en **7 bits**, lo que permite representar los 128 caracteres.
     
   - **Unicode**: Tiene diferentes formatos de codificación (`UTF-8`, `UTF-16`, `UTF-32`) que usan distintos tamaños. **UTF-8**, que es el más común, utiliza entre **1 y 4 bytes** por carácter, lo que le permite representar una enorme cantidad de símbolos y caracteres.

3. **Compatibilidad:**
   - **ASCII**: Al ser limitado a caracteres en inglés, no es adecuado para representar textos en otros idiomas o con caracteres especiales.
  
   - **Unicode**: Es compatible con **ASCII** porque los primeros 128 caracteres de Unicode son los mismos que en ASCII, pero además incluye una enorme variedad de caracteres adicionales.

### Recapitulando ...

- `ASCII` es un subconjunto de `Unicode`
- `Unicode` fue diseñado para soportar una gama mucho más amplia de caracteres.
- `Unicode` es hoy el estándar dominante en la mayoría de las aplicaciones 🥇

## Diferencia entre `Unicode` y `UTF-8`

- `Unicode` es un estándar que asigna un número único a cada carácter de casi todos los sistemas de escritura del mundo.
  -  `U+0041` para la letra `A`
  -  `U+1F600` para el emoji 😀.
  
- `UTF-8` es un método para codificar esos números ☝️ como una secuencia de bytes.
  - Utiliza entre 1 y 4 bytes para representar cada carácter.
  - El número de bytes depende del carácter específico.

## Codificación de caracteres en `UTF-8` - Ejemplos

- **1 byte** para caracteres simples (los más comunes, como los de **ASCII**).
- **2, 3 o 4 bytes** para caracteres menos comunes o más complejos (como caracteres de otros alfabetos, símbolos o emojis).

### Ejemplo de 1 byte (caracteres ASCII):
Los __primeros 128 caracteres de Unicode__ (del 0 al 127) coinciden con los caracteres ASCII, como letras y números.

Por ejemplo:
- El carácter `A` tiene el código Unicode `U+0041` (decimal: 65).
- En **UTF-8**, el carácter `A` se codifica con **1 byte**: `01000001` en binario o `0x41` en hexadecimal (equivalente a 65 en decimal).

👉 Esto significa que el carácter `A` ocupa **exactamente 1 byte** en la memoria.

### Ejemplo de 2 bytes:
Los __caracteres fuera del rango ASCII__ necesitan más de 1 byte para representarse.

Por ejemplo:
- El carácter `é` (e con acento agudo) tiene el código Unicode `U+00E9` (decimal: 233).
- En **UTF-8**, `é` se codifica con **2 bytes**: `11000011 10101001` en binario, o `0xC3 0xA9` en hexadecimal.

👉 Esto significa que el carácter `é` ocupa **2 bytes** en UTF-8.

### Ejemplo de 3 bytes:
Algunos símbolos o letras de alfabetos no latinos usan más bytes.

Por ejemplo:
- El símbolo de la moneda **€** (euro) tiene el código Unicode `U+20AC` (decimal: 8364).
- En **UTF-8**, el símbolo `€` se codifica con **3 bytes**: `11100010 10000010 10101100` en binario, o `0xE2 0x82 0xAC` en hexadecimal.

👉 Esto significa que el símbolo `€` ocupa **3 bytes**.

### Ejemplo de 4 bytes:

Los __caracteres más complejos__, como algunos emojis o caracteres de lenguas antiguas, requieren 4 bytes.

Por ejemplo:
- El emoji 😀 (cara sonriente) tiene el código Unicode `U+1F600` (decimal: 128512).
- En **UTF-8**, el emoji 😀 se codifica con **4 bytes**: `11110000 10011111 10011000 10000000` en binario, o `0xF0 0x9F 0x98 0x80` en hexadecimal.

👉 Esto significa que el emoji 😀 ocupa **4 bytes**.

### ¿Por qué UTF-8 usa múltiples bytes?
Porque **no todos los caracteres ocupan el mismo espacio**. Los caracteres más comunes, como las letras del alfabeto latino (`A-Z`, `a-z`, números), caben en **1 byte**, mientras que los caracteres más complejos o raros, como emojis o ideogramas chinos, necesitan **más bytes**.

Este esquema de "longitud variable" hace que UTF-8 sea **muy eficiente**, porque los textos con muchos caracteres latinos ocupan menos espacio en comparación con otros sistemas que usan un número fijo de bytes para cada carácter.

### Ejemplo práctico de cómo se almacenan los caracteres en `UTF-8`
Supongamos que tienes la siguiente cadena de texto:

```text
Hola 😀
```

El texto "Hola" tiene caracteres en el rango ASCII, así que cada letra ocupará **1 byte**:

- `H`: 1 byte (`0x48`)
- `o`: 1 byte (`0x6F`)
- `l`: 1 byte (`0x6C`)
- `a`: 1 byte (`0x61`)

El emoji 😀, como ya vimos, ocupa **4 bytes**: `0xF0 0x9F 0x98 0x80`.

Entonces, para la cadena `"Hola 😀"`, la codificación UTF-8 se vería así:

```text
48 6F 6C 61 F0 9F 98 80
```

Esto significa que la cadena completa ocupa **8 bytes** (4 bytes para "Hola" y 4 bytes para el emoji).

### Ventajas de usar múltiples bytes
- **Eficiencia**: Textos cortos en lenguajes basados en caracteres latinos ocupan menos espacio porque usan solo 1 byte por carácter.
- **Flexibilidad**: UTF-8 puede representar cualquier carácter en Unicode, desde letras básicas hasta símbolos complejos, como emojis o caracteres chinos.

---

### Resumen: 
- UTF-8 usa entre **1 y 4 bytes** para representar diferentes caracteres.
  - Los caracteres simples (como `A`) usan 1 byte.
  - Caracteres más complejos, como `é` o emojis como 😀, pueden usar 2, 3 o 4 bytes.
  
