### ¿Cómo te ha ayudado Git a mantener un historial claro y organizado de tus cambios?

Ayuda a tener una mejor vista y presentación de las actualizaciones que
tenemos en el archivo, tanto como la agregación de archivos .md como
.py, que con el comando \"git log \--online\" nos da de manera
organizada, una lista que todos los commit hechos para así llevar mejor
la organización del proyecto, ya que cada commit contará con una
descripción sobre que se ha hecho en ese commit

### ¿Qué beneficios ves en el uso de ramas para desarrollar nuevas características y corregir errores?

Permite modificar el código pero sin dañar el código principal, es decir
para arreglar algún problema, se crea una rama y en esta se puede
modificar el archivo con sus respectivos commits, y si se arregla el
problema, con un merge en la rama principal, unimos esa rama con la
principal, pero si no se arregla el problema, solo eliminamos esa rama y
el código no se vería afectado, sirve para la modificación \"externa\"
del archivo sin afectar la rama principal

- Ejercicio 1: Manejo avanzado de de ramas y resolución de conflictos

1.  Crear una nueva rama para una característica:

![](image2.webp){width="3.6927088801399823in"
height="1.329734251968504in"}

2.  Modificar archivos en la nueva rama:

    a.  Editar el archivo main.py con una función adicional: main.py de
        la rama feature/advanced-feature

> ![](image18.webp){width="3.15625in"
> height="1.0759350393700788in"}

b.  Añade y confirma estos cambios en la rama feature/advanced-feature:

> ![](image21.webp){width="4.942708880139983in"
> height="0.8867311898512686in"}

3.  Simular un desarrollo en paralelo en la rama main:

    a.  Cambiar la nueva ruta a la rama main

> ![](image38.webp){width="3.182292213473316in"
> height="1.3627329396325458in"}

b.  Edita el archivo main.py de forma diferente: main.py de la rama main

> ![](image30.webp){width="3.5381364829396325in"
> height="0.9337937445319335in"}

c.  Añade y confirma los cambios en la rama main

> ![](image15.webp){width="5.098958880139983in"
> height="1.3467344706911637in"}

4.  Intenta fusionar la rama feature/advanced-feature en main:
    Generación de error

> ![](image41.webp){width="5.401042213473316in"
> height="1.11250656167979in"}

5.  Resolver el conflicto de fusión

> ![](image29.webp){width="4.807638888888889in"
> height="1.5572922134733158in"}

6.  Eliminar la rama fusionada

> ![](image20.webp){width="4.109375546806649in"
> height="0.9582786526684165in"}

- Ejercicio 2: Exploración y manipulación del historial de commits

1.  Ver el historial detallado de commits (git log -p)

> ![](image22.webp){width="4.130208880139983in"
> height="4.130208880139983in"}

2.  Filtrar commits por autor (git log \--author="Nombre")

> ![](image10.webp){width="4.213542213473316in"
> height="1.898928258967629in"}

3.  Revertir un commit (git revert HEAD)

> ![](image33.webp){width="3.2130577427821523in"
> height="1.0427602799650044in"}
>
> ![](image9.webp){width="4.296875546806649in"
> height="1.4160159667541556in"}
>
> luego git revert HEAD, me salió en la consola para confirmar la
> reversión, y luego de poner ESC y :wq me salió lo siguiente
>
> ![](image11.webp){width="3.5156255468066493in"
> height="1.3447747156605425in"}

4.  Rebase Interactivo

    a.  Al usar git rebase -i HEAD\~3 aparece la siguiente consola

> ![](./media/media/image32.png){width="4.21875in"
> height="0.6469925634295713in"}

b.  Utilizamos squash para combinar los 3 últimos commits

> ![](image17.webp){width="4.03125in"
> height="0.761233595800525in"}

c.  Ponemos ESC y :wq y Enter para aceptar el rebase, luego si hay
    errores modificamos el archivo que da error, lo añadimos, le damos
    commit y luego con git rebase \--continua se termina el rebase

<!-- -->

5.  Visualización gráfica del historial:

> ![](image39.webp){width="4.880208880139983in"
> height="0.8187729658792651in"}

- Ejercicio 3: Creación y gestión de ramas desde commits específicos

1.  Crear una nueva rama desde un commit específico

    a.  Creando rama desde el commit f09f2cd

> ![](image34.webp){width="4.151042213473316in"
> height="0.4967060367454068in"}
>
> El hash del commit sobre el que cree la rama, en la imagen de arriba
> se puede notar que es antes de añadir el main.py, por lo tanto si me
> ubico a esa nueva rama, el sistema me avisa que no existe el main.py
>
> ![](image19.webp){width="4.110954724409448in"
> height="1.5070527121609798in"}
>
> podemos notar que el main.py está tachado indicando que no existe en
> esa rama, pero si vuelvo a la rama main, notamos que si existe
>
> ![](image27.webp){width="3.3177088801399823in"
> height="1.4079669728783901in"}
>
> Para continuar, eliminamos la nueva rama y la creamos en la dirección
> del último commit hecho, resolviendo distintos problemas, el último
> commit hecho por mi, sería c57def9 y a partir de ahí creamos la rama,
> modificamos el main y fusionamos con la rama principal

2.  Modificar y confirmar cambios en la nueva rama

3.  Fusionar los cambios en la rama principal

