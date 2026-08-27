### Conceptos de git ###
Git gestiona el control de versiones mediante un sistema distribuido que rastrea el historial de cambios en el código local y remoto a través de los siguientes conceptos fundamentales:

Las Tres Áreas de Trabajo

- Working Directory (Directorio de trabajo): Carpeta local en el sistema donde editas y creas archivos en tiempo real.

- Staging Area (Index): Zona de preparación donde seleccionas los cambios específicos que formarán parte de la próxima versión antes de guardarlos (git add).

- Repository (HEAD): Base de datos local donde Git guarda permanentemente las versiones y el historial del proyecto (git commit).

## Elementos y Operaciones Principales ##
- Commit: Captura del estado de tus archivos en un momento dado, identificada de forma única por un código alfanumérico (hash SHA-1).

- Branch (Rama): Puntero móvil que apunta a un commit específico. Permite desarrollar funcionalidades, corregir errores o experimentar en aislamiento sin alterar la línea principal (main o master).

- Merge: Operación para integrar el historial de una rama secundaria dentro de otra rama (por ejemplo, unir una rama de trabajo a main).

- Rebase: Alternativa a la fusión que reaplica los commits de una rama sobre la punta de otra para mantener un historial lineal y limpio.

- Checkout / Switch: Comandos utilizados para cambiar entre diferentes ramas o recuperar versiones antiguas del código.

