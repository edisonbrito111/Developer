# Eliminar archivos del repositorio si te has olvidado el .gitignore

Nos ha pasado a todos más de una vez que se nos olvida generar el correspondiente .gitignore después de haber hecho un commit. Observerás que, por mucho que estés diciendo que ahora sí quieres ignorar ciertas carpetas o rutas, éstas continúan en tu repositorio. Básicamente, ésto es así porque estaban allí antes de informar que se debían ignorar. En los siguientes commits serán ignoradas todas las modificaciones de las carpetas en cuestión, pero lo que había antes perdurará en el repositorio.

Por ejemplo, imagina que estás en un proyecto NodeJS. Olvidas de hacer el gitignore de la carpeta "node_modules". Entonces haces un commit y metes un montón de dependencias a tu repositorio git, que no debían estar. Si ves ahora en un sistema de interfaz gráfica tu repositorio (o subiéndolo a Github) podrás observar que los archivos de "node_modules" están ahí.

Luego creas tu .gitignore con el código para node, que puede ser muy grande pero donde querrás al menos ignorar los gestores de dependencias que puedas estar usando, como por ejemplo:

# Código gitignore para evitar procesar los directorios de las dependencias

node_modules
jspm_packages

Nota: Las líneas que comienzan por "#" en un .gitignore son simplemente comentarios.

Ahora haces nuevos commits pero los archivos no se borran. ¿Qué hacer entonces?

Básicamente lo solucionas con un comando de Git llamado "rm" que básicamente funciona igual que el comando del mismo nombre que usas para borrar archivos en una consola del estilo de Mac o Linux.

git rm -r --cached node_modules

Luego tendrás que hacer un commit para que esos cambios se apliquen al sistema de control de versiones.

git commit -m 'Eliminada carpeta node_modules del repo'

A partir de ahora esa carpeta no se verá en tu repositorio y gracias a tu .gitignore tampoco se tendrá en cuenta en las siguientes operaciones que realices mediante Git.
