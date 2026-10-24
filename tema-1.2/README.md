# Actividad 1 Tabla completa
 
| Recurso | Dónde verlo | Mi equipo |
|---|---|---|
| Memoria RAM | Rendimiento > Memoria | 16 GB LPDDR4 instalados (13.9 GB utilizables, 2.1 GB reservados para hardware) |
| Espacio libre en disco | Explorador > Este equipo | 36.9 GB libres de 474 GB (disco C:, SSD NVMe) |
| Procesador | Rendimiento > CPU | AMD Ryzen 7 7730U, 8 núcleos, 16 procesadores lógicos |
| Virtualización | Rendimiento > CPU > Virtualización | Habilitada |
| Permisos de administrador | ¿Puedo instalar programas? | Sí, mi cuenta es Administrador |
 

 # Actividad 1 Análisis de mi equipo
 
Mi equipo tiene un procesador AMD Ryzen 7 7730U de 8 núcleos, 16 GB de RAM (13.9 GB utilizables), un SSD NVMe con 36.9 GB libres, la virtualización habilitada y una cuenta de administrador.
 
Es apto sin problemas para un entorno ligero (consola Dart y Chrome) y también para el nivel medio con un celular físico.
 
El emulador Android es técnicamente posible porque cumple los 16 GB y la virtualización, pero queda justo: la memoria ya está en uso en un 83% con pocas aplicaciones abiertas y el espacio libre en disco es limitado, así que podría volver lento el equipo.
 
Por eso trabajaré principalmente con la consola y Chrome.
 

 # Actividad 2 Doctor
 
En mi `doctor.txt` no aparece ninguna X.
 
En la primera ejecución apareció un solo `!` que ya se soluciono,  en la categoría Flutter: avisaba de que `flutter` y `dart` del PATH apuntaban a mi instalación anterior (`C:\flutter`) y no al SDK portable (`C:\dev\flutter`). No es una falla del entorno portable, sino de tener una instalación global previa.
 
Android toolchain y Visual Studio aparecen en verde porque ya los tenía instalados de antes.
 
Para este curso solo necesito realmente Flutter y Chrome, porque trabajaré con la consola y el navegador. El Android toolchain solo haría falta para celular o emulador, y Visual Studio para apps de escritorio Windows.

# Actividad 3 - Que hace %~dp0 y porque el cambio en el PATH es temporal

`%~dp0` devuelve la unidad y la carpeta donde está guardado el script, con la barra final (por ejemplo `C:\dev\`). Así el script funciona aunque se copie a otra carpeta o a una USB que reciba otra letra de unidad.

El cambio en el PATH es temporal porque el comando `set` solo modifica las variables de entorno de esa ventana y de los programas que se abren desde ella, como VS Code. No escribe nada en el registro de Windows, así que al cerrar la ventana el equipo queda como estaba.

En mi equipo existe además una instalación global previa en `C:\flutter`, por lo que para demostrar que Flutter no se reconoce sin el script quité las entradas de Flutter del PATH solo de esa sesión.


# Actividad 4A Launch explicacion
Sin launch.json, VS Code ejecutó el programa en la Consola de depuración, que solo muestra texto y no permite escribir datos. Por eso stdin.readLineSync() se quedó esperando una entrada que nunca llegó. Con "console": "terminal", el programa se ejecuta en la terminal integrada, que sí acepta el teclado, y por eso pude escribir mi nombre. Además, "program": "${file}" hace que se ejecute el archivo que tengo abierto en lugar de buscar siempre main.dart.


# Actividad 4B Dispositivos conectados
 
```text
Found 3 connected devices:
  Windows (desktop) • windows • windows-x64    • Microsoft Windows [Versión 10.0.26200.9711]
  Chrome (web)      • chrome  • web-javascript • Google Chrome 154.0.8037.98
  Edge (web)        • edge    • web-javascript • Microsoft Edge 155.0.4283.62
```


# Actividad 5 Clinica de errores hecho con Liz Llinin
 
| Caso | Situación | Causa | Solución exacta |
|---|---|---|---|
| 1 | Ana agregó `C:\dev\flutter` al PATH y `flutter` no se reconoce | Falta `\bin` en la ruta: el ejecutable está en `flutter\bin`, no en `flutter` | Agregar `C:\dev\flutter\bin` al PATH y abrir una terminal nueva |
| 2 | Luis cambió el PATH, pero VS Code dice “Could not find a Flutter SDK” | VS Code ya estaba abierto y no leyó el PATH nuevo | Cerrar y volver a abrir VS Code, o usar el comando `Flutter: Change SDK` |
| 3 | El programa de María pide un dato con `stdin.readLineSync()` y se queda detenido | La ejecución va a la Consola de depuración, que no acepta entrada | Poner `"console": "terminal"` en `launch.json` |
| 4 | Pedro abre `ejercicio3.dart`, presiona F5 y se ejecuta `main.dart` | El `launch.json` apunta fijo a `main.dart` | Poner `"program": "${file}"` para ejecutar el archivo abierto |
| 5 | El SDK de Carla está en `C:\Users\Carla\OneDrive\Mis cosas\flutter` y da errores raros | La ruta tiene espacios y está en una carpeta sincronizada con OneDrive | Mover el SDK a `C:\dev\flutter` y actualizar el PATH |
| 6 | En una laptop de 8 GB, el emulador tarda minutos y congela el equipo | El emulador consume más recursos de los que tiene el equipo | Usar Chrome como destino o un celular físico por USB |


# Actividad 6 - Mi entorno

- **Flutter:** 3.47.8 (canal stable)
- **Dart:** 3.13.7
- **Ruta del entorno:** `C:\dev` (SDK en `C:\dev\flutter`, VS Code portable en `C:\dev\vscode`)
- **Destinos que puedo usar:** consola Dart, Chrome, Edge y escritorio Windows (los tres aparecen en `flutter devices`); también Android, porque mi equipo tiene el SDK instalado.

# Problema resuelto durante la práctica

El `iniciar.bat` de la guía mostraba la versión de Flutter pero no abría VS Code. La causa es que `flutter` es un archivo `.bat`, y en un script de lotes, llamar a otro `.bat` sin `call` termina el script original sin ejecutar las líneas siguientes. Lo resolví cambiando `flutter --version` por `call flutter --version`.


# Actividad 7 - Preguntas 
| # | Respuesta |
|---|---|
| 1 | b) `flutter\bin` |
| 2 | c) Crear la carpeta `data` junto a `Code.exe` |
| 3 | b) Chrome |
| 4 | c) Falta el SDK de Android, necesario solo para celular o emulador |
| 5 | b) Permitir la entrada de datos con `stdin` |
| 6 | c) `PUB_CACHE` |
| 7 | b) `pubspec.lock` |
| 8 | a) FVM |
 