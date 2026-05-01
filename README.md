# Trabajo Individual

![foto de perfil](images/perfil.jpg)

*Josue Joel Lizarazu Fernández*

## Clase 1 - 20 de abril, 2026

### ¿Qué es GIT?

Es un *sistema de control de versiones distribuido*, que nos permite guardar archivos y sus versiones a medidad que pasa el tiempo.

### ¿Cómo nació GIT?

Git nació porque, al principio, *Linus Torvalds* y los desarrolladores del kernel de Linux intercambiaban los cambios por correo, pero esa forma de trabajo no era muy eficiente para un proyecto tan grande.
Después empezaron a usar *BitKeeper*, que les ayudaba a organizar mejor las versiones. Sin embargo, años después se rompió la relación con la empresa de BitKeeper y se retiró el uso gratuito de la herramienta para el proyecto Linux.
Entonces Linus decidió crear su propia alternativa. De ahí nació Git.

### ¿Cómo instalar GIT?

#### Linux 
1. En el navegador buscar "Download GIT"
2. Buscar la distribución 
3. Copiar el comando y pegarlo en la terminal. Ejemplo: 
``` 
sudo apt install git 
```
4. Probar con:
```
git --version
```

#### Windows
1. En el navegador buscar "Download GIT"
2. Entrar a la pestaña "Windows"
3. Buscar la arquitectura de nuestra máquina y hacer clic en el instalador
4. Ejecutar el instalador y continuar con los pasos

### Configuraciones Básicas

+ Mostrar toda la *configuración actual* de Git, tanto general como del repositorio si existe.

```
git config --list 

```

+ Abrir la *ayuda de Git* del comando config

```
git config --help
```

+ Configurar *nombre de usuario* de forma global para todos tus repositorios en tu computadora.

```
git config --global user.name "nombredeusuario"
```

+ Configurar *correo electrónico* de forma global para todos tus respositorios.

```
git config --global user.email "nombre@correo.com"
```

+ Mostrar únicamente la configuración global de Git

``` bash
git config --global --list
```

+ Configura a Git para corregir automáticamente los *saltos de línea* de los archivos, evitando problemas entre Windows y otros sistemas operativos.

``` bash
git config --global core.autocrlf true
```

### Archivos que todo repositorio debería tener

+ **README.md**
Es un archivo de presentación y explicación del proyecto. Sirve para poner información como nombre del proyecto, autor, descripción, apuntes o avances, instrucciones de uso e imágenes.

+ **.gitignore**
Es un archivo que le dice a Git qué archivos no debe seguir ni subir al repositorio. 

### Inicializar un repositorio

Inicializa un repositorio Git en la carpeta actual. Conviete una carpeta común en una carpeta controlada por Git para usar commits, ramas y seguimiento de cambios.

``` bash
git init
```

Crea la carpeta oculta *.git* donde Git guarca toda la información del repositorio. Desde ese momento ya podemos usar comandos como *git add*, *git commit*, etc.

### Agregar archivo
Agregar el archivo README.md al área de preparación de Git.

``` bash
git add README.md
```

Confirmar este cambio:

``` bash
git commit -m "Primer commit"
```

### Sistema de puntuación - Fase 2
+ Examen: 50 pts
+ Trabajo Grupal (4 integrantes): 30 pts
+ Trabajo Individual: 10 pts
+ Asistencia: 9 pts
+ Forms del 19 de abril: 1 pts
Total: 100 pts

#### Examen
Examen presencial escrito en base a lo enseñado en clase. Contenido respecto a GIT

#### Trabajo Grupal
Grupos de 4 integrantes desarrollaran un mini proyecto a su elección que será presentado máximo hasta el día sábado 2 de mayo a horas 21:00. Calificación:
+ Participación de todos los miembros
+ Uso de GIT FLOW
+ Uso de buenas prácticas (en commits, ramas, etc)
+ README.md debe contener el nombre del equipo, integrantes, describir el mini-proyecto, y también incluir las instrucciones necesarias para ejecutar el proyecto de manera exitosa.

#### Trabajo Individual
Tener un repositorio desde el día 1. Tener un README.md, que debe contener el nombre y apuntes diarios. Se revisará los commits diarios.

