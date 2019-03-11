---
layout: post
title:  "Nociones básicas para aprender PHP"
date:   2019-03-11 18:07:01 +0100
categories: jekyll update
---

## Introducción:
	A lo largo de este post puede ver las herramientas necesarias para la utilización de php
y algunas nociones básicas en cuanto a sintaxis para su correcto uso.


### Herramientas necesarias para su uso:

- Linux
```sh
$ sudo apt install apache2 php7.2 php7.2-cli php7.2-common php7.2-mysql libapache2-mod-php7.2
```
- Windows
```sh
https://www.apachefriends.org/es/index.html 
```

### Nociones básicas de PHP
### Comentarios en php:

//comentario o con #
/* comentario bloque */

### Uso de variables
    $variable = "hola"
    $numero = 11;
    echo $variable . "\n";
    echo $numero;
    
### Uso de constantes
```sh
Constante simple:
<?php
    define("nombreconstante","valor");
    define("MI_CONSTANTE","HOLA");

Constante array:
    define("MI_ARRAY", array("2","3");
    $_miconstante = MI_CONSTANTE;
    echo MI_CONSTANTE . "\n";
```
- Las constantes son valores fijos 

### Para mostrar:

    print_r ("valor"); (muestra también arrays)
    echo "valor"; (muestra datos simples)
    
### Operadores
- Operadores lógicos
-- $a and $b (verdadero si $a y $b son verdaderos)
-- $a or $b (verdadero si alguno de los dos es verdadero)
-- $a or $b (verdadero si uno de los dos es verdadero, pero no ambos a la vez)
-- !$a (verdadero si $a es falso)
-- $a && $b (verdadero si $a y $b son verdaderos)
-- $a || $b (verdadero si cualquiera de los dos es verdadero)
- Operadores de asignación:
-- $a = "Uno"; (no se entiende por igual, sino que significa que el operando de la izquierda se asigna el valor del de la derecha)
-- $b = $a (en este caso $b, por ejemplo, valdría Uno)

- Operadores de comparación
-- $a == $b (verdadero si $a es igual a $b)
-- $a === $b (idénticos, además de igual, son del mismo tipo)
-- $a != $b (verdadero si $a es distinto de $b)
-- $a <> $b (verdadero si $a es diferente de $b)
-- $a !== $b (si $a no es igual que $b y además no son del mismo tipo)
-- $a > $b ($a es mayor que $b)
-- $a < $b ($a es menor que $b)
-- $a <= $b (verdadero si $a es menor o igual que $b)
-- $a >= $b (verdadero si $a es mayor o igual que $b)

- Operadores de incremento/decremento
-- ++ $a(Pre-incremento, incrementa $a en uno, y luego retorna $a, lo muestra la próxima vez que aparezca $a y no esa vez que lo hace)
-- $a++ (Post-incremento, retorna $a, y luego incrementa $a en uno)
-- --$a (Pre-decremento, decrementa $a en uno, luego retorna $a, lo muestra en decremento la próxima vez que aparezca $a, no cuando lo hace)
--$a-- (Post-decremento, retorna $a, luego decrementa $a en uno)
```sh
$a = 5
echo "\nincremento\n";
    echo $a . "\n";
    echo $a++ . "\n";
    echo $a . "\n";
    
echo "\nPreincremento\n";
$a = 5
    echo ++$a . "\n";
    echo $a . "\n";
```
- Operadores de string
-- . (con el punto se concatenan cadenas)
-- .= (es el operdor de asignación sobre concatenación)

```sh
<?php
    $a = "juan";
    $b = $a = "lopez";
    
    $c = "Pedro";
    $c .= "García";
    
    echo $b . "\n";
    echo $c . "\n";
    
Solución:
juanlopez
PedroGarcía
```

### Inclusión de páginas PHP:
Esto se hace para que sean más fácilmente modificables y legibles. Hay varias formas de incluirlo:

