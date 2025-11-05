Sistema de Registro de Empleados **Descripción** Este
repositorio contiene una aplicación de escritorio en Python
(Tkinter) para gestionar empleados, con conexión a MySQL,
exportación a CSV y visualización de un GIF. Está pensada
para uso local y pruebas. Si la corres en un servidor
jodidamente público, estás pidiendo problemas. ---
#Características principales - Interfaz gráfica con Tkinter y ttk
(tema oscuro). - Conexión a MySQL (mysql-connector). -
CRUD básico: listar, agregar y eliminar empleados. - Exportar
empleados a CSV. - Ventana emergente que reproduce un
GIF. - Manejo simple de reconexión a la base de datos y
mensajes de error. --- #Requisitos - Python 3.8+ - Paquetes
Python: - mysql-connector-python - pillow - reportlab (solo
para exportar PDF desde este README, no necesario para la
app) - MySQL en local o accesible desde la máquina.
Instalación rápida (usa pip):
```
pip install mysql-connector-python pillow reportlab
```
---
## Estructura del proyecto
- `main.py` (o el archivo con el código): contiene el modelo (EmpleadoModel) y la vista/controlador (App).
- `bp_image.jpg`: imagen de fondo (ruta absoluta en el código por defecto).
- `saludo_animado.gif`: GIF mostrado en la ventana emergente.
- `empleados_exportados_ilegalmente.csv`: nombre por defecto al exportar (broma).
- Carpeta configurada por defecto (modificable):
`C:\\Users\\pc1\\OneDrive\\Escritorio\\rpg\\trabajo`
> Nota: El código actualmente fuerza `base_dir` a la ruta anterior. Cambia `self.base_dir` en
`App.__init__` para usar tu propia carpeta.
---
## Configuración de la base de datos
Crea la base de datos y la tabla con este esquema SQL (ejemplo mínimo):
```sql
CREATE DATABASE IF NOT EXISTS empresa_db;
USE empresa_db;
CREATE TABLE IF NOT EXISTS empleados (
id INT AUTO_INCREMENT PRIMARY KEY,
nombre VARCHAR(255) NOT NULL,
sexo VARCHAR(20),
correo VARCHAR(255)
);
```
En `App.__init__` asegúrate de ajustar `db_config`:
```python
db_config = {
"host": "127.0.0.1",
"user": "root",
"password": "toor", # cambia esto, no dejes contraseñas por defecto
"database": "empresa_db"
}
```
---
## Uso
1. Ajusta `self.base_dir` en `App.__init__` o coloca `bp_image.jpg` y `saludo_animado.gif` en esa carpeta.
2. Asegúrate de que MySQL esté corriendo y la base de datos creada.
3. Ejecuta:
```
python main.py
```
4. En "Nuevo Registro" puedes añadir empleados.
5. En "Gestión de Empleados" puedes listar, eliminar y exportar a CSV.
---
## Consideraciones de seguridad
- El código usa consultas parametrizadas para evitar inyección SQL al insertar y borrar, lo cual está bien.
- No expongas la base de datos ni archivos sensibles; el botón "Hackear Base de Datos" es solo una
broma que exporta a CSV. Si lo pones público, eres un idiota por hacerlo sin seguridad.
- Cambia contraseñas, usa variables de entorno o un archivo de configuración fuera del repositorio.
---
## Personalización rápida
- Para cambiar la carpeta de recursos, edita `self.base_dir`.
- Para redimensionar la ventana por defecto, cambia `self.ancho_ventana` y `self.alto_ventana`.
- Para modificar estilos, revisa `_crear_estilos_ttk()`.
---
## Resolución de problemas comunes
- **Error al cargar imagen**: verifica que `bp_image.jpg` exista en `base_dir` y que el nombre sea
EXACTO (mayúsculas/minúsculas).
- **No se conecta a MySQL**: revisa `host`, `user`, `password`, que el servidor esté activo y que el usuario
tenga permisos.
- **GIF no carga**: confirma `saludo_animado.gif` y que Pillow esté instalado.
---
## Licencia
Código para uso personal/educativo. Si lo vas a usar en producción, revisa licencias y seguridad.
---
## Autor
Desarrollador: Eduardo (usuario) 