#### Asistencia
Cada día se enviará un form en cualquier hora de la clase, disponible de 5 a 10 mins.

#### Aprobación
Puntaje mínimo 65 pts sobre 100 en total.

## STATES Y COMMITS (Clase 2 - 21 de abril, 2026)
### Los estados de GIT
1. *Directorio de Trabajo (Modificado)*: Tu carpeta local. Estás escribiendo código, pero Git aún no lo tiene "asegurado". Esto es después del git init. Git ve lo que estamos haciendo.
2. *Stage Area (Preparado)*: El área de espera. Le dices a Git: "Esto es lo que quiero guardar".
3. *Repositorio Local (Confirmado)*: El historial. Tus cambios ya tienen un ID (hash) y son parte de la historia. Pasan a un punto de guardado, en el historial o logs.

*Diagrama de cómo funcionan los estados de GIT:*

![flujo de como funciona Git](images/diagrama.png)

#### Directorio de trabajo (Modificado)
Es nuestra carpeta común, con la diferencia que GIT observa nuestros archivos y los cataloga en dos estados:

+ *Untracked (Sin seguimiento)*: Lo ve pero no tiene una versión antigua de este archivo, sucede cuando este es creado.
+ *Modified*: Es cuando GIT ya tiene una versión previa del archivo y lo modificaste, eliminaste o cambiaste de nombre.

Cualquier archivo que no este en el .gitignore pasa automaticamente a uno de estos estados dependiendo que hayamos hecho.

*¿Qué pasa si quiero que el archivo que modifique vuelva a su estado original? (Que pase de "Modified" a su estado original)*

``` bash
git restore <archivo>
```

Esto borra físicamente lo que escribieron, así que debemos tener cuidado.

*¿Qué pasa si quiero que el archivo que creé no quiero que lo vea GIT?*
Lo unico que debemos hacer es agregar el nombre del archivo completo al .gitignore.

#### Stage Area (Preparado)
Permite seleccionar qué archivos modificados se incluirán en el siguiente commit (guardado) y cuáles no.

Para traer un archivo al stage area lo que debemos hacer es:
``` bash
git add <archivo> // Agrega el archivo <archivo>, lo hace uno por uno
```
``` bash
git add . // Agrega todos los archivos que esten observados por GIT.
```
Si queremos sacar un archivo del stage area para volver al estado anterior:
``` bash
git restore --staged <archivo>
```

#### Repositorio Local (Confirmado)
Esta es la última fase, aquí es donde le decimos al repositorio que cree el punto de guardado para que todos los cambio que estan en staged pasen a ser parte del historial.
```
git commit -m "mensaje"
```
Si queremos deshacer el último commit el comando simple es:
```
git reset --soft HEAD~1
```
### Buenas prácticas

**¿Cada cuánto conviene hacer un commit?**

Lo recomendable es hacer commits frecuentes, pero con sentido.  
Cada commit debería representar un cambio pequeño, claro y completo dentro del proyecto.

No se trata de guardar por guardar, sino de registrar avances que tengan lógica.  
Es mejor tener varios commits pequeños y entendibles, que un solo commit grande con muchos cambios mezclados.

Una buena regla es esta:  
si puedes describir el cambio en una sola idea, probablemente merece su propio commit.

Por ejemplo:
- corregir un error puntual
- agregar una nueva funcionalidad pequeña
- mejorar el diseño de una sección
- actualizar documentación
- refactorizar una parte específica del código

Así, si en algún momento algo falla, será más fácil identificar qué cambio lo causó y volver atrás si es necesario.

---
#### Cómo escribir buenos commits

Un mensaje de commit debe ser corto, directo y fácil de entender.  
La idea es que cualquier persona pueda leer el historial y comprender qué se hizo sin revisar primero el código.

#### Recomendaciones generales

1. **Usa verbos que indiquen acción**
   El mensaje debe expresar claramente qué hiciste.

Ejemplos:
- `Add login form`
- `Fix error in navbar`
- `Update README`
- `Remove unused styles`

2. **Sé breve y específico**
   No escribas mensajes demasiado largos en el título del commit.

3. **Haz que cada commit tenga un único propósito**
   Si cambias muchas cosas distintas al mismo tiempo, conviene separarlas en varios commits.

