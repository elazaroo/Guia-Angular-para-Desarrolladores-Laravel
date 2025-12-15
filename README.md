# 📘 Guía Angular para Desarrolladores Laravel / Angular Guide for Laravel Developers

**🌐 Language / Idioma:** [🇪🇸 Español](#español) | [🇬🇧 English](#english)

---

<a id="español"></a>
## 🇪🇸 Versión en Español

[→ Switch to English](#english)

### 🔄 Comparativa Rápida: Laravel vs Angular

| Laravel (Backend) | Angular (Frontend) |
|-------------------|-------------------|
| `php artisan serve` | `npm run start` |
| Blade templates (`.blade.php`) | Templates Angular (`.html`) |
| Controladores | Componentes |
| `{{ $variable }}` | `{{ variable }}` |
| `@if`, `@foreach` | `*ngIf`, `*ngFor` |
| Modelos Eloquent | Interfaces TypeScript |
| `composer.json` | `package.json` |
| `vendor/` | `node_modules/` |

---

### 🚀 Crear un Proyecto Angular

#### En Laravel:
```bash
composer create-project laravel/laravel mi-proyecto
```

#### En Angular:
```bash
npx @angular/cli new mi-proyecto
# o si tienes Angular CLI instalado globalmente:
ng new mi-proyecto
```

---

### 📁 Estructura del Proyecto

#### Laravel tendría:
```
app/
├── Http/Controllers/    # Lógica
├── Models/              # Modelos de datos
resources/
├── views/               # Vistas Blade
public/
├── css/
├── js/
```

#### Angular tiene:
```
src/
├── app/
│   ├── models/          # Interfaces (como Modelos)
│   ├── app.ts           # Componente principal (como un Controller)
│   ├── app.html         # Template (como una vista Blade)
│   └── app.css          # Estilos del componente
├── index.html           # Punto de entrada
└── styles.css           # Estilos globales
```

---

### 🧩 ¿Qué es un Componente?

**En Laravel** tienes Controladores + Vistas Blade.
**En Angular** tienes **Componentes** = Lógica + Vista + Estilos, todo junto.

```
┌─────────────────────────────────┐
│         COMPONENTE              │
├─────────────────────────────────┤
│  app.ts     → Lógica (TS)       │  ← Como un Controller
│  app.html   → Vista (HTML)      │  ← Como una vista Blade
│  app.css    → Estilos (CSS)     │  ← Estilos específicos
└─────────────────────────────────┘
```

---

### 📝 Sintaxis: Blade vs Angular Templates

#### Variables

**Blade (Laravel):**
```blade
<p>Hola {{ $nombre }}</p>
```

**Angular:**
```html
<p>Hola {{ nombre }}</p>
```
> ¡Casi igual! Solo que en Angular no usamos `$`.

---

#### Condicionales

**Blade (Laravel):**
```blade
@if($mostrar)
    <p>Visible</p>
@endif
```

**Angular:**
```html
<p *ngIf="mostrar">Visible</p>
```
> El `*ngIf` se pone como atributo del elemento.

---

#### Bucles

**Blade (Laravel):**
```blade
@foreach($usuarios as $usuario)
    <li>{{ $usuario->nombre }}</li>
@endforeach
```

**Angular:**
```html
<li *ngFor="let usuario of usuarios">{{ usuario.nombre }}</li>
```

---

#### Formularios (Two-Way Binding)

**Blade + JS (Laravel):**
```blade
<input type="text" id="nombre" value="{{ old('nombre') }}">
<script>
    document.getElementById('nombre').addEventListener('input', function(e) {
        // Actualizar variable manualmente
    });
</script>
```

**Angular (automático):**
```html
<input type="text" [(ngModel)]="nombre">
```
> `[(ngModel)]` sincroniza automáticamente el input con la variable.
> ¡Sin necesidad de JavaScript adicional!

---

#### Eventos (Click)

**Blade + JS:**
```blade
<button onclick="enviarDatos()">Enviar</button>
<script>
    function enviarDatos() {
        // lógica
    }
</script>
```

**Angular:**
```html
<button (click)="enviarDatos()">Enviar</button>
```
```typescript
// En el componente .ts
enviarDatos() {
    // lógica
}
```

---

#### Deshabilitar Elementos

**Blade + JS:**
```blade
<button id="btn" disabled>Enviar</button>
<script>
    if (formularioValido) {
        document.getElementById('btn').removeAttribute('disabled');
    }
</script>
```

**Angular (reactivo):**
```html
<button [disabled]="!formularioValido">Enviar</button>
```
> Se actualiza automáticamente cuando cambia `formularioValido`.

---

### 📦 Modelos: Eloquent vs Interfaces TypeScript

#### En Laravel usas Modelos Eloquent:
```php
// app/Models/Configuracion.php
class Configuracion extends Model {
    protected $fillable = ['nombre', 'apellido', 'rango', 'intentos'];
}
```

#### En Angular usas Interfaces TypeScript:
```typescript
// src/app/models/configuracion.ts
export interface Configuracion {
    nombre: string;
    apellido: string;
    rangoMaximo: number;
    intentos: number;
}
```

> La diferencia: Eloquent conecta con la BD. Las interfaces de Angular solo definen la "forma" de los datos en el frontend.

---

### ⚡ Getters: Propiedades Calculadas

#### En Laravel (Modelo):
```php
class Usuario extends Model {
    public function getNombreCompletoAttribute() {
        return $this->nombre . ' ' . $this->apellido;
    }
}
// Uso: $usuario->nombre_completo
```

#### En Angular (Componente):
```typescript
export class App {
    nombre = 'Juan';
    apellido = 'García';
    
    get nombreCompleto(): string {
        return this.nombre + ' ' + this.apellido;
    }
}
```
```html
<!-- Uso en template -->
<p>{{ nombreCompleto }}</p>
```

---

### 🔧 Comandos Útiles

| Acción | Laravel | Angular |
|--------|---------|---------|
| Iniciar servidor | `php artisan serve` | `npm run start` |
| Instalar dependencias | `composer install` | `npm install` |
| Crear proyecto | `composer create-project laravel/laravel` | `ng new` |
| Generar componente | `php artisan make:controller` | `ng generate component` |

---

### 💡 Tips Finales

1. **Angular es SPA**: No se recarga la página, todo se actualiza dinámicamente (a diferencia de Laravel donde cada ruta recarga).

2. **TypeScript**: Es JavaScript con tipos. Si defines `nombre: string`, TypeScript te avisa si intentas asignar un número.

3. **Reactividad automática**: Cuando cambias una variable, la vista se actualiza sola. No necesitas manipular el DOM.

4. **Componentes reutilizables**: Puedes crear componentes pequeños (como un botón o un formulario) y usarlos en múltiples lugares.

---

[⬆️ Volver arriba](#-guía-angular-para-desarrolladores-laravel--angular-guide-for-laravel-developers) | [→ Switch to English](#english)

---
---
---

<a id="english"></a>
## 🇬🇧 English Version

[→ Cambiar a Español](#español)

### 🔄 Quick Comparison: Laravel vs Angular

| Laravel (Backend) | Angular (Frontend) |
|-------------------|-------------------|
| `php artisan serve` | `npm run start` |
| Blade templates (`.blade.php`) | Angular Templates (`.html`) |
| Controllers | Components |
| `{{ $variable }}` | `{{ variable }}` |
| `@if`, `@foreach` | `*ngIf`, `*ngFor` |
| Eloquent Models | TypeScript Interfaces |
| `composer.json` | `package.json` |
| `vendor/` | `node_modules/` |

---

### 🚀 Create an Angular Project

#### In Laravel:
```bash
composer create-project laravel/laravel my-project
```

#### In Angular:
```bash
npx @angular/cli new my-project
# or if you have Angular CLI installed globally:
ng new my-project
```

---

### 📁 Project Structure

#### Laravel has:
```
app/
├── Http/Controllers/    # Logic
├── Models/              # Data models
resources/
├── views/               # Blade views
public/
├── css/
├── js/
```

#### Angular has:
```
src/
├── app/
│   ├── models/          # Interfaces (like Models)
│   ├── app.ts           # Main component (like a Controller)
│   ├── app.html         # Template (like a Blade view)
│   └── app.css          # Component styles
├── index.html           # Entry point
└── styles.css           # Global styles
```

---

### 🧩 What is a Component?

**In Laravel** you have Controllers + Blade Views.
**In Angular** you have **Components** = Logic + View + Styles, all together.

```
┌─────────────────────────────────┐
│         COMPONENT               │
├─────────────────────────────────┤
│  app.ts     → Logic (TS)        │  ← Like a Controller
│  app.html   → View (HTML)       │  ← Like a Blade view
│  app.css    → Styles (CSS)      │  ← Specific styles
└─────────────────────────────────┘
```

---

### 📝 Syntax: Blade vs Angular Templates

#### Variables

**Blade (Laravel):**
```blade
<p>Hello {{ $name }}</p>
```

**Angular:**
```html
<p>Hello {{ name }}</p>
```
> Almost the same! Just in Angular we don't use `$`.

---

#### Conditionals

**Blade (Laravel):**
```blade
@if($show)
    <p>Visible</p>
@endif
```

**Angular:**
```html
<p *ngIf="show">Visible</p>
```
> The `*ngIf` is added as an element attribute.

---

#### Loops

**Blade (Laravel):**
```blade
@foreach($users as $user)
    <li>{{ $user->name }}</li>
@endforeach
```

**Angular:**
```html
<li *ngFor="let user of users">{{ user.name }}</li>
```

---

#### Forms (Two-Way Binding)

**Blade + JS (Laravel):**
```blade
<input type="text" id="name" value="{{ old('name') }}">
<script>
    document.getElementById('name').addEventListener('input', function(e) {
        // Manually update variable
    });
</script>
```

**Angular (automatic):**
```html
<input type="text" [(ngModel)]="name">
```
> `[(ngModel)]` automatically synchronizes the input with the variable.
> No additional JavaScript needed!

---

#### Events (Click)

**Blade + JS:**
```blade
<button onclick="sendData()">Submit</button>
<script>
    function sendData() {
        // logic
    }
</script>
```

**Angular:**
```html
<button (click)="sendData()">Submit</button>
```
```typescript
// In the .ts component
sendData() {
    // logic
}
```

---

#### Disable Elements

**Blade + JS:**
```blade
<button id="btn" disabled>Submit</button>
<script>
    if (formValid) {
        document.getElementById('btn').removeAttribute('disabled');
    }
</script>
```

**Angular (reactive):**
```html
<button [disabled]="!formValid">Submit</button>
```
> Automatically updates when `formValid` changes.

---

### 📦 Models: Eloquent vs TypeScript Interfaces

#### In Laravel you use Eloquent Models:
```php
// app/Models/Configuration.php
class Configuration extends Model {
    protected $fillable = ['name', 'lastname', 'range', 'attempts'];
}
```

#### In Angular you use TypeScript Interfaces:
```typescript
// src/app/models/configuration.ts
export interface Configuration {
    name: string;
    lastname: string;
    maxRange: number;
    attempts: number;
}
```

> The difference: Eloquent connects to the database. Angular interfaces only define the "shape" of the data on the frontend.

---

### ⚡ Getters: Computed Properties

#### In Laravel (Model):
```php
class User extends Model {
    public function getFullNameAttribute() {
        return $this->name . ' ' . $this->lastname;
    }
}
// Usage: $user->full_name
```

#### In Angular (Component):
```typescript
export class App {
    name = 'John';
    lastname = 'Smith';
    
    get fullName(): string {
        return this.name + ' ' + this.lastname;
    }
}
```
```html
<!-- Usage in template -->
<p>{{ fullName }}</p>
```

---

### 🔧 Useful Commands

| Action | Laravel | Angular |
|--------|---------|---------|
| Start server | `php artisan serve` | `npm run start` |
| Install dependencies | `composer install` | `npm install` |
| Create project | `composer create-project laravel/laravel` | `ng new` |
| Generate component | `php artisan make:controller` | `ng generate component` |

---

### 💡 Final Tips

1. **Angular is SPA**: The page doesn't reload, everything updates dynamically (unlike Laravel where each route reloads).

2. **TypeScript**: It's JavaScript with types. If you define `name: string`, TypeScript warns you if you try to assign a number.

3. **Automatic reactivity**: When you change a variable, the view updates itself. You don't need to manipulate the DOM.

4. **Reusable components**: You can create small components (like a button or form) and use them in multiple places.

---

[⬆️ Back to top](#-guía-angular-para-desarrolladores-laravel--angular-guide-for-laravel-developers) | [→ Cambiar a Español](#español)