> ![](image36.){width="4.557292213473316in"
> height="3.5101859142607172in"}

4.  Explorar el historial después de la fusión

    a.  Con el codigo git log \--graph \--oneline se aprecia el
        historial y podemos ver la generación de una nueva rama y su
        unión generando solo una

> ![](image23.webp){width="5.296875546806649in"
> height="1.58378280839895in"}

5.  Eliminar la rama bugfix/rollback-feature

- Manipulación y restauración de commits con git reset y git restore

1.  Hacer cambios en el archivo main.py y hacer commit

> ![](image31.webp){width="4.390625546806649in"
> height="1.257561242344707in"}

2.  Usar git reset para deshacer el commit:

    a.  Como se puede ver en la ultima figura de la sección anterior,
        nuestro ultimo commit tenía el hash f576797, así que al hacer el
        commit anterior, y al aplicar git reset \--hard HEAD\~1
        tendríamos que volver al commit con hash f576797 para verificar
        que hemos deshecho el commit de la primera parte

> ![](image43.webp){width="5.015625546806649in"
> height="1.4247036307961505in"}

3.  Usar git restore para deshacer cambios no confirmados:

    a.  Modificamos el archivos README.md creada al comienzo de la
        actividad y al usar git status, notamos que como no hemos hecho
        un add, la modificación está sin confirmar, no está en 'stages'
        osea listo para el commit

> ![](image45.webp){width="4.755208880139983in"
> height="2.765977690288714in"}

b.  Aplicamos git restore y notamos que deshace el cambio no confirmado,
    y al usar git status vemos que no hay modificación pendiente

> ![](image12.webp){width="3.901042213473316in"
> height="1.9414063867016622in"}

- Ejercicio 5: Trabajo colaborativo y manejo de Pull Requests

1.  Crear un nuevo repositorio remoto:

> ![](image44.webp){width="5.098958880139983in"
> height="1.228153980752406in"}

2.  Crear una nueva rama para desarrollo de una característica

> ![](image25.webp){width="5.151042213473316in"
> height="0.71875in"}

3.  Realizar cambios y enviar la rama al repositorio remoto

> ![](image37.webp){width="5.244792213473316in"
> height="2.8450010936132983in"}
>
> y al verificar en el repositorio de github
>
> ![](image8.webp){width="3.1093755468066493in"
> height="2.668044619422572in"}

4.  Abrir un Pull Request

> ![](image1.webp){width="4.360073272090989in"
> height="3.0781255468066493in"}

5.  Revisar y fusionar el Pull Request

> ![](image42.webp){width="4.716534339457568in"
> height="2.6011450131233596in"}
>
> Aceptamos el Merge pull request y el merge se hará valido
>
> ![](image35.webp){width="4.807292213473316in"
> height="1.541208442694663in"}

6.  Eliminar la rama remota y local

Para eliminarlo por consola, primero tenemos que hacer un pull para
actualizar los cambios hechos en github

![](image4.webp){width="4.619792213473316in"
height="2.2433552055993in"}

Luego procedemos a eliminar la rama

![](image6.webp){width="5.088542213473316in"
height="0.9382524059492563in"}

Y al verificar las ramas en github solo nos aparecerá la rama main

- Cherry Picking y Git Stash

git cherry-pick: Aplicar commits específicos a otra rama

git stash: Guardar temporalmente cambios no confirmados

1.  Hacer cambios en main.py y confirmarlos

> ![](image13.webp){width="6.267716535433071in"
> height="1.2638888888888888in"}

2.  Crear una nueva rama y aplicar el commit específico

    a.  Creando rama: Como queremos aplicar el mismo commit con
        cherry-pick, verificaremos el listado de commits, y generaremos
        la rama en el commit anterior al de la parte 1, porque si
        hicieramos commit en esa parte, la rama ya tendría el commit

> ![](image7.webp){width="4.932292213473316in"
> height="0.9543318022747157in"}
>
> ![](image5.webp){width="5.817708880139983in"
> height="1.1210203412073492in"}

b.  Ahora para hacer el commit especifico, tomaremos el hash del ultimo
    commit de la rama main, que es cda2651

> ![](image26.webp){width="4.536458880139983in"
> height="1.565838801399825in"}

3.  Guardar temporalmente cambios no confirmados

> ![](image16.webp){width="3.7031255468066493in"
> height="0.6215649606299213in"}
>
> ![](image28.webp){width="5.505208880139983in"
> height="2.3045056867891516in"}
>
> Al aplicar git stash vemos que se guarda y ya no aparece en el main.py
>
> ![](image14.webp){width="5.515625546806649in"
> height="1.74997375328084in"}

4.  Aplicar los cambios guardados

    a.  Con git stash list podemos ver la lista de stash y el primero
        que aparece es la actualización que habíamos hecho en el main.py

> ![](image3.wep){width="5.296875546806649in"
> height="0.6687084426946631in"}

b.  Para recuperar los cambios, lo que hacemos es git stash pop

> ![](image24.webp){width="4.619792213473316in"
> height="2.770340113735783in"}
>
> También lo elimina de la lista y se guarda normal

5.  Revisar el historial y confirmar la correcta aplicación de los
    cambios

    a.  Usando git log revisamos el historial de commits y vemos que
        todo se ha aplicado correctamente

> ![](image40.webp){width="4.963542213473316in"
> height="3.0341918197725284in"}