4. **Evita mensajes vagos**
   Mensajes como `cambios`, `arreglos`, `update` o `cosas nuevas` no ayudan a entender el historial.

---

#### Ejemplos de mensajes de commit

```bash
git commit -m "Add user login validation"
```
Crea un commit con un mensaje breve que resume el cambio.
```bash
git commit -m "Fix sidebar on mobile"
```
Guarda una corrección puntual dentro del proyecto.
```bash
git commit -m "Update installation guide"
```
Registra una mejora hecha en la documentación.

#### Usa mensajes cortos

Como regla general, trata de que el mensaje principal no sea demasiado largo.
Si necesitas explicar muchas cosas, probablemente ese commit contiene varios cambios y conviene dividirlo.

Un mensaje corto y claro hace que el historial sea más fácil de leer.
#### Usa prefijos para que el historial sea más ordenado

En muchos proyectos se usan prefijos al inicio del mensaje para indicar el tipo de cambio realizado.

Algunos de los más comunes son:

- `feat:` agrega una nueva funcionalidad
- `fix:` corrige un error
- `docs:` modifica documentación
- `style:` cambia formato o estilos sin tocar la lógica
- `refactor:` reorganiza código sin cambiar su comportamiento
- `test:` agrega o modifica pruebas
- `build:` cambia procesos de instalación o compilación
- `ci:` modifica integración continua
- `perf:` mejora el rendimiento

Ejemplos:
```bash
git commit -m "feat: add search filter"
```
Guarda una nueva característica.
```bash
git commit -m "fix: correct button position"
```
Registra la corrección de un error.
```bash
git commit -m "docs: improve README structure"
```
Guarda cambios relacionados con la documentación.

#### Agrega más contexto cuando sea necesario

A veces el título del commit no es suficiente para explicar bien el cambio.
En ese caso, puedes escribir un commit con título y descripción más detallada.
```bash
git commit
```
Abre el editor para escribir el título y el cuerpo del commit.

Ejemplo:
```bash
feat: add profile edit option

Se añadió la opción para editar el perfil del usuario.
También se validan campos vacíos antes de guardar los cambios.
```

## GITHUB (Clase 3 - 22 de abril, 2026)
### ¿Qué es GitHub?
Es una plataforma en línea para almacenar, compartir y colaborar en código de software. Es como una red social para programadores, combinada con un servicio de almacenamiento en la nube y herramientas de control de versiones.

### Diferencia entre GIT y GitHub
En pocas palabras:
+ *Git* es la herramienta (motor)
+ *GitHub* es el sitio web (plataforma)

*Git* es como Microsoft Word instalado en tu laptop. Con Word podemos escribir, guardar cambios, ver versiones anteriores, corregir errores, etc. Todo sin internet. 

*GitHub* es como Google Docs (pero solo para código). Es un sitio web donde podemos escribir nuestro documento de Word (nuestro repositorio de Git) para que otros lo puedan ver, comentar, sugerir cambios, o incluso hagan una copia y escriban su propio capítulo. Además, Google Docs guarda nuestro documento en la nube por si se daña nuestra laptop o computadora.

### ¿Cómo crear una cuenta en GitHub?
1. Ir a https://github.com/
2. Sign up for GitHub
3. Continuar con Google y seleccionar una cuenta o ingresar un correo válido (no institucional - recomendado) 
4. Colocar un username (nombre)
5. Escoger el pais/región
6. Oprimir el botón de "Crear cuenta"

### Conectar nuestro repositorio con GitHub
Antes que nada debemos configurar el SSH de nuestra maquina para que se conecte con GitHub. 

*¿Por qué no HTTP/HTTPS?*

Porque *SSH es más seguro* (usa claves criptográficas) y *más cómodo* (no te pide usuario/contraseña ni token en cada push o pull). Con *HTTPS* tendríamos que autenticarnos constantemente; con SSH lo hacemos una sola vez.

*Configuración del SSH*
1. Desde Linux: Abrimos la terminal
   Desde Windows: Abrimos Git Bash
2. Ingresamos el siguiente comando:
   ```bash
   ssh-keygen -t ed25519 -C "nombre@correo.com"
   ```
   (El correo debe ser el mismo con el que creamos la cuenta de GitHub)
   
   Este es el comando que genera un par de claves SSH (pública y privada) usando el algoritmo Ed25519, donde -t especifica el tipo de cifrado y -C agrega una etiqueta (generalmente el correo de GitHub) para identificar quién creó la clave.
