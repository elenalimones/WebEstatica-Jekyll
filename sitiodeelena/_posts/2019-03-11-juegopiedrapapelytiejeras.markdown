---
layout: post
title:  "Aprende a crear el juego de Piedra, Papel o Tijeras"
date:   2019-03-11 18:07:01 +0100
categories: jekyll update
---


Aclaración previa: Recuerde darle como nombre Metodopost.pl y Metodoget.pl

## Haciendo uso del método GET

```sh
#!/usr/bin/perl
print "Content-Type: text/html; charset=utf-8\n\n";

@pairs = split(/&/, $ENV{QUERY_STRING});


#Contador para controlar la obtención de valores nombre y elección
$count = 0;

foreach $pair (@pairs) {
	if( $count eq 0 ) {
    
		($name, $value) = split(/=/, $pair);
		 $value =~ tr/+/ /;
		 $value =~ s/%(..)/pack("C", hex($1))/eg;
		@jugador1 = ($name,$value);
		$count = $count +1;

    }
   
	if( $count eq 1 ) {
    
		($name, $value) = split(/=/, $pair);
		 $value =~ tr/+/ /;
		 $value =~ s/%(..)/pack("C", hex($1))/eg;
		@jugador2 = ($name,$value);
    }
    
}

#Creación de la variable de la que obtengo la hora exacta en la que ocurre el juego
($sec,$min,$hora,$mday,$mes,$Y,$wday,$syday,$isdst) = localtime(time);

#Para configurar el formato de la fecha de forma personalizada
@meses= qw(Ene Feb Mar Abr May Jun Jul Ago Sep Oct Nov Dec);
@dias= qw(Domingo Lunes Martes Miércoles Jueves Viernes Sábado);
$fecha= "$dias[$wday] $mday de $meses[$mes] de $Y, $hora:$min:$sec";


#Creacion de un hash haciendo uso del simbolo => para establecer la clave/valor:
%valores = ( 'piedra' => 'tijera', 'papel' => 'piedra', 'tijera' => 'papel' );


if($jugador1[1] eq $jugador2[1]) {
  print("$jugador1[0] y $jugador2[0] han empatado","\n");
  open (T, '>>', '/tmp/datosjuego');
  print T "Jugadores: $jugador1[0] y $jugador2[0]:$fecha: Empate\n";
  close (T);

}

if($valores{$jugador1[1]} eq $jugador2[1]) {
  print("Ha ganado $jugador1[0]","\n");
  open (T, '>>', '/tmp/datosjuego');
  print T "Jugadores: $jugador1[0] y $jugador2[0]: $fecha: Ganador:$jugador1[0]\n";
  close (T);
  }

if($valores{$jugador2[1]} eq $jugador1[1]) {
 print("Ha ganado $jugador2[0]","\n");
 open (T, '>>', '/tmp/datosjuego');
 print T "Jugadores: $jugador1[0] y $jugador2[0]:$fecha: Ganador:$jugador2[0]\n";
 close (T);
  }

``` 


# ¿Quiere poner a prueba su funcionamiento usando el método GET?
curl -G "http://localhost/cgi-bin/Recuperacionelena.pl?elena=piedra&juanito=papel"


## Haciendo uso del método POST

```sh
#!/usr/bin/perl
print "Content-Type: text/html; charset=utf-8\n\n";

#Para hacer uso del método POST:
$datos = <STDIN>;

@pairs = split(/&/, $datos );


#Contador para controlar la obtención de valores nombre y elección
$count = 0;

foreach $pair (@pairs) {
	if( $count eq 0 ) {
    
		($name, $value) = split(/=/, $pair);
		 $value =~ tr/+/ /;
		 $value =~ s/%(..)/pack("C", hex($1))/eg;
		@jugador1 = ($name,$value);
		$count = $count +1;

    }
   
	if( $count eq 1 ) {
    
		($name, $value) = split(/=/, $pair);
		 $value =~ tr/+/ /;
		 $value =~ s/%(..)/pack("C", hex($1))/eg;
		@jugador2 = ($name,$value);

    }
    
}

#Creación de la variable de la que obtengo la hora exacta en la que ocurre el juego
($sec,$min,$hora,$mday,$mes,$Y,$wday,$syday,$isdst) = localtime(time);

#Para configurar el formato de la fecha de forma personalizada
@meses= qw(Ene Feb Mar Abr May Jun Jul Ago Sep Oct Nov Dec);
@dias= qw(Domingo Lunes Martes Miércoles Jueves Viernes Sábado);
$fecha= "$dias[$wday] $mday de $meses[$mes] de $Y, $hora:$min:$seg";


#Creacion de un hash haciendo uso del simbolo => para establecer la clave/valor:
%valores = ( 'piedra' => 'tijera', 'papel' => 'piedra', 'tijera' => 'papel' );


if($jugador1[1] eq $jugador2[1]) {
  print("$jugador1[0] y $jugador2[0] han empatado","\n");
  open (T, '>>', '/tmp/datosjuego');
  print T "Jugadores: $jugador1[0] y $jugador2[0]:$fecha: Empate\n";
  close (T);

}

if($valores{$jugador1[1]} eq $jugador2[1]) {
  print("Ha ganado $jugador1[0]","\n");
  open (T, '>>', '/tmp/datosjuego');
  print T "Jugadores: $jugador1[0] y $jugador2[0]: $fecha: Ganador:$jugador1[0]\n";
  close (T);
  }

if($valores{$jugador2[1]} eq $jugador1[1]) {
 print("Ha ganado $jugador2[0]","\n");
 open (T, '>>', '/tmp/datosjuego');
 print T "Jugadores: $jugador1[0] y $jugador2[0]:$fecha: Ganador:$jugador2[0]\n";
 close (T);
  }

close F;
```


# ¿Quiere poner a prueba su funcionamiento usando el método POST?
	curl -d "elena=papel&juanito=tijera" http://localhost/cgi-bin/Metodopost.pl
