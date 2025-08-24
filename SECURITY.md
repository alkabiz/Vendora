# Política de Seguridad

## 🛡️ Versiones Soportadas

Actualmente damos soporte de seguridad para las siguientes versiones de Vendora:

| Versión | Soporte de Seguridad |
| ------- | ------------------- |
| 1.0.x   | ✅ Soportada        |
| < 1.0   | ❌ No soportada     |

## 🚨 Reportar una Vulnerabilidad

La seguridad de Vendora es una prioridad para nosotros. Si descubres una vulnerabilidad de seguridad, por favor sigue estos pasos:

### 📧 Contacto Directo
**NO** reportes vulnerabilidades de seguridad a través de issues públicos de GitHub.

En su lugar, envía un email a: **security@vendora.com**

### 📋 Información a Incluir

Por favor incluye la siguiente información en tu reporte:

- **Descripción**: Explicación detallada de la vulnerabilidad
- **Tipo**: Clasificación del tipo de vulnerabilidad (ej. XSS, SQL Injection, CSRF)
- **Impacto**: Evaluación del impacto potencial
- **Pasos para reproducir**: Instrucciones paso a paso
- **Evidencia**: Screenshots, logs, o código de prueba (si aplica)
- **Versión afectada**: Versión específica de Vendora
- **Entorno**: Detalles del sistema donde se encontró

### ⏱️ Tiempo de Respuesta

Nos comprometemos a:

- **24 horas**: Confirmación de recibo del reporte
- **72 horas**: Evaluación inicial y clasificación
- **7 días**: Respuesta detallada con plan de acción
- **30 días**: Corrección para vulnerabilidades críticas
- **90 días**: Corrección para vulnerabilidades de severidad media/baja

## 🔒 Prácticas de Seguridad Implementadas

### Autenticación y Autorización
- Hash seguro de contraseñas usando `password_hash()` con `PASSWORD_ARGON2ID`
- Sistema de roles y permisos granulares
- Tokens CSRF para prevenir ataques Cross-Site Request Forgery
- Sesiones seguras con configuración apropiada
- Rate limiting para prevenir ataques de fuerza bruta

### Protección de Datos
- Validación y sanitización de todas las entradas
- Prepared statements para prevenir SQL Injection
- Escape de salida para prevenir XSS
- Headers de seguridad HTTP apropiados
- Cifrado de datos sensibles en base de datos

### Configuración Segura
- Archivos de configuración fuera del directorio web
- Variables de entorno para datos sensibles
- Configuración segura de PHP (expose_php=Off, etc.)
- Configuración apropiada del servidor web
- Logging de eventos de seguridad

### Uploads y Archivos
- Validación estricta de tipos de archivo
- Escaneado de malware en uploads
- Almacenamiento seguro de archivos subidos
- Límites de tamaño de archivo
- Nombres de archivo seguros

## 🎯 Clasificación de Severidad

### 🔴 Crítica
- Ejecución remota de código
- SQL Injection que comprometa datos
- Bypass de autenticación
- Acceso no autorizado a datos de admin

### 🟠 Alta
- XSS persistente
- CSRF en funciones sensibles
- Exposición de información sensible
- Escalación de privilegios

### 🟡 Media
- XSS reflejado
- Información disclosure limitada
- Bypass de validación
- Problemas de configuración

### 🟢 Baja
- Problemas de UI/UX que afecten seguridad
- Information leakage menor
- Configuraciones subóptimas

## 🏆 Programa de Reconocimiento

Reconocemos y agradecemos a los investigadores de seguridad responsables:

### 🎖️ Hall of Fame
<!-- Los contribuidores de seguridad serán listados aquí -->
*Próximamente...*

### 🎁 Recompensas
Para vulnerabilidades confirmadas ofrecemos:

- **Crítica**: $500 - $1000 (o equivalente)
- **Alta**: $200 - $500 (o equivalente)
- **Media**: $50 - $200 (o equivalente)
- **Baja**: Reconocimiento público

*Las recompensas están sujetas a la disponibilidad del programa y la calidad del reporte.*

## ⚡ Divulgación Responsable

Seguimos estos principios:

### Para Investigadores
- Reporta vulnerabilidades de manera responsable
- No accedas a datos que no te pertenecen
- No interrumpas servicios
- Mantén confidencialidad hasta la corrección
- Da tiempo razonable para la corrección

### Nuestro Compromiso
- Responderemos de manera oportuna
- Mantendremos comunicación durante el proceso
- Reconoceremos tu contribución públicamente (si deseas)
- No tomaremos acciones legales contra reportes de buena fe

## 📚 Recursos de Seguridad

### Para Desarrolladores
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [PHP Security Guide](https://phpsecurity.readthedocs.io/)
- [Secure Coding Practices](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

### Para Usuarios
- Usa contraseñas fuertes y únicas
- Habilita autenticación de dos factores cuando esté disponible
- Mantén tu navegador actualizado
- Ten cuidado con enlaces sospechosos
- Reporta comportamientos extraños

## 🔧 Configuración de Seguridad Recomendada

### Servidor Web
```apache
# .htaccess - Configuraciones de seguridad
<IfModule mod_headers.c>
    Header always set X-Content-Type-Options "nosniff"
    Header always set X-Frame-Options "SAMEORIGIN"
    Header always set X-XSS-Protection "1; mode=block"
    Header always set Referrer-Policy "strict-origin-when-cross-origin"
    Header always set Content-Security-Policy "default-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline'"
</IfModule>
```

### PHP
```ini
; php.ini - Configuraciones recomendadas
expose_php = Off
display_errors = Off
log_errors = On
allow_url_fopen = Off
allow_url_include = Off
session.cookie_httponly = 1
session.cookie_secure = 1
session.use_strict_mode = 1
```

### Base de Datos
- Usar usuarios con privilegios mínimos
- Conexiones cifradas (SSL/TLS)
- Auditoría de accesos habilitada
- Backups regulares y seguros

## 📞 Contacto

Para cualquier pregunta sobre seguridad:

- **Email**: security@vendora.com
- **PGP Key**: [Disponible aquí](link-to-pgp-key)
- **Response Time**: 24-48 horas

## 📜 Historial de Actualizaciones

| Fecha | Cambio |
|-------|--------|
| 2025-08-24 | Política inicial creada |

---

**Nota**: Esta política de seguridad puede ser actualizada periódicamente. Los cambios significativos serán comunicados a través de nuestros canales oficiales.