3. Damos Enter para aceptar la ubicación por defecto (~/.ssh/id_ed25519)
4. Mostramos la *clave pública* y la copiamos:
   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```
   Comandos alternativos según dónde guardaste la clave 
   | Situación | Comando | Nota |
   | :--- | :--- | :--- |
   | **Ubicación por defecto** | `cat ~/.ssh/id_ed25519.pub` | Muestra la clave en pantalla para copiarla manualmente |
   | **Ubicación personalizada** | `cat /ruta/donde/guardaste/la/clave.pub` | Reemplaza "ruta" por la que elegiste al ejecutar `ssh-keygen` |
   | **Copiar directamente al portapapeles (Linux)** | `xclip -sel clip < ~/.ssh/id_ed25519.pub` | Necesitas tener `xclip` instalado |
   | **Copiar directamente al portapapeles (Windows Git Bash)** | `clip < ~/.ssh/id_ed25519.pub` | Te ahorra seleccionar y copiar manualmente |
   | **Copiar directamente al portapapeles (Mac)** | `pbcopy < ~/.ssh/id_ed25519.pub` | Comando nativo de macOS |
5. Dentro de GitHub ir a Configuración y Claves SSH y GPG.
6. Click en "Nueva clave SSH".
7. Añadir un título (ej: "Mi PC") y pegar la clave en el apartado Clave.
8. Click en "Agregar clave SSH".


#### Pasos
1. Crearse un nuevo repositorio en el apartado de "Repositorio" en GitHub
2. Colocar el nombre de la carpeta local de preferencia o si es uno vacío cualquier nombre.
3. *Configuración:*
   - `Choose Visibility:` Con *public* lo ve cualquier persona y con *private* solo lo ves tú y las personas que invites.
   - `Add README:` *On* para crear automáticamente un archivo README.md con información sobre el proyecto (descripción, cómo usarlo, etc.) y *Off* para no crearlo y tener el repositorio vacío inicialmente.
   - `Add gitignore:` Selecciona una plantilla para ignorar archivos temporalmente o de configuración que no queramos subir al repositorio. 
   - `Add license:` Elige una licencia (como MIT, GPL, Apache) para definir qué permisos tienen otros usuarios para usar, modificar o distribuir nuestro código. 
4. Seguidamente, GitHub nos da comandos de que es lo que debemos hacer para contectar nuestro repositorio existente desde la terminal:
   ```bash
   git remote add origin git@github.com:Username/Repositorio.git
   ```
   (Enlaza nuestra carpeta local con el repositorio remoto de GitHub usando la clave SSH)
   ```bash
   git branch -M main
   ```
   (Renombra la rama actual a "main" - estándar de GitHub)
   ```bash
   git push -u origin main
   ```
   (Sube nuestro código local a GitHub por primera vez y guarda la conexión para futuros *push* simples.)

### Clonar un repositorio
Para clonar un repositorio usamos el comando:
```bash
git clone "git@github.com:Username/Repositorio.git"
```

Si por accidente lo hiciste con *HTTPS*:
```bash
git clone "https://github.com/Username/Repositorio.git"
```

Usamos el siguiente comando para cambiar el puntero de github y no te pida autenticación cada vez:
```bash
git remote set-url origin "git@github.com:Username/Repositorio.git"
```
(Este comando tamibén se usa si queremos cambiar el repositorio remoto al cual esta conectado el repositorio)

Si queremos ver a que repositorio remoto esta conectado nuestro repo usamos el siguiente comando:
```bash
git remote -v
```

### Cambios en un repositorio
Para subir cualquier cambio a nuestro repositorio usamos el siguiente comando:
```bash
git push origin <rama>
```
#### Comandos
+ `git push:` "Empujar" nuestros commits.
+ `origin:` ¿A dónde? Al servidor que apodamos "origin" (GitHub).
+ `<rama>`: ¿Qué rama? La rama `<rama>` de mi código.

### Bajar los cambios de un repositorio
Para bajar o traer los cambios hechos en un repositorio se utiliza el siguiente comando:
```bash
git pull origin <rama>
```
#### Comandos
+ `git pull:` "Traer" los commits del servidor.
+ `origin:` ¿De dónde? Del servidor que apodamos "origin" (GitHub).
+ `<rama>:` ¿Qué rama? La rama `<rama>` de mi código

## REMOTE, SSH MULTIPLE Y CHECKOUT (Clase 4 - 23 de abril, 2026)

### GIT REMOTE

`git remote` es el comando que nos permite administrar las conexiones con repositorios remotos. Le indica a Git local a dónde enviar información y de dónde traerla.

Algunos comandos útiles son:

```bash
git remote -v
```
Permite ver las URLs exactas a las que apunta nuestro repositorio.

```bash
git remote add <apodo> "url"
```
Vincula nuestro repositorio local con uno remoto en la nube.

```bash
git remote set-url <apodo> "url"
```
Cambia la URL a la que apunta nuestro repositorio.

### Múltiples SSH

Si tenemos más de una cuenta de GitHub, o necesitamos trabajar con varias cuentas, conviene usar más de una llave SSH. Cada cuenta necesita su propia llave para evitar conflictos entre accesos. La idea es como tener una llave distinta para cada puerta.

### Configurar múltiples SSH

#### Paso 1. Generar una nueva llave SSH con otro nombre

```bash
ssh-keygen -t ed25519 -C "micorreo@gmail.com" -f ~/.ssh/id_miname
```

Este comando crea una nueva llave SSH con un nombre distinto al que ya usábamos por defecto. Así podemos separar una cuenta personal de otra cuenta adicional.

#### Paso 2. Crear el archivo `config`

Debemos crear o editar el archivo `~/.ssh/config` para que cada llave use su propia configuración y no choquen entre sí.

Ejemplo:

```text
# Cuenta personal (la de siempre)
Host github.com
HostName github.com
User git
IdentityFile ~/.ssh/id_ed25519

