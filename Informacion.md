# BORRAR ARCHIVOS
### ➡️ Borrarlo desde Git bash
Ya subiste el archivo → ahora está en el historial de tu repositorio remoto (GitHub).
Si querés eliminarlo de la rama actual:<br>
git pull origin "rama" <br>
git rm "archivo" <br>
git commit -m "Eliminado archivo innecesario" <br>
git push origin "rama" <br>
👉 Eso borra el archivo del proyecto en GitHub (pero igual sigue quedando en el historial anterior).
Si después querés volver a subirlo (con cambios o el mismo archivo):
git add "archivo"<br>
git commit -m "Reagregado archivo"<br>
git push origin "rama"<br>
⚠️ Importante:
Si lo que querés es que no quede rastro en el historial (porque el archivo tenía claves, contraseñas, etc.), 
ahí ya no alcanza con git rm. En ese caso hay que reescribir la historia del repo con algo como git filter-repo
o git filter-branch.
### ➡️ Borrarlo desde el explorador
Cuando lo borrás desde el explorador, Git detecta el cambio automáticamente.
Después tenés que confirmarlo igual con Git:<br>
git status        # vas a ver el archivo como "deleted"<br>
git add .         # agrega el cambio (la eliminación)<br>
git commit -m "Eliminado archivo desde explorador"<br>
git push origin "rama"<br>
👉 O sea, da igual si lo borrás con git rm o manualmente desde el explorador.
La diferencia es solo que git rm hace los dos pasos de una vez (borrar + marcarlo para commit).<br>
✅ Conclusión:
Podés borrarlo desde el explorador tranquilo, no es mala práctica. Solo no te olvides de hacer el add, commit y push después, porque si no GitHub nunca se entera del borrado.
# CREAR UNA RAMA EN GIT HUB Y LUEGO LLEVARLA AL REPO LOCAL
1° Creo la Rama "Ejercicio" desde Git Hub con la opción New Branch<br>
2° En esa rama creo/modifico un archivo y lo commiteo desde la web<br>
Nota: en este ejemplo la rama creada se llama ejercicio
### ➡️ Ahora llevamos esa rama "Ejercicio" a nuestro repo local con Git Bash
#### Pasos en Git Bash:<br>
Pararte en la rama principal (ej. main):<br>
git checkout main<br>
Actualizar la info del remoto (trae la rama que hiciste en GitHub):<br>
git fetch origin<br>
Crear localmente la rama prueba conectada a la de GitHub:
git checkout -b ejercicio origin/ejercicio <br>
👉 Esto hace dos cosas:<br>
Crea la rama prueba en tu PC.<br>
La conecta directamente con la rama ejercicio de GitHub.<br>
(Opcional) Confirmar que quedó vinculada al remoto:<br>
git branch -vv<br>
Vas a ver algo como:<br>
* ejercicio     e680e73   [origin/ejercicio]   mensaje del último commit
<br>
A partir de ahí ya podés seguir trabajando en la rama prueba, modificar archivos en tu PC, hacer commits y subirlos con:<br>
git push origin prueba<br>
<br>
➡️ Importante: Git Bash<br>
<br>
🔹 git checkout -b prueba origin/prueba<br>
<br>
Crea la rama local prueba a partir de la rama remota origin/prueba.<br>
Trae automáticamente el snapshot (estado de los archivos) del último commit de esa rama.<br>
Te deja posicionado en esa rama listo para trabajar.<br>
👉 Es como un pull inicial: no hace falta que después corras git pull, porque ya te bajó lo último de la rama remota en ese momento.<br>
<br>
🔹 git pull<br>
<br>
Solo funciona si ya estás en una rama que está vinculada a un remoto.<br>
Lo que hace es traer cambios nuevos del remoto y mergearlos en tu rama local.<br>
En resumen:<br>
Cuando hacés:
git checkout -b prueba origin/prueba<br>
✅ Ya tenés todo el contenido de la rama remota en tu repo local.<br>
Después solo usarías git pull más adelante si alguien más hace cambios en GitHub y querés actualizarlos en tu local.<br>

# CÓMO HACEMOS PARA BORRAR ESA RAMA SI YA NO VAMOS A USARLA?
1° Después de realizar las modificaciones y commitear desde git hub, hacemos un merge<br>
2° Eliminamos la rama desde Git Hub<br>
3° Actualizamos el repo local y borramos la rama en git bash<br>
### Pasos
1. Merge en GitHub<br>
Cuando hacés el merge de ejercicio → main en GitHub:<br>
Todo el contenido de ejercicio ya se integra en main remoto.<br>
La rama ejercicio se puede borrar directamente desde GitHub (te aparece el botón “Delete branch”).<br>
2. En tu PC (Git Bash)<br>
Si ya no querés tener más la rama local ejercicio:<br>
Cambiá a otra rama (ejemplo main):<br>
git checkout main<br>
Borrá la rama local ejercicio:<br>
git branch -d ejercicio<br>
👉 -d significa “borrar si ya está fusionada con otra rama”.<br>
👉 Si por alguna razón no te deja porque ve commits que no tenés, podés forzar con:
git branch -D ejercicio<br>
También podés borrar la rama remota (si no lo hiciste desde la web):<br>
git push origin --delete ejercicio<br>
#### 🔑 Importante:<br>
No hace falta que hagas git pull antes de borrar, a menos que quieras asegurarte de tener en tu PC el historial más reciente.<br>
La rama se puede borrar igual aunque tu copia local esté desactualizada.<br>