- include
```sh
    include "script2.php";
    include_once "script2.php"; (una sola vez)
```
- require
```sh
    require "script2.php";
    require_once "script2.php"; (la incluye una sola vez y se encarga de que no esté incluída en otra parte del programa)
```
> Include y require son iguales solo se diferencian en el tipo de error que generan. 
Require indica que el código que se inluye es obligatorio para la ejecución del script y si no se encuentra el archivo dará un error y se parara el script o programa php.
Include indica que el código que se incluye es opcional y si el fichero no se encuentra dará un warning, una advertencia que no existe el fichero que queremos incluir pero el programa seguirá ejecutándose aunque no funcione bien.

### Sessiones y cookies

- Sessiones: Son un conjunto de datos de un usuario que se guardan mientras él permanece en nuestro sitio. Funcionan de una forma similar a las cookies pero las cookies no son aceptadas por todos los usuarios y navegadores y se almacenan en el ordenador del cliente, mientras las sessiones son almacenadas en el servidor:

```sh
   <?php
    session_start();
    $_SESSION['mi_sesion']="valor";

<?php
    session_start();
    $_SESSION['mi_sesion'];
```
 > ¿Cuándo se usan las sesiones?
 · Carrito de compras
 · Control de un usuario registrado

- Cookies 
```sh
   <?php
    setcookie("name","valor");
?>
<a href="otrapagina.php">COOKIES</a>

Otra página
<?php
    echo $_COOKIE['name'];
?>
```
```sh
$nombre = 'usuario';
$valor = 'Homer';
// El tiempo de expiración es en 30 minutos. PHP traduce la fecha al formato adecuado
$expiracion = time() + 60 * 30;
// Ruta y dominio
$ruta = '/cookies/';
$dominio = "prueba.dev";
// Sólo envía la cookie con conexión HTTPs
$seguridad = false;
// Cookie disponible sólo para el protocolo HTTP
$solohttp = true;
setcookie($nombre, $valor, $expiracion, $ruta, $dominio, $seguridad, $solohttp);
echo "Cookie establecida";
```

> Para leer las cookies existe un array llamado $_COOKIE, que se usa para extraer los valores de la cookie:
```sh
$valorCookie = $_COOKIE['usuario'];
echo $valorCookie; // Devuelve: usuario
```


### Arrays
Sirven para ordenar y guardar grupos de datos:
- Arrays (puede contener cualquier tipo de valor en su interior, empiezan por 0)
```sh
    Creación del array:
    $array_1 = array("1","2","3","4", array('juan','diego'));
    $array_2 = array("uno","dos","tres","cuatro");
   
    Ver los elementos del array por pantalla:
    $array_2[1]; (nos da como resultado: dos) 
    print_r (array_1); (muestra el array completo con el otro array dentro)
```
- Arrays asociativos
```sh
    Definición:
    $arra_ass = array(
        '1' => 'valor2',
        '2' => 'valor2',
        '3' => 'valor3',
        '4' => $array_2,
    );
    
    Acceso a través de claves:
    echo $arra_ass[2];
    echo "<pre>"; (para que se vea de forma legible, lo formatea)
    print_r ($arra_ass); (muestra el array completo)
    echo "</pre>"
```
- Funciones de arrays (algunas importantes)
-- is_array ($arra_ass); (indica si lo que hay dentro es un array)
-- array_keys (Devuelve todas las claves del array, en este caso 1,2,3...)

Hay una gran variedad de funciones de arrays.


## Estructuras de control
### If...else
Es una estructura condicional, hace una cosa u otra:

```sh
<?php
    $a = "5";
    $b = "10";
    if ( $a == $b)
    {
        echo "Son iguales";
    }
    elseif ( $a < $b )
    {
        echo "$a es menor que $b";   
    }
    else
    {
        echo "$a es mayor que $b";
    }
?>
```

### While / do ... while

