# Kata Users Practice

## Español

### Qué es y por qué
Este repositorio es mi practica deliberada de los principios de Clean Architecture vistos
en el **[curso de Clean Architecture de Jorge Sánchez](https://xurxodev.com/curso-clean-architecture/)**.
Esto lo haré mediante el ejercicio que hicimos en el curso: la [Kata Users](kata-users.es.md).

Mi intención al repetir el ejercicio solo (en el curso lo hicimos en grupos) es interiorizar los 
principios básicos de Clean Architecture. Además de afrontar el reto de resolver la kata yo solo. 
En mi caso concreto, además, incluye el reto de practicar el escribir tests en base a las 
especificaciones del ejercicio.

Este repositorio contiene un ejercicio de práctica deliberada. No es la base para una app de producción.
### Alcance


Para empezar me voy a centrar en las dos primeras partes de la kata: Entidades y Casos de Uso.
#### Parte 1 - Entidades
- Define entidades y value objects.
- Las reglas empresariales deben estar testeadas creando test unitarios.
  - Reglas:
    - El usuario debe tener:
     - Nombre.
     - Email. 
     - Password 
     como obligatorios.
  - El email debe ser un email válido.  Eso significa que:
    - Contiene un nombre de usuario.
    - Contiene un nombre de host.
    - Contiene el dominio del host.
    - El nombre del usuario está separado del nombre del host mediante un carácter de '@'.
    - El nombre del host está separado del dominio del host mediante un punto('.').
  - La password debe:
    - Ser mínimo 8 caracteres.
    - Contener al menos una letra.
    - Contener al menos un número.
  - Dos instancias de un mismo email deben ser iguales.
  - Dos instancias de una misma password deben ser iguales en una comparación.
  - Dos instancias de user con el mismo id deben ser iguales en una comparación.

**Bola Extra**
- Añade la dirección, formada por:
  - Dirección
  - Via.
  - Número.
  - [Opcionalmente] piso y/o puerta.
  - Código Postal.
  - Ciudad.
 como parte de la información necesaria para el usuario.

#### Parte 2 - Casos de uso
- Define los casos de uso, repositorio para:
  - Mostrar Lista de usuarios.
  - Añadir un usuario nuevo.
- Las reglas de aplicación deben estar testeadas creando test unitarios.
- En los test unitarios puedes utilizar objetos fake manuales.
- Reglas:
    - La aplicación no debe permitir añadir dos usuarios con el mismo email.
**Bola Extra**
- Solo puede existir un usuario por dominio (1 usuario con gmail.com, etc.)

#### N/A
- Instrucciones para despliegue.
- Usar variables de entorno.
- Usar libreria de tests propia o externa.
- TypeScript: fuerzo generics/union types para lucirlos.
- Usar un Linter.

### Arquitectura
#### Estructura de carpetas        
Agruparemos las carpetas por capas:
  - `domain` incluye:
    - `entities`
    - `value-objects`
    - `core`: aquí vivirán las clases abstractas de las que heredan las clases base para entidades y objetos valor. Contiene la lógica de igualdad por valor compartida, con sus tests.
  - `use-cases`


Cada capa incluirá su carpeta `__tests__`.

```
── src
    ├── use-cases
    │   └── __tests__
    ├── domain
    │   ├── core
    │   │    └── __tests__
    │   ├── entities
    │   │    └── __tests__
    │   └── value-objects
    │        └── __tests__
```

#### Principios y decisiones de diseño

Se aplica la ley de dependencia de Clean Architecture: El dominio no depende de las capas exteriores.

Las capas exteriores dependen de las capas interiores. Y el dominio está en la capa más interior.


Se prioriza el uso de objetos valor para representar strings como el nombre o el email para evitar el code smell: **Primitive Obsession**.

La validación deberá devolver todos los errores cometidos a la vez.

Para la presentación se implementará el [patrón MVP](https://learn.microsoft.com/en-us/archive/msdn-magazine/2006/august/design-patterns-model-view-presenter).
Convenciones:
- Tanto para nombres de directorios como nombres de carpetas se usará `kebab-case`. Motivos:
  - Por probar este enfoque a ver que tal.
  - Mejora la legibilidad de nombres de carpetas multipalabra.
  - Evitar problemas de "case-insensitivity". En el dia a dia uso mac os, que es case insensitive. Ocasionalmente uso otras máquinas con sistemas Linux, que si son "case sensitive". I quiero poder trabajar en ambos sistemas sin problemas.

### (más adelante) Cómo ejecutar y tests   ← esqueleto, no escribir aún
### Detalles de implementación
- Uso de TypeScript.
- npm como gestor de paquetes.
- Prettier como formateador de código.

