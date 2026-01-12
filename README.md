<div align="center">

# 🤖 AgentSGT WordPress Site

**Sitio WordPress con integración del widget de chat AgentSGT para desarrollo local**

[![WordPress](https://img.shields.io/badge/WordPress-6.0+-21759B?style=for-the-badge&logo=wordpress&logoColor=white)](https://wordpress.org/)
[![PHP](https://img.shields.io/badge/PHP-7.4+-777BB4?style=for-the-badge&logo=php&logoColor=white)](https://www.php.net/)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)

[Características](#-características) • [Instalación](#-instalación-rápida) • [Configuración](#-configuración) • [Uso](#-uso) • [Soporte](#-soporte)

</div>

---

## 📑 Tabla de Contenidos

- [Características](#-características)
- [Requisitos del Sistema](#-requisitos-del-sistema)
- [Instalación Rápida](#-instalación-rápida)
  - [Opción 1: LocalWP (Recomendado)](#opción-1-localwp-recomendado)
  - [Opción 2: Instalación Manual](#opción-2-instalación-manual)
- [Configuración](#-configuración)
  - [Configurar WordPress](#1-configurar-wordpress)
  - [Configurar Plugin AgentSGT](#2-configurar-plugin-agentsgt)
- [Uso](#-uso)
  - [Widget Global](#widget-global)
  - [Shortcode](#shortcode)
  - [Propiedades Personalizadas](#propiedades-personalizadas)
- [Estructura del Proyecto](#-estructura-del-proyecto)
- [Desarrollo](#-desarrollo)
- [Troubleshooting](#-troubleshooting)
- [Seguridad](#-seguridad)
- [Contribuir](#-contribuir)
- [Soporte](#-soporte)
- [Licencia](#-licencia)

---

## ✨ Características

- 🚀 **Instalación rápida** con LocalWP o manual
- 🤖 **Plugin AgentSGT Widget** integrado y listo para usar
- 🎨 **Widget personalizable** con opciones de posición y apariencia
- 📱 **Shortcode** para insertar el widget en páginas específicas
- 🔧 **Configuración fácil** desde el panel de administración de WordPress
- 🔐 **Seguro** - Archivos sensibles excluidos del repositorio
- 📝 **Documentación completa** incluida

---

## 💻 Requisitos del Sistema

| Componente | Versión Mínima | Recomendada |
|------------|----------------|-------------|
| **PHP** | 7.4 | 8.0+ |
| **MySQL** | 5.7 | 8.0+ |
| **WordPress** | 6.0 | Última versión |
| **Servidor Web** | Nginx 1.18+ / Apache 2.4+ | Nginx 1.20+ |

### Herramientas Recomendadas

- **[LocalWP](https://localwp.com/)** - Entorno de desarrollo local (Recomendado)
- **Git** - Control de versiones
- **Composer** - Gestor de dependencias (opcional)

---

## 🚀 Instalación Rápida

### Opción 1: LocalWP (Recomendado) ⭐

Esta es la forma más fácil y rápida de configurar el proyecto. **LocalWP creará automáticamente la base de datos**, así que **NO necesitas un archivo .sql**.

> **💡 IMPORTANTE:** LocalWP **NO puede importar directamente desde GitHub**. Debes descargar el proyecto primero y luego copiar los archivos manualmente.

#### 📥 Paso 1: Descargar el Proyecto

Tienes dos opciones:

**Opción A: Usando Git (Recomendado)**
```bash
git clone https://github.com/ddrinnova/agentsgt-wp.git
cd agentsgt-wp
```

**Opción B: Descargar ZIP desde GitHub**
1. Ve a: https://github.com/ddrinnova/agentsgt-wp
2. Haz clic en **"Code"** → **"Download ZIP"**
3. Descomprime el archivo ZIP en tu carpeta de descargas

#### 🆕 Paso 2: Crear un Sitio Nuevo en LocalWP

**IMPORTANTE:** Primero crea un sitio nuevo en LocalWP, luego copiaremos los archivos.

1. Abre **LocalWP**
2. Haz clic en **"Add Site"** → **"Create a new site"**
3. Configura:
   - **Site name**: `agentsgt-wp` (o el nombre que prefieras)
   - **Environment**: Preferencias (recomendado: "Preferred")
   - **WordPress version**: Cualquiera (se reemplazará)
   - **PHP version**: 8.0 o superior
   - **Web server**: Nginx (recomendado)
   - **Database**: MySQL
4. Haz clic en **"Add Site"**
5. Espera a que LocalWP cree el sitio

#### 📋 Paso 3: Copiar Archivos Manualmente

Ahora necesitas copiar los archivos del proyecto descargado al sitio de LocalWP:

1. **Abre la carpeta del sitio en LocalWP:**
   - Haz clic derecho en el sitio → **"Reveal in Finder"** (Mac) o **"Open Site Shell"**
   - O navega manualmente a: `~/Local Sites/agentsgt-wp/app/public/`

2. **Copia el contenido de `wp-content`:**
   
   **Desde terminal:**
   ```bash
   # Desde la carpeta del proyecto descargado:
   cp -r app/public/wp-content/* ~/Local\ Sites/agentsgt-wp/app/public/wp-content/
   ```
   
   **O manualmente:**
   - Abre la carpeta del proyecto descargado: `agentsgt-wp/app/public/wp-content/`
   - Copia **TODO el contenido** (plugins, themes, etc.)
   - Pégalo en: `~/Local Sites/agentsgt-wp/app/public/wp-content/`
   - **Reemplaza** si te pregunta (es normal)

3. **Copia `wp-config-sample.php` y renómbralo:**
   
   **Desde terminal:**
   ```bash
   # Desde la carpeta del proyecto descargado:
   cp app/public/wp-config-sample.php ~/Local\ Sites/agentsgt-wp/app/public/wp-config.php
   ```
   
   **O manualmente:**
   - Copia `app/public/wp-config-sample.php` del proyecto descargado
   - Pégalo en `~/Local Sites/agentsgt-wp/app/public/`
   - Renómbralo a `wp-config.php`

#### ⚙️ Paso 4: Configurar wp-config.php

1. **Abre `wp-config.php`** en un editor de texto (puedes hacer clic derecho → "Open with" → tu editor)
2. **Busca las líneas de base de datos** y reemplázalas con las credenciales de LocalWP:
   ```php
   define( 'DB_NAME', 'local' );           // Siempre 'local' en LocalWP
   define( 'DB_USER', 'root' );            // Siempre 'root' en LocalWP
   define( 'DB_PASSWORD', 'root' );        // Siempre 'root' en LocalWP
   define( 'DB_HOST', 'localhost' );       // Siempre 'localhost' en LocalWP
   ```

3. **Genera nuevas keys de seguridad:**
   - Ve a: https://api.wordpress.org/secret-key/1.1/salt/
   - Copia **TODAS las keys generadas** (8 líneas completas)
   - Reemplaza las keys en `wp-config.php` (líneas 52-60 aproximadamente)
   - Debe verse así:
     ```php
     define( 'AUTH_KEY',         'tu-key-aqui...' );
     define( 'SECURE_AUTH_KEY',  'tu-key-aqui...' );
     // ... etc
     ```

#### 🚀 Paso 5: Iniciar el Sitio

1. En **LocalWP**, haz clic en **"Start"** en tu sitio
2. Espera a que el sitio esté listo (ícono verde)

#### 🌐 Paso 6: Instalar WordPress

1. Haz clic en **"Open Site"** en LocalWP o ve a `http://agentsgt-wp.local`
2. WordPress detectará que necesita instalación
3. Sigue el asistente de instalación:
   - **Idioma**: Selecciona tu idioma
   - **Título del sitio**: Elige un nombre
   - **Usuario administrador**: Crea un usuario
   - **Contraseña**: Crea una contraseña segura (guárdala)
   - **Email**: Tu email de administrador
4. Haz clic en **"Instalar WordPress"**

> **💡 Nota:** WordPress creará automáticamente la base de datos. **NO necesitas importar un archivo .sql**.

#### 🔌 Paso 7: Activar el Plugin AgentSGT

1. Una vez instalado WordPress, ve a **WordPress Admin**
2. Ve a **Plugins** → **Plugins instalados**
3. Busca **"AgentSGT Widget"**
4. Haz clic en **"Activar"**
5. Ve a **AgentSGT Widget** → **Settings** para configurar

✅ **¡Listo!** Tu sitio está funcionando con el plugin AgentSGT instalado.

---

### 🔍 Solución de Problemas Comunes en LocalWP

#### ❌ Error: "No se encuentra wp-content folder"

**Solución:**
- Asegúrate de copiar el contenido **DENTRO** de `wp-content/`, no la carpeta misma
- La estructura debe ser: `app/public/wp-content/plugins/...`
- **NO debe ser:** `app/public/wp-content/wp-content/plugins/...`

#### ❌ Error: "Necesita un archivo .sql"

**Solución:**
- **NO necesitas un archivo .sql** para empezar
- WordPress creará la base de datos automáticamente durante la instalación
- Si quieres datos de ejemplo, puedes importarlos después desde **Tools** → **Import** en WordPress Admin

#### ❌ Error: "No puedo importar desde GitHub"

**Solución:**
- LocalWP **NO puede importar directamente desde GitHub**
- Debes descargar el proyecto primero (Git o ZIP)
- Luego crear un sitio nuevo en LocalWP
- Finalmente copiar los archivos manualmente (como se explica arriba)

#### ❌ El plugin no aparece

**Solución:**
- Verifica que copiaste la carpeta `wordpress-plugin` dentro de `wp-content/plugins/`
- La ruta debe ser: `app/public/wp-content/plugins/wordpress-plugin/agentsgt-widget.php`
- Recarga la página de Plugins en WordPress Admin (F5)
- Si aún no aparece, verifica los permisos de la carpeta

---

### Opción 2: Instalación Manual

Si prefieres usar tu propio servidor web.

#### Paso 1: Clonar el Repositorio

```bash
git clone https://github.com/ddrinnova/agentsgt-wp.git
cd agentsgt-wp
```

#### Paso 2: Configurar Servidor Web

**Para Nginx:**
```nginx
server {
    listen 80;
    server_name agentsgt-wp.local;
    root /ruta/al/proyecto/app/public;
    index index.php;

    location / {
        try_files $uri $uri/ /index.php?$args;
    }

    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php8.0-fpm.sock;
        fastcgi_index index.php;
        include fastcgi_params;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }
}
```

**Para Apache:**
- Configura un VirtualHost apuntando a `app/public`
- Asegúrate de que `mod_rewrite` esté habilitado

#### Paso 3: Crear Base de Datos

```sql
CREATE DATABASE agentsgt_wp CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'wp_user'@'localhost' IDENTIFIED BY 'tu_contraseña_segura';
GRANT ALL PRIVILEGES ON agentsgt_wp.* TO 'wp_user'@'localhost';
FLUSH PRIVILEGES;
```

#### Paso 4: Configurar WordPress

1. **Copia el archivo de configuración:**
   ```bash
   cp app/public/wp-config-sample.php app/public/wp-config.php
   ```

2. **Edita `wp-config.php`:**
   ```php
   define( 'DB_NAME', 'agentsgt_wp' );
   define( 'DB_USER', 'wp_user' );
   define( 'DB_PASSWORD', 'tu_contraseña_segura' );
   define( 'DB_HOST', 'localhost' );
   ```

3. **Genera keys de seguridad** desde https://api.wordpress.org/secret-key/1.1/salt/

#### Paso 5: Instalar WordPress

1. Accede a `http://agentsgt-wp.local/wp-admin/install.php`
2. Completa el formulario de instalación
3. Activa el plugin **AgentSGT Widget**

---

## ⚙️ Configuración

### 1. Configurar WordPress

#### Configuración Básica

Después de la instalación, configura estos aspectos básicos:

1. **Permalinks:**
   - Ve a **Settings** → **Permalinks**
   - Selecciona **"Post name"** (recomendado)
   - Guarda cambios

2. **Zona Horaria:**
   - Ve a **Settings** → **General**
   - Configura tu zona horaria

3. **Idioma:**
   - Ve a **Settings** → **General**
   - Selecciona tu idioma preferido

### 2. Configurar Plugin AgentSGT

#### Configuración Inicial

1. Ve a **WordPress Admin** → **AgentSGT Widget**

2. **Configura los campos requeridos:**
   - **Runtime URL**: URL de tu backend CopilotKit
     ```
     Ejemplo: https://api.agentsgt.com/runtime
     ```
   - **API Key**: Tu clave API de AgentSGT
     ```
     Ejemplo: sk-1234567890abcdef
     ```

3. **Personaliza el widget (opcional):**
   - **Título del Widget**: Título que aparecerá en el widget
   - **Mensaje Inicial**: Mensaje de bienvenida cuando se abre el chat
   - **Posición**: Esquina inferior derecha o izquierda

4. **Activa el widget:**
   - Marca la casilla **"Habilitar widget"**
   - Haz clic en **"Guardar cambios"**

#### Configuración Avanzada

**Propiedades Personalizadas (JSON):**

Puedes agregar contexto personalizado usando JSON:

```json
{
  "siteInfo": {
    "description": "Información del sitio",
    "value": {
      "name": "Mi Sitio Web",
      "services": ["Servicio 1", "Servicio 2"],
      "contact": "info@misitio.com"
    }
  },
  "userContext": {
    "description": "Contexto del usuario",
    "value": {
      "language": "es",
      "timezone": "America/Mexico_City"
    }
  }
}
```

> **Nota:** WordPress automáticamente agrega información del sitio (nombre, URL, página actual) al contexto.

---

## 📖 Uso

### Widget Global

Una vez activado en la configuración, el widget aparecerá automáticamente en todas las páginas del sitio.

**Características:**
- ✅ Aparece en todas las páginas
- ✅ Persistente durante la navegación
- ✅ No requiere código adicional

### Shortcode

Inserta el widget en páginas o posts específicos usando el shortcode:

#### Uso Básico

```
[agentsgt_widget]
```

#### Con Parámetros Personalizados

```
[agentsgt_widget title="Mi Asistente" message="¡Hola! ¿Cómo puedo ayudarte?"]
```

#### Parámetros Disponibles

| Parámetro | Descripción | Ejemplo |
|-----------|-------------|---------|
| `title` | Título del widget | `title="Mi Asistente"` |
| `message` | Mensaje inicial | `message="Bienvenido"` |
| `position` | Posición (left/right) | `position="left"` |

**Ejemplo en un Post:**

```html
<!-- Contenido del post -->
<p>Este es el contenido de mi post.</p>

<!-- Widget de chat -->
[agentsgt_widget title="¿Necesitas ayuda?" message="Estoy aquí para ayudarte"]
```

### Propiedades Personalizadas

El plugin automáticamente detecta y envía información de WordPress:

- **Información del sitio**: Nombre, URL, descripción
- **Página actual**: Título, URL, tipo de contenido
- **Usuario**: Si está logueado, información básica

Puedes agregar propiedades adicionales desde el panel de administración.

---

## 📁 Estructura del Proyecto

```
agentsgt-wp/
│
├── 📄 README.md                 # Este archivo
├── 📄 SECURITY.md               # Guía de seguridad
├── 📄 .gitignore                # Archivos excluidos de Git
│
├── 📂 app/
│   ├── 📂 public/              # WordPress core y archivos públicos
│   │   ├── 📄 wp-config-sample.php  # Template de configuración
│   │   └── 📂 wp-content/
│   │       ├── 📂 plugins/
│   │       │   └── 📂 wordpress-plugin/  # Plugin AgentSGT
│   │       │       ├── 📄 agentsgt-widget.php
│   │       │       ├── 📂 admin/
│   │       │       └── 📄 README.md
│   │       └── 📂 themes/      # Temas de WordPress
│   └── 📂 sql/                 # Bases de datos (no en Git)
│
├── 📂 conf/                    # Configuraciones de servidor (no en Git)
│   ├── 📂 nginx/
│   ├── 📂 mysql/
│   └── 📂 php/
│
└── 📂 logs/                    # Logs del servidor (no en Git)
```

### Archivos Importantes

| Archivo | Descripción |
|---------|-------------|
| `app/public/wp-config-sample.php` | Template de configuración (✅ seguro para Git) |
| `app/public/wp-config.php` | Configuración real (❌ NO subir a Git) |
| `app/public/wp-content/plugins/wordpress-plugin/` | Plugin AgentSGT |

---

## 🛠️ Desarrollo

### Estructura del Plugin

El plugin AgentSGT se encuentra en:
```
app/public/wp-content/plugins/wordpress-plugin/
```

**Archivos principales:**
- `agentsgt-widget.php` - Archivo principal del plugin
- `admin/` - Archivos del panel de administración
  - `admin.css` - Estilos del admin
  - `admin.js` - Scripts del admin
  - `widget-styles.css` - Estilos del widget

### Desarrollo Local

1. **Habilita el modo debug:**
   ```php
   // En wp-config.php
   define( 'WP_DEBUG', true );
   define( 'WP_DEBUG_LOG', true );
   define( 'WP_DEBUG_DISPLAY', false );
   ```

2. **Revisa los logs:**
   - Logs de PHP: `logs/php/php-fpm.log`
   - Logs de WordPress: `app/public/wp-content/debug.log`

3. **Desarrollo del plugin:**
   - Edita los archivos en `app/public/wp-content/plugins/wordpress-plugin/`
   - Los cambios se reflejan inmediatamente (sin necesidad de recargar)

### Hooks Disponibles

El plugin expone estos hooks para desarrolladores:

```php
// Modificar propiedades antes de renderizar
apply_filters('agentsgt_widget_properties', $properties);

// Modificar configuración del widget
apply_filters('agentsgt_widget_config', $config);
```

---

## 🔧 Troubleshooting

### Problema: El sitio no carga

**Solución:**
1. Verifica que el servidor esté corriendo (LocalWP: botón "Start")
2. Revisa que `wp-config.php` tenga las credenciales correctas
3. Verifica los logs en `logs/nginx/error.log`

### Problema: Error de conexión a la base de datos

**Solución:**
```php
// Verifica en wp-config.php:
define( 'DB_NAME', 'nombre_correcto' );
define( 'DB_USER', 'usuario_correcto' );
define( 'DB_PASSWORD', 'contraseña_correcta' );
define( 'DB_HOST', 'localhost' );
```

### Problema: El widget no aparece

**Solución:**
1. Verifica que el plugin esté activado
2. Ve a **AgentSGT Widget** → **Settings**
3. Asegúrate de que "Habilitar widget" esté marcado
4. Verifica la consola del navegador (F12) para errores JavaScript
5. Revisa que la Runtime URL y API Key sean correctas

### Problema: Error 404 en permalinks

**Solución:**
1. Ve a **Settings** → **Permalinks**
2. Haz clic en **"Save Changes"** (sin cambiar nada)
3. Esto regenera las reglas de rewrite

### Problema: El shortcode no funciona

**Solución:**
1. Verifica que el plugin esté activado
2. Asegúrate de usar la sintaxis correcta: `[agentsgt_widget]`
3. Revisa que no haya errores de sintaxis en el editor

---

## 🔐 Seguridad

### ⚠️ Archivos que NUNCA deben subirse a Git

Por seguridad, estos archivos están excluidos del repositorio:

- ❌ `app/public/wp-config.php` - Contiene credenciales sensibles
- ❌ `app/sql/*.sql` - Bases de datos con datos reales
- ❌ `app/public/wp-content/uploads/` - Archivos subidos por usuarios
- ❌ `logs/` - Logs del servidor
- ❌ `conf/**/*.hbs` - Configuraciones del servidor local

### ✅ Archivos Seguros para Git

- ✅ `wp-config-sample.php` - Template sin credenciales
- ✅ Plugin personalizado
- ✅ Temas personalizados
- ✅ Archivos de documentación

### 🔒 Mejores Prácticas

1. **Nunca compartas credenciales** en el código
2. **Usa diferentes credenciales** en desarrollo y producción
3. **Regenera las keys** de WordPress si se comprometen
4. **Mantén WordPress actualizado** para seguridad
5. **Usa contraseñas fuertes** para la base de datos

Para más información, consulta [SECURITY.md](SECURITY.md).

---

## 🤝 Contribuir

¡Las contribuciones son bienvenidas! Sigue estos pasos:

1. **Fork el proyecto**
2. **Crea una rama** para tu feature (`git checkout -b feature/AmazingFeature`)
3. **Commit tus cambios** (`git commit -m 'Add some AmazingFeature'`)
4. **Push a la rama** (`git push origin feature/AmazingFeature`)
5. **Abre un Pull Request**

### Guía de Contribución

- Sigue las convenciones de código de WordPress
- Documenta tus cambios
- Agrega tests si es posible
- Actualiza el README si es necesario

---

## 📞 Soporte

### Documentación

- 📚 [Documentación AgentSGT](https://docs.agentsgt.com)
- 📖 [Documentación WordPress](https://wordpress.org/support/)

### Contacto

- 📧 **Email**: support@agentsgt.com
- 🐛 **Issues**: [GitHub Issues](https://github.com/tu-usuario/agentsgt-wp/issues)
- 💬 **Discusiones**: [GitHub Discussions](https://github.com/tu-usuario/agentsgt-wp/discussions)

### Reportar un Bug

Si encuentras un bug, por favor:

1. Verifica que no esté ya reportado en [Issues](https://github.com/tu-usuario/agentsgt-wp/issues)
2. Crea un nuevo issue con:
   - Descripción clara del problema
   - Pasos para reproducir
   - Versión de WordPress y PHP
   - Logs relevantes (sin información sensible)

---

## 📄 Licencia

Este proyecto está bajo la **Licencia MIT**. Ver el archivo [LICENSE](LICENSE) para más detalles.

---

<div align="center">

**Hecho con ❤️ por [DDRinnova](https://agentsgt.com)**

[⬆ Volver arriba](#-agentsgt-wordpress-site)

</div>