- while (evalúa una expresión mientras sea verdadera sino sale del bucle. No evalúa la expresión si no es verdadero de entrada)
```sh
    $a = 10;
    $b = 5;
    
    while ( $a != $b )
    {
        echo $b . "<br>";
        $b++;
    }
```
- Do ... while (es al reves, primero entra en el bucle y luego te evalúa la expresión (do while en este caso evalúa si es igual y el while evaluaba si era distinto))
 ```sh
    do {
        echo $b . "<br";
        $b++;
    }
    while ( $a == $b );
```

### For
Evalúa una expresión1 mientras la expresión2 es verdadera y la expresión3 se encarga de hacer un incremento o decremento de la expresion1.

```sh
<?php
    for ( $i = 0; $j = 0; $i < 10; $i+=3; $j++ )
    {
        echo $i . "<br>";
    }
```


### Foreach
Se utiliza para recorrer arrays u objetos y tiene dos formas de uso:

```sh
    · Sintaxis:
    foreach (expresion_array as $valor)
        sentencias
    · Ejemplo:
    $arr = array("uno","dos","tres");
    foreach ($arr as $value) {
        echo $value . "<br>";
    }
    
    Sintaxis:
    foreach (expresion_array as $clave => $valor)
        sentencias
    · Ejemplo:
     $arr = array(
     "1" => "uno",
     "2" => "dos",
     "3" => "tres");
     foreach ( $arr as $key => $value) {
        echo $value . "<br>";
        echo $key . " = " . $value . "<br>";
    }
```

> Uso de Break y continue
Break = Finaliza la ejecución de la estructura for, foreach, while, do-while o switch en curso. 
Continue = Se utiliza en estructuras de control para pasar a la siguiente iteracción.
```sh
· Ejemplo de uso de break:
<?php
    for ( $i = 0; $i < 10; $i+=3)
    {
       if ( $i == 5 )
       {
            break;
       }
       echo $i . "<br>";
    }
```

> Dato interesante:
$line = readline();
En $line se almacena todo lo que escribes por la consola hasta finalizar con un intro.

## FORMULARIOS
### GET (muestra los datos por la url)
Esta forma no es muy segura porque se ven todos los datos desde la url. Está mas delimitado en cuanto a caracteres que puedes enviar, archivos no se pueden enviar, datos binarios tampoco:
```sh
index.php:
<!DOCTYPE html>
<html>
<head>
    <tittle></tittle>
</head>
<body>
    <form action=form.php method=get>
        Escriba su nombre<input type="text" name="nombre">
        <input type="submit" name="enviar" value="Enviar">
    </form>
</body>
</html>

form.php donde recibe los datos del formulario:
<?php
echo $_GET ['nombre'];
```
### POST ()
Se pueden enviar archivos, datos binarios y muchas más cosas que con el método GET:
```sh
index.php:
<!DOCTYPE html>
<html>
<head>
    <tittle></tittle>
</head>
<body>
    <form action=form.php method=post>
        Escriba su nombre<input type="text" name="nombre">
        <input type="submit" name="enviar" value="Enviar">
    </form>
</body>
</html>

form.php donde recibe los datos del formulario:
<?php
echo $_POST['nombre'];
```
 [Este ejemplo de formulario tiene un zip llamado Ejemplo_formulario_en_PHP.zip]
 
 ###Subida de ficheros al servidor
 Se va realizar con el método POST porque el método GET no permite subida de ficheros, lo que aparece a continuación, nos crea una caja de texto con la que podemos añadir ficheros:
 ```sh
index.php:
<!DOCTYPE html>
<html>
<head>
    <tittle></tittle>
</head>
<body>
    <form action=form.php method=post enctype="multipart/form-data">
        Escriba su nombre<input type="text" name="nombre">
        Subir fichero<input type="file" name="fichero">
        <input type="submit" name="enviar" value="Enviar">
    </form>
</body>
</html>

form.php donde recibe los datos del formulario:
<?php
echo $_POST['nombre'];
```
[ con esto: method=post enctype="multipart/form-data" le estamos diciendo al servidor que subiremos un fichero]