# Cuenta del otro correo
Host github-miname
HostName github.com
User git
IdentityFile ~/.ssh/id_miname
```

#### Significado de cada parte del archivo config

- **Host:** es el alias o apodo que le damos a la conexión. Es lo que escribimos después de `git@`.
- **HostName:** es la dirección real del servidor. En GitHub siempre será `github.com`.
- **User:** es el usuario del sistema remoto. En GitHub siempre es `git`.
- **IdentityFile:** es la ruta de la llave privada que se usará para ese `Host`.

#### Paso 3. Verificar que funcione

```bash
ssh -T git@github-miname
```

Este comando sirve para comprobar si la configuración de la nueva llave SSH está funcionando correctamente.

### Configuraciones locales

Las configuraciones locales tienen prioridad sobre las globales, pero solo dentro del repositorio donde se aplican. Para hacer una configuración local se usa el mismo comando que en la configuración global, pero sin `--global`.

```bash
git config user.name "Mi nuevo Name"
git config user.email "micorreo@gmail.com"
```

Esto significa que podemos tener un nombre y correo diferentes según el repositorio en el que estemos trabajando.

### Importante al clonar con múltiples SSH

Si usamos varias cuentas SSH, debemos clonar con el `Host` correcto de esa cuenta.

```bash
git clone git@github-miname:usuario/repo.git
```

Si usamos el host equivocado, Git intentará autenticarse con otra llave y puede fallar el acceso.

### Git Checkout

`git checkout` es el comando que nos permite mover el `HEAD` (el puntero actual) hacia un punto específico del historial o hacia otra rama.

#### ¿Para qué sirve?

- **Inspeccionar:** ver cómo era el código en un commit antiguo.
- **Restaurar:** recuperar archivos que borramos o modificamos.
- **Experimentar:** probar cambios sin afectar la rama principal.
- **Cambiar:** pasar de una rama a otra, por ejemplo de `main` a `desarrollo`.

### El estado "Detached HEAD"

Normalmente, `HEAD` apunta a una rama, y esa rama se va moviendo con nuevos commits. Pero en estado **Detached HEAD**, `HEAD` apunta directamente a un commit específico, no a una rama.

#### ¿Qué significa?

- Estamos viendo el proyecto en un punto del pasado.
- Podemos revisar archivos e incluso hacer cambios.
- Pero si hacemos cambios y luego salimos de ahí sin crear una rama, esos cambios pueden quedar perdidos.

### ¿Cómo ir y volver de un commit?

Para movernos a un commit antiguo:

```bash
git checkout <hash_antiguo>
```

Para volver al último commit de una rama:

```bash
git checkout <rama>
```

Si hicimos algo importante en ese estado, por ejemplo un commit, no debemos salir sin antes rescatarlo. Para conservarlo:

```bash
git checkout <hash_commit_creado>
git checkout -b rama_nueva
```

Así creamos una nueva rama a partir de ese commit y evitamos que el trabajo se pierda.

### Buenas prácticas del checkout

- Antes de ir a un commit del pasado, conviene hacer commit de lo que estamos haciendo en el presente. Si no, Git puede impedir el cambio.
- Si vamos a trabajar varias líneas o hacer cambios importantes, es mejor crear una rama de una vez.
- No conviene pasar mucho tiempo trabajando en estado `Detached HEAD`.
- Hacer checkout a commits de proyectos grandes sirve bastante para aprender cómo fue creciendo el proyecto.

## RAMAS Y GITFLOW BÁSICO (Clase 5 - 27 de abril, 2026)
### ¿Qué son las ramas?

Las ramas son una de las herramientas más importantes de Git para llevar un mejor control del código.  
Una rama es una bifurcación del estado actual del proyecto, que crea un camino nuevo para seguir desarrollando en paralelo sin afectar directamente a otras ramas.

### Git Branch

`git branch` es el comando que nos permite gestionar las ramas que tiene o tendrá nuestro proyecto.

#### Comandos básicos de `git branch`

```bash
git branch
```
Lista las ramas disponibles y muestra en cuál está posicionado actualmente el `HEAD`.

```bash
git branch <rama>
```
Crea una nueva rama a partir de la rama en la que estamos posicionados.

```bash
git branch -D <rama>
```
Elimina una rama.

### Git Checkout enfocado en ramas

Aunque antes usamos `git checkout` para movernos a commits antiguos, también se puede usar con ramas.

```bash
git checkout <rama>
```
Cambia de una rama a otra. Para hacerlo sin problemas, no deberíamos tener archivos en estado `modified`, `untracked` o `staged`.

```bash
git checkout -b <rama>
```
Crea una nueva rama y además nos mueve a ella directamente.

### Git Checkout vs Git Switch

Originalmente, `git checkout` era un comando sobrecargado porque servía para varias cosas: cambiar ramas, ir a commits antiguos y restaurar archivos.  
En 2019, desde Git 2.23, se introdujo `git switch` para separar mejor el manejo de ramas y hacer el flujo más seguro e intuitivo.

#### Diferencia principal

- **`git checkout`** es multipropósito: sirve para ramas, commits y archivos.
- **`git switch`** está especializado únicamente en ramas y evita errores accidentales al moverte.

En resumen, `git checkout` es el comando clásico y universal, mientras que `git switch` es una alternativa más moderna para trabajar específicamente con ramas.

### Gitflow básico

Gitflow es un flujo de trabajo que nos permite organizar mejor las ramas del proyecto.  
A través de reglas y convenciones, ayuda a que el trabajo en equipo sea más ordenado, entendible y fácil de mantener. Es especialmente útil en proyectos donde varias personas trabajan al mismo tiempo.

Sin Gitflow, las ramas pueden volverse desordenadas y difíciles de entender.  
Con Gitflow, el trabajo se organiza mejor y la estructura de ramas se vuelve mucho más clara visualmente.

### ¿Cómo funciona Gitflow?
#### Rama `main`
Es la rama principal que normalmente existe por defecto al crear un repositorio.  
Su propósito es contener el código que ya está en producción.

#### Rama `develop`
Es la rama de preproducción.  
Aquí se integran las características que todavía están en prueba o validación, pero que más adelante se lanzarán a producción.  
Es la rama en la que normalmente más se trabaja durante el proyecto.

#### Ramas de apoyo
Son ramas auxiliares que se usan para escribir código de forma más ordenada.  
Las principales son:

- `feature`
- `release`
- `hotfix`

### Ramas de apoyo en Gitflow
#### `feature/*`
Se usan cuando trabajamos en una nueva característica para el proyecto.  
Estas ramas nacen desde `develop`, y cuando la funcionalidad está terminada, vuelven a fusionarse en `develop` y luego se eliminan.

Ejemplos de nombres:
- `feature/sum-function`
- `feature/add-search-bar`
- `feature/new-form-user`

#### `release/*`
Se usan cuando se está preparando una nueva versión del proyecto.  
En teoría, aquí se hacen pruebas y ajustes finales antes del lanzamiento.  
Nacen desde `develop` y luego se fusionan en `main` o también de vuelta en `develop`.

Ejemplos de nombres:

- `release/v1.0.0`
- `release/v2.1.0-beta`

#### `hotfix/*`
Se usan para arreglar problemas imprevistos en producción, como errores críticos o fallos urgentes.  
Por eso nacen desde `main`, ya que `develop` puede tener cambios inestables todavía.  
Después se fusionan en `main` y también en `develop`.

Ejemplos de nombres:
- `hotfix/login-authentication-error`
- `hotfix/fix-database-connection-leak`
- `hotfix/security-patch-v1.0.2`
- `hotfix/api-timeout-emergency`
- `hotfix/mobile-responsive-crash`
- `hotfix/broken-payment-gateway`

### Resumen de Gitflow
- **`develop`** nace de `main`, no se elimina y representa el trabajo diario del equipo.
- **`feature/*`** nace de `develop`, muere en `develop` y sirve para desarrollar una tarea específica.
- **`release/*`** nace de `develop`, muere en `main` y `develop`, y sirve para preparar la versión final.
- **`hotfix/*`** nace de `main`, muere en `main` y `develop`, y sirve para corregir errores urgentes en producción.

## GIT MERGE, FETCH, PULL Y PUSH (Clase 6 - 28 de abril, 2026)
### ¿Qué es `git merge`?

La palabra *merge* significa “fusión”.  
Por eso, `git merge` es el comando que nos permite unir dos ramas en una sola, incorporando en una rama los commits que fueron realizados en otra.

En otras palabras, sirve para combinar el trabajo hecho en distintas ramas y mantenerlo dentro de una misma línea de desarrollo.

```bash
git merge <rama>
```

Este comando fusiona la rama indicada con la rama en la que estamos posicionados actualmente.

#### Uso de `--no-ff`

Existe el flag `--no-ff`, que significa **no fast forward**.  
Su función es evitar que Git haga una fusión rápida donde parezca que la rama nunca existió como tal.

```bash
git merge --no-ff <rama>
```

Al usar este flag, Git conserva mejor el historial de ramas y además fuerza la creación de un commit de merge.  
Esto ayuda a que se vea con más claridad cuándo una rama fue integrada al proyecto, incluso si después esa rama se elimina.

### ¿Qué es `git fetch`?

`git fetch` es el comando que permite revisar si existen cambios nuevos en el repositorio remoto, sin mezclarlos todavía con tu rama local.

```bash
git fetch
```

Este comando actualiza la información de las ramas remotas y te permite ver si hubo cambios, pero no modifica tu trabajo actual directamente.  
Es útil para comprobar si otra persona subió cambios antes de hacer un `pull` o un `merge`.

### ¿Qué es `git pull`?
`git pull` es el comando que trae los cambios del repositorio remoto a tu rama local.

```bash
git pull origin <rama>
```

Se recomienda usarlo junto con `origin` y el nombre de la rama para indicar exactamente de dónde quieres traer los cambios.  
Así se evitan confusiones cuando trabajamos con varias ramas o con repositorios compartidos.

### ¿Qué es `git push`?
`git push` es el comando que sube tus commits desde tu repositorio local hacia el repositorio remoto.

```bash
git push origin <rama>
```

También es recomendable usarlo junto con `origin` y el nombre de la rama, para dejar claro a qué rama remota quieres enviar tus cambios.

#### Uso de `-u`
Si no es tu repositorio, o es la primera vez que subes esa rama al remoto, conviene usar el flag `-u`.

```bash
git push -u origin <rama>
```

Este flag establece una relación de seguimiento entre tu rama local y la rama remota.  
De esa forma, después podrás usar simplemente `git push` o `git pull` sin tener que escribir todo de nuevo.

### Flujo de trabajo básico (sin Pull Requests)

Un flujo de trabajo básico en equipo, sin usar Pull Requests, puede seguir estos pasos:

#### 1. Actualizar la rama `develop`
```bash
git checkout develop
git fetch
git pull origin develop
```

Primero nos movemos a la rama `develop`, revisamos si hay cambios en el remoto y luego los traemos a nuestra copia local.

#### 2. Volver a nuestra rama de trabajo
```bash
git checkout <rama>
git merge develop
```

Después regresamos a nuestra rama de trabajo y fusionamos `develop`, pero solo si hubo cambios nuevos.  
Así trabajamos con una rama lo más actualizada posible.

#### 3. Trabajar y subir cambios
```bash
git push origin <rama>
```

Aquí subimos nuestros avances al repositorio remoto.  
Si es la primera vez que subimos esa rama, entonces usamos:

```bash
git push -u origin <rama>
```

#### 4. Integrar nuestra rama en `develop`
```bash
git checkout develop
git fetch
git pull origin develop
git merge --no-ff <rama>
```

Luego volvemos a `develop`, la actualizamos y fusionamos nuestra rama usando `--no-ff` para conservar mejor el historial.

#### 5. Resolver conflictos si aparecen
Si durante el merge aparecen conflictos, debemos resolverlos manualmente en los archivos afectados.  
Una vez resueltos, hacemos:

```bash
git add .
git commit
```

Con esto confirmamos la resolución del conflicto y finalizamos el merge.

#### 6. Eliminar la rama si ya no se necesita
```bash
git branch -D <rama>
```

Cuando la rama ya fue fusionada y no se va a seguir usando, se puede eliminar localmente.

#### 7. Subir la rama principal actualizada
```bash
git push origin develop
```

Finalmente, subimos la rama `develop` ya actualizada con los cambios fusionados.

### Resumen
- `git merge` une ramas.
- `git fetch` revisa cambios remotos sin aplicarlos.
- `git pull` trae cambios del remoto a tu rama local.
- `git push` sube tus cambios al remoto.
- `git push -u origin <rama>` se usa la primera vez para enlazar la rama local con la remota.
- `git merge --no-ff <rama>` ayuda a conservar mejor el historial de integración de ramas.

### PULL REQUEST Y PROTECCIÓN DE REPOSITORIO (Clase 7 - 29 de abril, 2026)
### ¿Qué son los Pull Requests?
Los **Pull Requests**, también conocidos como **PRs**, son una forma más profesional y ordenada de trabajar con Git y GitHub.

Un Pull Request es una solicitud que se crea en GitHub para proponer que los cambios realizados en una rama sean fusionados con otra rama del proyecto, normalmente `develop` o `main`.

Su principal ventaja es que permite que otras personas del equipo revisen los cambios antes de integrarlos al código base.  
De esta manera, no se hace el merge directamente, sino que primero existe una etapa de revisión, comentarios y aprobación.

### ¿Por qué usar Pull Requests?
Trabajar sin Pull Requests puede ser más rápido, pero también más riesgoso.  
Si cualquier colaborador puede hacer `push` y `merge` directamente, se pierde control sobre lo que entra al proyecto.

Los PRs ayudan a:

- revisar los cambios antes del merge
- entender qué se modificó y por qué
- debatir o comentar propuestas
- aprobar o rechazar cambios
- mejorar la organización del trabajo en equipo
- reducir errores o integraciones no revisadas

En resumen, los Pull Requests hacen que el trabajo grupal sea más seguro, más claro y más controlado.

### ¿Cómo crear un Pull Request?
Primero debemos subir nuestra rama al remoto:

```bash
git push origin <rama>
```

Si es la primera vez que subimos esa rama:

```bash
git push -u origin <rama>
```

Después, en GitHub, se sigue este flujo:

1. Entrar al repositorio en GitHub.
2. Buscar el aviso o banner que indica que tu rama tuvo cambios recientes.
3. Hacer clic en **Compare & pull request**.
4. Verificar que en `base` esté la rama destino, normalmente `develop` o `main`.
5. Verificar que en `compare` esté tu rama con los cambios.
6. Escribir un título claro y una descripción breve de lo que hiciste.
7. Hacer clic en **Create pull request**.

A partir de ahí, el equipo puede revisar los cambios, dejar comentarios, pedir correcciones o aprobar el merge.