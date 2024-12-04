# Instalación de Docker y Ejecución de Docker Compose en macOS

Este archivo describe cómo instalar Docker en macOS y cómo usar Docker Compose para ejecutar un archivo `docker-compose.yml`.

## Requisitos Previos

- macOS 10.15 (Catalina) o superior.
- Acceso de administrador para instalar aplicaciones.

---

## Paso 1: Instalar Docker para Mac

1. **Descargar Docker Desktop**:
   - Ve al sitio oficial de Docker: [Docker Desktop para Mac](https://www.docker.com/products/docker-desktop).
   - Descarga la versión para macOS.

2. **Instalar Docker Desktop**:
   - Abre el archivo `.dmg` descargado.
   - Arrastra el ícono de Docker a la carpeta `Aplicaciones`.

3. **Abrir Docker Desktop**:
   - Ve a `Aplicaciones` y abre `Docker`.
   - Sigue las instrucciones para completar la configuración inicial.

4. **Verificar la instalación**:
   - Abre una terminal y ejecuta:

     ```bash
     docker --version
     ```

     Debes ver un mensaje similar a:

     ```
     Docker version 24.0.5, build abcdef1
     ```

5. **Habilitar Docker Compose**:
   - Docker Desktop incluye Docker Compose. Verifica su instalación ejecutando:

     ```bash
     docker-compose --version
     ```

     Debes ver algo como:

     ```
     Docker Compose version v2.12.2
     ```

---

## Paso 2: Configurar y Ejecutar el Proyecto con Docker Compose

1. **Clonar o Crear el Proyecto**:
   - Clona el repositorio que contiene el archivo `docker-compose.yml` o crea uno.

     ```bash
     git clone <URL_DEL_REPOSITORIO>
     cd <NOMBRE_DEL_PROYECTO>
     ```

2. **Asegurarte de que el archivo `docker-compose.yml` está presente**:
   - Lista los archivos del directorio actual y confirma que `docker-compose.yml` esté ahí:

     ```bash
     ls
     ```

3. **Ejecutar Docker Compose**:
   - Levanta los servicios definidos en el archivo `docker-compose.yml`:

     ```bash
     docker-compose up -d
     ```

   - Este comando:
     - Descargará las imágenes necesarias si no están disponibles localmente.
     - Creará y levantará los contenedores.

4. **Verificar los contenedores en ejecución**:
   - Usa el siguiente comando para verificar que los contenedores están activos:

     ```bash
     docker ps
     ```

---

## Paso 3: Acceder a los Servicios

- Accede a los servicios expuestos en los puertos definidos en el archivo `docker-compose.yml`. Por ejemplo:
  - WordPress: `http://localhost:8000`
  - phpMyAdmin: `http://localhost:8080`
  - Mailhog: `http://localhost:8025`

---

## Paso 4: Detener y Eliminar los Contenedores

1. **Detener los contenedores**:
   - Usa el comando:

     ```bash
     docker-compose down
     ```

   - Esto detendrá y eliminará los contenedores, pero mantendrá los volúmenes.

2. **Eliminar volúmenes (opcional)**:
   - Si también deseas eliminar los datos almacenados en los volúmenes:

     ```bash
     docker-compose down -v
     ```

---

## Solución de Problemas

1. **Error: `command not found: docker`**:
   - Asegúrate de que Docker Desktop está instalado y en ejecución.

2. **Error: `permission denied`**:
   - Asegúrate de ejecutar los comandos con un usuario que tenga privilegios administrativos.

3. **Puertos en uso**:
   - Si otro servicio está usando el puerto necesario, modifica el archivo `docker-compose.yml` para usar un puerto diferente.

---

## Referencias

- [Documentación oficial de Docker](https://docs.docker.com/)
- [Documentación de Docker Compose](https://docs.docker.com/compose/)
