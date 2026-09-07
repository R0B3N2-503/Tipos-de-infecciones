# 🛡️ Guía Completa de Ciberseguridad: Virus, Clasificación, Diagnóstico y Protección

[![Seguridad Informática](https://img.shields.io/badge/Ciberseguridad-Virus%20%26%20Malware-blue.svg)](https://www.cisa.gov/uscert/ncas/tips)
[![Herramientas CMD](https://img.shields.io/badge/Herramientas-Windows%20CMD-0078D6.svg)](https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/windows-commands)
[![NIST Framework](https://img.shields.io/badge/Marco%20de%20Seguridad-NIST%20CSF-green.svg)](https://www.nist.gov/cyberframework)

Bienvenido a esta guía educativa sobre **virus informáticos, categorías de malware, niveles de daño, estrategias de defensa y diagnóstico mediante la consola de comandos (CMD)**. Este repositorio está estructurado para servir como documento de referencia y aprendizaje en proyectos de ciberseguridad.

---

## 📋 Tabla de Contenidos
1. [¿Qué es un Virus Informático y Cómo Funciona?](#1-qué-es-un-virus-informático-y-cómo-funciona)
2. [Categorías Generales de Virus](#2-categorías-generales-de-virus)
3. [Virus de Daño Bajo: Funcionamiento y Ejemplos](#3-virus-de-daño-bajo-funcionamiento-y-ejemplos)
4. [10 Tipos de Virus y sus Impactos](#4-10-tipos-de-virus-y-sus-impactos)
5. [Mecanismos y Tipos de Protección](#5-mecanismos-y-tipos-de-protección)
6. [Cómo Analizar y Detectar Virus usando el CMD (Windows)](#6-cómo-analizar-y-detectar-virus-usando-el-cmd-windows)
7. [Contribuciones](#8-contribuciones)

---

## 1. ¿Qué es un Virus Informático y Cómo Funciona?

Un **virus informático** es un fragmento de código malicioso (*malware*) diseñado para insertarse en otros archivos o programas ejecutables del sistema sin el consentimiento ni conocimiento del usuario.

### Ciclo de vida y funcionamiento:
* **Infección / Acoplamiento:** El virus se adhiere a un programa huésped, documento u orden de arranque.
* **Fase de Latencia:** Permanece inactivo hasta que se cumple una condición predeterminada (por ejemplo, una fecha específica o la ejecución de una aplicación).
* **Propagación:** Una vez activado, copia su código e infecta otros componentes o archivos dentro del disco o la red.
* **Ejecución del Payload (Carga Útil):** Despliega su objetivo final (modificar archivos, recopilar datos, ralentizar la máquina o corromper el sistema).

---

## 2. Categorías Generales de Virus

Los virus se clasifican según su método de propagación, forma de ocultación o el área del sistema que atacan:

* **Según su Alojamiento:**
  * 🧠 **Residentes en Memoria:** Se cargan directamente en la memoria RAM y permanecen activos tras cerrar el programa infectado original.
  * ⚡ **Acción Directa:** Se ejecutan únicamente al abrir el archivo infectado y luego detienen su actividad.
* **Según su Objetivo:**
  * 🥾 **Sector de Arranque (Boot Sector / MBR):** Atacan el código de inicio del disco duro para ejecutarse antes de que se cargue el sistema operativo.
  * 📄 **Virus de Macro:** Infectan plantillas y documentos creados en suites ofimáticas (Microsoft Word, Excel).
  * 📁 **Virus de Archivos/Infectores de Ficheros:** Infectan archivos ejecutables (`.exe`, `.com`, `.bat`, `.dll`).
* **Según su Evasión:**
  * 🎭 **Polimórficos / Metamórficos:** Modifican su encriptación o reescriben su código fuente en cada nueva infección para eludir los motores antivirus por firmas.
  * 🧬 **Multipartitos:** Combinan simultáneamente diferentes técnicas de infección (ejemplo: infectan tanto ejecutables como el MBR).

---

## 3. Virus de Daño Bajo: Funcionamiento y Ejemplos

### ¿Qué es un virus de daño bajo?
Un **virus de daño bajo** (o malware de impacto leve) es aquel cuya intención principal **no es destruir hardware, robar contraseñas ni borrar datos personales**. Su objetivo es molestar al usuario, mostrar publicidad o consumir recursos mínimos del sistema.

### ¿Cómo funciona?
Suelen instalarse a través de paquetes de programas gratuitos (*bundling*), add-ons no deseados o descargas engañosas. Modifican parámetros sencillos del registro de Windows o de los navegadores web.

### Efectos típicos:
* Cambiar la página de inicio o el motor de búsqueda del navegador (Hijacker).
* Desplegar ventanas emergentes (*pop-ups*) publicitarias no solicitadas.
* Crear accesos directos innecesarios en el escritorio.
* Reproducir sonidos o mostrar mensajes informativos/broma en pantalla.

---

## 4. 10 Tipos de Virus y sus Impactos

| # | Tipo de Virus / Malware | ¿Qué daño causa en el sistema? | Nivel de Riesgo |
|---|---|---|---|
| 1 | **Ransomware** | Cifra los archivos del usuario y exige un rescate en criptomonedas para desbloquear los datos. | 🚨 Crítico |
| 2 | **Troyano (Trojan)** | Se camufla como software legítimo para abrir puertas traseras (*backdoors*) e ingresar remotamente al equipo. | 🔴 Alto |
| 3 | **Gusano (Worm)** | Se replica autónomamente por la red, saturando el ancho de banda y agotando los recursos de memoria. | 🔴 Alto |
| 4 | **Keylogger** | Graba en silencio cada tecla presionada para robar contraseñas, credenciales y números de tarjetas. | 🔴 Alto |
| 5 | **Spyware** | Monitoriza los hábitos de navegación y recopila información personal enviándola a servidores externos. | 🟡 Medio-Alto |
| 6 | **Rootkit** | Modifica el núcleo (*kernel*) del sistema operativo para ocultar la presencia de otros programas maliciosos. | 🚨 Crítico |
| 7 | **Virus de Sector de Arranque** | Corrompe el MBR o la tabla de particiones, imposibilitando el inicio correcto del sistema operativo. | 🔴 Alto |
| 8 | **Adware** | Genera anuncios publicitarios intrusivos y ralentiza la velocidad de navegación del equipo. | 🟢 Bajo |
| 9 | **Virus de Macro** | Modifica o corrompe documentos de texto y hojas de cálculo infectando la plantilla base de Office. | 🟡 Medio |
| 10 | **Cryptojacker** | Utiliza la capacidad de cómputo (CPU/GPU) para minar criptomonedas sin autorización, generando sobrecalentamiento. | 🟡 Medio-Alto |

---

## 5. Mecanismos y Tipos de Protección

Un entorno informático seguro aplica la estrategia de **Defensa en Profundidad**:

1. **Antivirus y Antimalware (EDR):**
   * *Detección por Firmas:* Compara patrones con bases de datos de amenazas conocidas.
   * *Análisis Heurístico y Conductual:* Evalúa el comportamiento de un archivo desconocido para detectar ataques *Zero-Day*.
2. **Cortafuegos (Firewall):**
   * Filtra el tráfico de red de entrada y salida, bloqueando puertos y conexiones sospechosas.
3. **Filtros Antiphishing y de Correo:**
   * Detienen adjuntos maliciosos (`.exe`, `.iso`, `.vbs`) e inspeccionan URLs fraudulentas.
4. **Parches y Actualizaciones de Seguridad:**
   * Cierran vulnerabilidades conocidas (*exploits*) en el sistema operativo y en las aplicaciones instaladas.
5. **Estrategia de Respaldos (Regla 3-2-1):**
   * Mantener 3 copias de tus datos, en 2 medios distintos y 1 fuera de línea (*off-site*) para proteger la información contra el Ransomware.

---

## 6. Cómo Analizar y Detectar Virus usando el CMD (Windows)

La consola de comandos de Windows (`CMD`) cuenta con utilidades integradas para verificar la integridad del sistema, detectar procesos anómalos o revisar conexiones no autorizadas.

> ⚠️ **Importante:** Ejecuta el Símbolo del Sistema (`CMD`) con **privilegios de Administrador**.

---

### Paso 1: Verificación de Integridad de Archivos (`SFC` y `DISM`)
Analiza si un archivo clave del sistema operativo fue modificado o corrupto por un virus:

```cmd
sfc /scannow
```
* **Función:** Examina todos los archivos protegidos del sistema y reemplaza los dañados usando una copia limpia almacenada en caché.

Si el comando reporta errores no corregibles, repara la imagen base con:
```cmd
DISM /Online /Cleanup-Image /RestoreHealth
```

---

### Paso 2: Análisis de Conexiones de Red Sospechosas (`netstat`)
Muchos virus (troyanos, keyloggers) abren sockets de comunicación con servidores remotos:

```cmd
netstat -ano | findstr ESTABLISHED
```
* **Función:** Muestra las conexiones activas.
* **Uso:** Anota el número que aparece al final de la columna derecha; este número es el **PID** (Identificador de Proceso).

---

### Paso 3: Identificar el Proceso vinculado al PID (`tasklist`)
Con el número de PID obtenido en el paso anterior, identifica la aplicación origen:

```cmd
tasklist /fi "PID eq NUMERO_DE_PID"
```
*(Ejemplo: `tasklist /fi "PID eq 3412"`)*

* **Resultado:** Mostrará el nombre de la aplicación ejecutándose (por ejemplo: `malware.exe`).

Para detener el proceso malicioso de forma inmediata:
```cmd
taskkill /F /PID NUMERO_DE_PID
```

---

### Paso 4: Revelar Archivos Ocultos por Virus en USB / Unidades (`attrib`)
Ciertos virus de USB ocultan los archivos reales del usuario y generan accesos directos infectados.

Para analizar la unidad infectada (por ejemplo la unidad `E:`):
```cmd
cd /d E:
attrib -h -r -s /s /d *.*
```
* **Explicación de modificadores:**
  * `-h`: Elimina la propiedad de oculto.
  * `-r`: Elimina la propiedad de solo lectura.
  * `-s`: Quita la propiedad de sistema.
  * `/s /d`: Aplica a todos los archivos y subcarpetas dentro del directorio.

---

### Paso 5: Escaneo Completo mediante Microsoft Defender desde el CMD
Ejecuta un escaneo nativo directo sin abrir la interfaz gráfica:

```cmd
"C:\Program Files\Windows Defender\MpCmdRun.exe" -Scan -ScanType 2
```
* **`-ScanType 2`:** Realiza un análisis exhaustivo (*Full Scan*) de todo el disco duro.

---

## 7. Contribuciones

¡Las contribuciones son bienvenidas y apreciadas! Si deseas ampliar la información, agregar más comandos o corregir alguna sección:

1. Haz un **Fork** de este repositorio.
2. Crea una rama para tus modificaciones (`git checkout -b feature/nueva-seccion`).
3. Guarda tus cambios y haz Commit (`git commit -m 'Añade información sobre...'`).
4. Sube la rama a GitHub (`git push origin feature/nueva-seccion`).
5. Abre un **Pull Request**.
