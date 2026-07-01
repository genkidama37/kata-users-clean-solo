# Kata users app

Basado en las dispositivas de [Jorge Sánchez (aka xurxodev)(https://xurxodev.com/).

## Descripción general
### Requerimientos funcionales
- Mostrar Lista de usuarios.
- Añadir un usuario nuevo.
- Un usuario debe contener:
  - Nombre.
  - Email. 
  - Password. 
  como campos obligatorios.
- El email debe ser un email válido. Eso significa que:
 - Contiene un nombre de usuario.
 - Contiene un nombre de host.
 - Contiene el dominio del host.
 - El nombre del usuario está separado del nombre del host mediante un carácter de '@'.
 - El nombre del host está separado del dominio del host mediante un punto('.').

- La password debe:
 - Ser mínimo 8 caracteres.
 - Contener al menos una letra.
 - Contener al menos un número.

- La app debería mostrar un error si se intenta añadir dos usuarios con el mismo email.

**Bola Extra**
- Añade la dirección, formada por: 
 - Dirección
   - Via.
   - Número. 
   - [Opcionalmente] piso y/o puerta.
 - Código Postal.
 - Ciudad.
 como parte de la información necesaria para el usuario.
- Solo puede existir un usuario por dominio (1 usuario con gmail.com, etc..).

### Plataforma de desarrollo
- La UI será una app de línea de comandos o terminal.
- Todos los datos en memoria, Sin persistencia entre ejecuciones.
- El origen de los datos podrá ser en un futuro una API o Base de datos.
- La UI podrá cambiar en un futuro a una web app, mobile app o desktop app.
- Las reglas de negocio deben ser validadas mediante test unitarios.
- En los tests las dependencias serán reemplazadas por dependencias fake manuales.
- Hay que crear también tests de igualdad para los value objects y entidades.
- Usa MVP para la capa de presentación.
