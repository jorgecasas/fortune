# Fortune

**Fortune** es una pequeña aplicación que coge una frase de un fichero de texto y la saca por pantalla, de forma aleatoria. A continuación se muestran los pasos para que cada vez que se abra un terminal se muestren frases aleatorias de nuestra propia colección.

## Instalación y configuración de fortune
En primer lugar, instalaremos _fortune_:
<code>
sudo apt-get update && sudo apt-get install fortune
</code>

Necesitamos un fichero de texto (por ejemplo, _fortunes-jorgecasas_) en las que escribiremos frases (cuantas más, mejor). Entre frase y frase hay que el símbolo de porcentaje en una línea nueva (_%_). Por ejemplo:

<code>
Everything happens for a reason. Sometimes that reason is that you're stupid and make bad choices.
%
Toda ardilla es voladora si la tiras con suficiente fuerza
%
Software and cathedrals are much the same – first we build them, then we pray 
%
</code>

Este fichero lo guardaremos en el directorio _/usr/share/games/fortunes_, en donde habrá otros ficheros de texto (sin extensión) y otros con extensión _.dat_. Ahora necesitaremos convertir nuestro fichero de texto en _.dat_ para que lo entienda _fortune_. Para ello ejecutamos:
<code>
strfile -c % fortunes-jorgecasas fortunes-jorgecasas.dat
</code>

Ahora, podremos obtener una frase aleatoria escribiendo el siguiente comando (siendo _fortunes-jorgecasas_ el nombre de nuestro fichero de extensión _.dat_):
<code>
fortune fortunes-jorgecasas
</code>

## Configuración de .bashrc para que muestre frases cada vez

En el fichero _~/.bashrc_, al final del todo escribiremos el siguiente código, para sacar la frase en color rojo negrita:
<code>
cli_colorize_normal="$(printf '\033[0m')" # returns to normal
cli_colorize_red="$(printf '\033[0;1;31m')" # set bold red
printf "%s" "$cli_colorize_red" ; fortune fortunes-jorgecasas ; printf "%s" "$cli_colorize_normal";
</code>

Y con esto, una frase nueva cada vez que abras el terminal... 