# Guía de Contribución - Vendora

¡Gracias por tu interés en contribuir a Vendora!
Esta guía te ayudará a entender cómo puedes colaborar con el proyecto.

## 🚀 Formas de Contribuir

- 🐛 Reportar bugs
- 💡 Sugerir nuevas características
- 📖 Mejorar documentación
- 🔧 Contribuir con código
- 🧪 Escribir tests
- 🎨 Mejorar el diseño UI/UX

## 📋 Requisitos Previos

Antes de contribuir, asegúrate de tener:

- PHP >= 8.1
- Composer instalado
- MySQL/MariaDB
- Git configurado
- Conocimiento básico de PSR-12

## 🔧 Configuración del Entorno de Desarrollo

1. **Fork el repositorio**
   ```bash
   # Fork desde GitHub, luego clona tu fork
   git clone https://github.com/TU_USUARIO/vendora.git
   cd vendora
   ```

2. **Configurar upstream**
   ```bash
   git remote add upstream https://github.com/usuario-original/vendora.git
   ```

3. **Instalar dependencias**
   ```bash
   composer install
   ```

4. **Configurar entorno**
   ```bash
   cp config/config.example.php config/config.php
   # Editar config.php con tus configuraciones locales
   ```

5. **Configurar base de datos de desarrollo**
   ```bash
   mysql -u root -p -e "CREATE DATABASE vendora_dev;"
   php scripts/install-database.php
   ```

## 📝 Estándares de Código

### Estilo de Código
- **Seguir PSR-12** para el estilo de código PHP
- **Usar nombres descriptivos** para variables y funciones
- **Comentar código complejo** de manera clara
- **Mantener funciones pequeñas** y enfocadas

### Ejemplo de código bien formateado:

```php
<?php

declare(strict_types=1);

namespace Vendora\Controllers;

use Vendora\Models\Product;
use Vendora\Services\ProductService;

class ProductController
{
    private ProductService $productService;

    public function __construct(ProductService $productService)
    {
        $this->productService = $productService;
    }

    /**
     * Muestra la lista de productos
     * 
     * @param array $filters Filtros de búsqueda
     * @return array Lista de productos
     */
    public function index(array $filters = []): array
    {
        // Validar filtros
        $validFilters = $this->validateFilters($filters);
        
        // Obtener productos
        return $this->productService->getProducts($validFilters);
    }
}
```

### Estructura de Commits

