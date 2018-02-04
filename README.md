# Integracion de contenido interactivo
### carrusel de imagenes:
Para crear el carrusel hacemos uso de css y una funcion de jquery que realice las siguientes tareas:
1. cuando la pagina haya cargado, ejecuta la funcion. 
2. ocultamos todas las imagenes de la lista
3. mostramos solo la primera imagen
4. guardamos la longitud que tiene la lista ordenada de imagenes
5. creamos la primera posicion desde la cual partir
6. hacemos que al hacer click sobre la flecha izquierda muestre la imagen anterior
7. hacemos que al hacer click sobre la flecha derecha se muestre la siguiente imagen y para ello llamamos a la funcion 'siguiente'
8. hacemos que las imagenes pasen automaticamente
9. creamos la funcion siguiente que haga que las imagenes pase, la creamos a parte ya que es necesario llamarla desde dos lugares

### Efecto al hacer scroll:
Para que la pagina se vea mas vistosa, hemos añadido un efecto al hacer scroll en el index que consiste en hacer aparecer una imagen desde la 
izquierda a la derecha, para ello hemos creado una funcion jquery que se encargue de ello. Tambien mediante css creamos un keyframe que llamamos dentro
de la funcion de jquery que hace que a medida que la imagen se desplaza hacia la derecha gire 360, a medida que a imagen gira aparece un texto.

### menu desplegable lateral:
Para hacer que el menu lateral sea desplegable, creamos la siguiente funcion:

```
$(document).ready(function() {
	$menu = $('#menu').find('ul').find('li');
        //.on("click", 
	$menu.hover(function() {
		$(this).children('ul').stop();
		$(this).children('ul').slideDown();
	}, function() {
		$(this).children('ul').stop();
		$(this).children('ul').slideUp();
	});
    
    
});

```
###Imagenes:
Queremos que al pasar el raton por encima de una imagen nos muestre informacion de esta, para ello usamos efectos css.
1. Creamos un ```<div>``` del mismo tamaño que la imagen con opacidad 0 para que no se vea desde el principio
2. Creamos la etiqueta ```<p>``` que contendrá la informacion de cada imagen.
3. Añadimos iconos de font awesome: 
  * like
  * favoritos
  * comentarios
4. creamos un hover que ponga la opacidad a 0.75 cuando pasemos el raton por encima
Además hemos añadido funcionalidad a los iconos con javascript:
creamos una funcion para cada icono:
* para el icono de like:
Hacemos que si el usuario esta loggueado y pulsa sobre el icono, los likes aumenten en 1
```
function likes(){
    if(obtenerCookie("logueado")=="true"){
        var contador= $("i.fa.fa-heart").html();
        contador=parseInt(contador);
        contador++;
        $("i.fa.fa-heart").text(contador);
      
    }
}
```
* para el icono de favoritos:
Hacemos que si el usuario esta loggueado y pulsa sobre el icono, los favoritos aumenten en 1
```
function favorito(){
    if(obtenerCookie("logueado")=="true"){
        var contador= $("i.fa.fa-star").html();
        contador=parseInt(contador);
        contador++;
        $("i.fa.fa-star").text(contador);
        //$("i.fa.fa-star").css("color", "yellow");
    }
}
```
tambien hacemos que si el usuario pincha sobre la descipcion del producto, le lleve a una pagina donde se muestren los detalles del poducto
donde se muestran:
1. Iconos de:
* likes
* favoritos
* comentarios
* compartir
2. Imagen de producto y su descricion
3. boton de compra
