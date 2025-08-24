# Vendora 🛒

Una moderna plataforma de e-commerce desarrollada con PHP y MySQL/MariaDB, diseñada para ofrecer una experiencia de compra fluida y una gestión administrativa completa.

## 🚀 Características

### Para Clientes
- ✅ Catálogo de productos con búsqueda y filtros
- ✅ Carrito de compras persistente
- ✅ Sistema de registro y autenticación de usuarios
- ✅ Gestión de perfiles de usuario
- ✅ Historial de pedidos
- ✅ Sistema de reseñas y valoraciones
- ✅ Múltiples métodos de pago
- ✅ Seguimiento de envíos

### Para Administradores
- ✅ Panel de administración completo
- ✅ Gestión de productos (CRUD)
- ✅ Gestión de categorías
- ✅ Gestión de pedidos
- ✅ Gestión de usuarios
- ✅ Reportes de ventas
- ✅ Control de inventario
- ✅ Configuración de métodos de pago

## 🛠️ Tecnologías

- **Backend**: PHP 8.1+
- **Base de Datos**: MySQL 8.0+ / MariaDB 10.6+
- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Framework CSS**: Bootstrap 5
- **Servidor Web**: Apache/Nginx
- **Gestión de Dependencias**: Composer

## 📋 Requisitos del Sistema

- PHP >= 8.1
- MySQL >= 8.0 o MariaDB >= 10.6
- Apache/Nginx con mod_rewrite habilitado
- Composer
- Extensiones PHP requeridas:
  - PDO
  - PDO_MySQL
  - mbstring
  - openssl
  - json
  - curl

## ⚡ Instalación Rápida

1. **Clonar el repositorio**
   ```bash
   git clone https://github.com/tuusuario/vendora.git
   cd vendora
   ```

2. **Instalar dependencias**
   ```bash
   composer install
   ```

3. **Configurar base de datos**
   ```bash
   # Copiar archivo de configuración
   cp config/config.example.php config/config.php
   
   # Editar config.php con tus credenciales de base de datos
   ```

4. **Importar base de datos**
   ```bash
   mysql -u usuario -p nombre_base_datos < database/vendora.sql
   ```

5. **Configurar permisos**
   ```bash
   chmod 755 uploads/
   chmod 644 config/config.php
   ```

6. **Acceder a la aplicación**
   - Tienda: `http://localhost/vendora`
   - Panel Admin: `http://localhost/vendora/admin`
   - Usuario admin por defecto: `admin@vendora.com` / `admin123`

## 📁 Estructura del Proyecto

```
vendora/
├── admin/                  # Panel de administración
│   ├── dashboard.php
│   ├── products/
│   ├── orders/
│   └── users/
├── assets/                 # Recursos estáticos
│   ├── css/
│   ├── js/
│   └── images/
├── config/                 # Archivos de configuración
│   ├── config.php
│   └── database.php
├── database/              # Scripts de base de datos
│   ├── vendora.sql
│   └── migrations/
├── includes/              # Archivos PHP incluibles
│   ├── header.php
│   ├── footer.php
│   └── functions.php
├── src/                   # Clases principales
│   ├── Controllers/
│   ├── Models/
│   └── Services/
├── templates/             # Plantillas
├── uploads/               # Archivos subidos
├── vendor/                # Dependencias de Composer
├── index.php             # Página principal
├── cart.php              # Carrito de compras
├── checkout.php          # Proceso de compra
└── README.md
```

## 🔧 Configuración

### Base de Datos
1. Crear una base de datos MySQL/MariaDB
2. Importar el archivo `database/vendora.sql`
3. Configurar credenciales en `config/config.php`

### Variables de Entorno
Edita `config/config.php` con tus configuraciones:

```php
// Configuración de base de datos
define('DB_HOST', 'localhost');
define('DB_NAME', 'vendora_db');
define('DB_USER', 'tu_usuario');
define('DB_PASS', 'tu_password');

// Configuración de la aplicación
define('SITE_URL', 'http://localhost/vendora');
define('SITE_NAME', 'Vendora');
```

## 🧪 Testing

```bash
# Ejecutar tests unitarios
./vendor/bin/phpunit tests/

# Verificar estilo de código
./vendor/bin/phpcs --standard=PSR-12 src/
```

## 📖 API Documentation

La documentación de la API REST está disponible en `/docs/api.md` una vez que la aplicación esté en funcionamiento.

## 🤝 Contribuir

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

### Estándares de Código
- Seguir PSR-12 para el estilo de código PHP
- Comentar el código de manera clara
- Escribir tests para nuevas funcionalidades

## 🐛 Reportar Bugs

Si encuentras un bug, por favor [abre un issue](https://github.com/tuusuario/vendora/issues) con:
- Descripción del problema
- Pasos para reproducirlo
- Comportamiento esperado vs actual
- Screenshots si aplica

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Ver el archivo [LICENSE](LICENSE) para más detalles.

## 👥 Autores

- **Tu Nombre** - *Desarrollador Principal* - [@tuusuario](https://github.com/tuusuario)

## 🙏 Agradecimientos

- Bootstrap team por el excelente framework CSS
- Comunidad PHP por las mejores prácticas
- Contribuidores del proyecto

## 📞 Soporte

- 📧 Email: support@vendora.com
- 💬 Discord: [Servidor de Vendora](link-discord)
- 📖 Wiki: [Documentación completa](https://github.com/tuusuario/vendora/wiki)

---

⭐ Si este proyecto te ayuda, ¡dale una estrella en GitHub!

**Vendora** - *Construyendo el futuro del e-commerce*