Usa el formato de [Conventional Commits](https://www.conventionalcommits.org/):

```
tipo(ámbito): descripción breve

Descripción más detallada si es necesaria.

Fixes #123
```

**Tipos de commit:**
- `feat`: Nueva característica
- `fix`: Corrección de bug
- `docs`: Cambios en documentación
- `style`: Cambios de formato (no afectan funcionalidad)
- `refactor`: Refactorización de código
- `test`: Agregar o modificar tests
- `chore`: Tareas de mantenimiento

**Ejemplos:**
```bash
git commit -m "feat(products): agregar filtro por categoría"
git commit -m "fix(cart): corregir cálculo de total con descuentos"
git commit -m "docs(api): actualizar documentación de endpoints"
```

## 🧪 Testing

### Ejecutar Tests
```bash
# Todos los tests
composer test

# Tests con cobertura
composer test-coverage

# Tests específicos
./vendor/bin/phpunit tests/Unit/ProductTest.php
```

### Escribir Tests

Todos los cambios deben incluir tests apropiados:

```php
<?php

namespace Vendora\Tests\Unit\Models;

use PHPUnit\Framework\TestCase;
use Vendora\Models\Product;

class ProductTest extends TestCase
{
    public function testProductCreation(): void
    {
        $product = new Product([
            'name' => 'Test Product',
            'price' => 99.99,
            'category_id' => 1
        ]);

        $this->assertEquals('Test Product', $product->getName());
        $this->assertEquals(99.99, $product->getPrice());
    }

    public function testProductValidation(): void
    {
        $this->expectException(\InvalidArgumentException::class);
        
        new Product([
            'name' => '', // Nombre vacío debe fallar
            'price' => -10 // Precio negativo debe fallar
        ]);
    }
}
```

## 🔍 Code Review

### Verificaciones Automáticas
Antes de enviar tu PR, ejecuta:

```bash
# Verificar estilo de código
composer cs-check

# Análisis estático
composer stan

# Ejecutar todos los tests
composer test

# O todo junto
composer quality
```

### Lista de Verificación para PRs

- [ ] El código sigue PSR-12
- [ ] Todos los tests pasan
- [ ] Se agregaron tests para nuevas funcionalidades
- [ ] La documentación está actualizada
- [ ] No hay código comentado o debug
- [ ] Variables y funciones tienen nombres descriptivos
- [ ] Se manejaron casos edge y errores

## 🐛 Reportar Bugs

### Antes de reportar:
1. Busca en issues existentes
2. Reproduce el bug en la última versión
3. Verifica que no sea un problema de configuración

### Template de Bug Report:

```markdown
## 🐛 Descripción del Bug
Descripción clara del problema

## 🔄 Pasos para Reproducir
1. Ir a '...'
2. Hacer clic en '...'
3. Ver error

## ✅ Comportamiento Esperado
Qué debería haber pasado

## ❌ Comportamiento Actual
Qué pasó realmente

## 🖼️ Screenshots
Si aplica

## 🌐 Entorno
- OS: [ej. Ubuntu 22.04]
- PHP: [ej. 8.1.2]
- MySQL: [ej. 8.0.32]
- Navegador: [ej. Chrome 108]

## 📝 Información Adicional
Contexto adicional sobre el problema
```

## 💡 Sugerir Características

### Template de Feature Request:

```markdown
## 🚀 Descripción de la Característica
Descripción clara de la nueva funcionalidad

## 🎯 Problema que Resuelve
¿Qué problema específico resuelve?

## 💡 Solución Propuesta
Cómo visualizas que funcione

## 🔄 Alternativas Consideradas
Otras formas de resolver el problema

## 📋 Criterios de Aceptación
- [ ] Criterio 1
- [ ] Criterio 2
- [ ] Criterio 3

## 🖼️ Mockups/Wireframes
Si aplica
```

## 🔄 Proceso de Pull Request

1. **Crear rama feature**
   ```bash
   git checkout -b feature/nombre-descriptivo
   ```

2. **Hacer cambios y commits**
   ```bash
   git add .
   git commit -m "feat: descripción del cambio"
   ```

3. **Mantener actualizada la rama**
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

4. **Push y crear PR**
   ```bash
   git push origin feature/nombre-descriptivo
   ```

5. **Completar template de PR**

### Template de Pull Request:

```markdown
## 📝 Descripción
Describe los cambios realizados

## 🔄 Tipo de Cambio
- [ ] Bug fix
- [ ] Nueva característica
- [ ] Breaking change
- [ ] Documentación

## 🧪 Testing
- [ ] Tests existentes pasan
- [ ] Agregué tests para mis cambios
- [ ] Tests locales pasan

## 📋 Checklist
- [ ] Código sigue PSR-12
- [ ] Self-review del código
- [ ] Comenté código complejo
- [ ] Actualicé documentación
- [ ] Sin warnings o errors

## 🔗 Issues Relacionados
Fixes #123
```

## 📚 Recursos Adicionales

- [Documentación PHP](https://www.php.net/docs.php)
- [PSR Standards](https://www.php-fig.org/psr/)
- [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/)
- [Conventional Commits](https://www.conventionalcommits.org/)

## 🤝 Código de Conducta

- Se respetuoso y profesional
- Acepta feedback constructivo
- Ayuda a otros contribuidores
- Mantén discusiones enfocadas en el tema

## 🙋 ¿Necesitas Ayuda?

- 💬 Abre un [Discussion](https://github.com/usuario/vendora/discussions)
- 📧 Envía email a dev@vendora.com
- 💬 Únete a nuestro [Discord](https://discord.gg/AG8euD8y)

¡Gracias por contribuir a Vendora! 🚀