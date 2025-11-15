# Instrucciones para Subir el Proyecto Joyería a GitHub

## Problema
GitHub muestra el error: "Yowza, that's a lot of files. Try uploading fewer than 100 at a time."

## Solución

El archivo `.gitignore` que se ha añadido ayudará, pero debes seguir estos pasos para subir correctamente tu proyecto:

### Opción 1: Usar Git desde la Línea de Comandos (RECOMENDADO)

1. **Clona este repositorio en tu máquina local:**
   ```bash
   git clone https://github.com/Didiu92/Joyeria.git
   cd Joyeria
   ```

2. **Cambia a la rama main:**
   ```bash
   git checkout main
   git pull origin copilot/fix-git-upload-issue
   ```

3. **Copia tus archivos del proyecto a esta carpeta** (excepto las carpetas que ya están en `.gitignore`)

4. **Verifica qué archivos se van a subir:**
   ```bash
   git status
   ```
   
   **IMPORTANTE:** NO debes ver estas carpetas/archivos en la lista:
   - `vendor/`
   - `node_modules/`
   - `.idea/`
   - `.vscode/`
   - `composer.lock`
   - Archivos `.log`

5. **Si ves carpetas que no deberían estar, elimínalas antes de continuar:**
   ```bash
   rm -rf vendor/
   rm -rf node_modules/
   rm -rf .idea/
   ```

6. **Añade los archivos en pequeños lotes:**
   ```bash
   git add *.php
   git commit -m "Añadir archivos PHP principales"
   git push origin main
   
   git add css/
   git commit -m "Añadir archivos CSS"
   git push origin main
   
   git add js/
   git commit -m "Añadir archivos JavaScript"
   git push origin main
   ```

### Opción 2: Si Ya Tienes Archivos Localmente con Git

1. **Asegúrate de tener el archivo `.gitignore` en tu proyecto local:**
   - Descarga el archivo `.gitignore` de esta rama
   - Cópialo a la raíz de tu proyecto

2. **Limpia el caché de Git para que respete el `.gitignore`:**
   ```bash
   git rm -r --cached .
   git add .
   ```

3. **Verifica que solo se añadan los archivos necesarios:**
   ```bash
   git status
   ```

4. **Haz commit y push en lotes pequeños si hay muchos archivos:**
   ```bash
   git commit -m "Actualizar archivos del proyecto"
   git push origin main
   ```

### Archivos que NO Deben Subirse

El `.gitignore` excluye automáticamente:
- ✅ `vendor/` - dependencias de Composer
- ✅ `node_modules/` - dependencias de NPM
- ✅ `.env` - archivo de configuración con contraseñas
- ✅ `.idea/`, `.vscode/` - configuración de IDEs
- ✅ `*.log` - archivos de registro
- ✅ `.DS_Store` - archivos del sistema Mac
- ✅ Archivos de caché y temporales

### Archivos que SÍ Deben Subirse

- ✅ Archivos `.php` de tu aplicación
- ✅ Archivos `.html`, `.css`, `.js`
- ✅ `composer.json` (pero NO `composer.lock`)
- ✅ Imágenes y recursos (en carpetas como `img/`, `images/`)
- ✅ Documentación y README

## ¿Necesitas Ayuda?

Si sigues teniendo problemas:
1. Verifica que NO estés subiendo carpetas `vendor/` o `node_modules/`
2. Cuenta cuántos archivos tienes: `find . -type f | wc -l`
3. Si tienes más de 100 archivos, súbelos en lotes usando múltiples commits

## Después de Subir

Una vez subido el proyecto, otros desarrolladores pueden descargarlo y ejecutar:
```bash
composer install  # Para instalar dependencias PHP
npm install       # Para instalar dependencias JavaScript (si las hay)
```
