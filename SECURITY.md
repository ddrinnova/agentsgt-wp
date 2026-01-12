# 🔐 Guía de Seguridad - Archivos que NO Subir a GitHub

## ⚠️ IMPORTANTE: Antes de hacer commit

Antes de subir este proyecto a GitHub, asegúrate de que **NO** estás incluyendo archivos sensibles.

## 🚫 Archivos que NUNCA deben subirse

### 1. Archivos de Configuración con Credenciales

- ✅ **NO incluir:** `app/public/wp-config.php`
- ✅ **SÍ incluir:** `app/public/wp-config-sample.php` (ya está en el repo)

**Razón:** `wp-config.php` contiene:
- Credenciales de base de datos (usuario, contraseña)
- Keys y salts de seguridad de WordPress
- Información sensible del servidor

### 2. Bases de Datos

- ✅ **NO incluir:** `app/sql/*.sql` o cualquier archivo `.sql`
- ✅ **NO incluir:** Exports de base de datos

**Razón:** Contienen:
- Datos de usuarios (contraseñas hasheadas, pero aún sensibles)
- Contenido del sitio
- Información personal

### 3. Archivos Subidos por Usuarios

- ✅ **NO incluir:** `app/public/wp-content/uploads/`
- ✅ **NO incluir:** Cualquier archivo en la carpeta `uploads/`

**Razón:** Pueden contener:
- Imágenes con información sensible
- Documentos privados
- Archivos grandes innecesarios

### 4. Logs del Servidor

- ✅ **NO incluir:** `logs/` (cualquier archivo `.log`)
- ✅ **NO incluir:** Logs de errores, acceso, etc.

**Razón:** Pueden contener:
- Información de debugging
- Rutas del servidor
- Información del sistema

### 5. Configuraciones del Servidor Local

- ✅ **NO incluir:** `conf/**/*.hbs` (templates de configuración)
- ✅ **NO incluir:** `conf/**/*.conf` (archivos de configuración)

**Razón:** Contienen:
- Configuraciones específicas del entorno local
- Rutas absolutas del sistema
- Configuraciones de servidor

### 6. Archivos de Entorno

- ✅ **NO incluir:** `.env`, `.env.local`, `.env.*.local`
- ✅ **NO incluir:** Cualquier archivo con variables de entorno

**Razón:** Contienen:
- API keys
- Secretos de aplicación
- Credenciales de servicios externos

## ✅ Archivos SEGUROS para incluir

- ✅ Plugin personalizado: `app/public/wp-content/plugins/wordpress-plugin/`
- ✅ Temas personalizados (si los hay)
- ✅ `wp-config-sample.php` (sin credenciales)
- ✅ `README.md`
- ✅ `.gitignore`
- ✅ Archivos de documentación

## 🔍 Verificación Antes de Commit

Ejecuta estos comandos para verificar:

```bash
# Ver qué archivos se van a subir
git status

# Verificar que wp-config.php NO está incluido
git ls-files | grep wp-config.php

# Verificar que no hay archivos SQL
git ls-files | grep "\.sql$"

# Verificar que no hay logs
git ls-files | grep "\.log$"
```

## 🛠️ Si ya subiste archivos sensibles por error

1. **Elimina el archivo del historial de Git:**
   ```bash
   git rm --cached app/public/wp-config.php
   git commit -m "Remove sensitive config file"
   ```

2. **Si ya hiciste push:**
   - Considera cambiar todas las credenciales (base de datos, keys de WordPress)
   - Usa `git filter-branch` o `BFG Repo-Cleaner` para eliminar del historial
   - O crea un nuevo repositorio limpio

3. **Regenera las keys de WordPress:**
   - Ve a: https://api.wordpress.org/secret-key/1.1/salt/
   - Genera nuevas keys y actualiza `wp-config.php`

## 📝 Checklist Pre-Commit

Antes de hacer commit, verifica:

- [ ] `wp-config.php` NO está en el staging area
- [ ] No hay archivos `.sql` en el staging area
- [ ] La carpeta `uploads/` está vacía o excluida
- [ ] No hay archivos `.log` en el staging area
- [ ] No hay archivos `.env` en el staging area
- [ ] El `.gitignore` está configurado correctamente
- [ ] Has revisado `git status` antes de commit

## 🔗 Recursos

- [WordPress Security Best Practices](https://wordpress.org/support/article/hardening-wordpress/)
- [GitHub Security Best Practices](https://docs.github.com/en/code-security)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)

