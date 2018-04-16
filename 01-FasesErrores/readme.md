**Comando 1  cc hello2.c -E -P -o hello2.i**  
*Respuesta en consola>* ninguna  
*Respuesta en carpeta>* genera archivo hello2.i  
*Comparación entre hello2.c y hello2.i>* en .i desaparecieron los comentarios realizados en .c y se enlistan todas las declaraciones de las librerias declaradas con #include.    
**Comando 2 cc hello3.c -E -P -o hello3.i**  
*Respuesta en consola>* ninguna  
*Respuesta en carpeta>* genera archivo hello3.i    
*Comparación entre hello3.c y hello3.i>* Entre hello3.i y hello3.c no hay diferencias (excepto por los comentarios de cabecera que fueron eliminados en hello3.i, pero es un caso particular mio debido a que yo cree a hello3.c así).    
**Comando 3 cc hello3.i -S -o hello3.s**  
*Respuesta en consola>*  
hello3.i: In function 'main':  
hello3.i:4:2: warning: implicit declaration of function 'prontf' [-Wimplicit-function-declaration]  
  prontf("La respuesta es %d\n");  
  ^~~~~~  
hello3.i:4:2: error: expected declaration or statement at end of input  
  
 Retornó un warning por la declaración implicita de la funcion prontf y un error porque nunca se cierra la llave en el programa.
 *Respuesta en carpeta>* No genera archivo hello3.s    
 **Comando 4 cc hello4.c -E -P -o hello4.i**  
 En hello4.c se cerró la llave que faltaba en hello3.c    
 *Resultado>* Genera archivo hello4.i    
 **Comando 5 cc hello4.i -S -o hello4.s**  
 *Resultado>* Debido a que no se hizo ningún cambio con respecto al warning anterior, este se repitió, sin embargo se generó el archivo hello4.s, el cual está en lenguaje de maquina como principal diferencia de los anteriores, siendo muy dificil de leer para una persona.
 hello4.i: In function 'main':    
hello4.i:4:2: warning: implicit declaration of function 'prontf' [-Wimplicit-function-declaration]  
  prontf("La respuesta es %d\n");  
  ^~~~~~    
**Comando 6 cc hello4.s -C -o hello4.o**  
*Resultado>* Se retornó error ya que se está haciendo referencia a una función "prontf", la cual no está definida
C:\Users\Luciano\AppData\Local\Temp\cccLkP8y.o:hello4.i:(.text+0x1c): undefined reference to 'prontf'  
collect2.exe: error: ld returned 1 exit status  
**Comando7 cc hello5.c -E -P -o hello5.i**    
**Comando8 cc hello5.i -S -o hello5.s**  
**Comando9 cc hello5.s -C -o hello5.o**  
**Comando10 cc hello5.o -C -o hello5**  
*Respuesta>* La ejecución de los comandos 7, 8, 9 y 10 da como resultado la generación del archivo que le correspondía a cada uno sin ningún mensaje de advertencia o error. Al ejecutar el hello5.exe generado por el comando10 la respuesta fue: "La respuesta es 44897120". Se debe a que nunca se pasó la variable i como parametro en printf, por lo tanto se imprime cualquier otra cosa que esté en memoria.  
**Comando11 cc hello6.c -E -P -o hello6.i  
Comando12 cc hello6.i -S -o hello6.s  
Comando13 cc hello6.i -c -o hello6.o   
Comando14 cc hello6.o -o hello6**  
*Respuesta>* Los comandos 11, 12, 13, y 14 generan los archivos correspondientes sin ningún error ni advertencia. Al ejecutar hello6.exe la respuesta fue: "La respuesta es 42".  
**Comando15 cc hello7.c -E -P -o hello7.i**  
*Respuesta>* Genera hello7.i sin errores.  
**Comando16 cc hello7.i -S -o hello7.s**  
*Respuesta>* Se genera el archivo hello7.s pero con varios warning porque no se declaró a printf ni tampoco a las librerías que la contienen, resultando ser una declaración implicita de esta función. En una nota en los mensajes de error, aclara que se encuentra en el include studio.h  
hello7.i: In function 'main':  
hello7.i:3:2: warning: implicit declaration of function 'printf' [-Wimplicit-function-declaration]  
  printf("La respuesta es %d\n", i);  
  ^~~~~~  
hello7.i:3:2: warning: incompatible implicit declaration of built-in function 'printf'  
hello7.i:3:2: note: include '<stdio.h>' or provide a declaration of 'printf'  
**Comando17 cc hello7.i -c -o hello7.o**  
*Respuesta>* Igual al caso anterior, se generá el archivo con el mismo warning.
hello7.i: In function 'main':
hello7.i:3:2: warning: implicit declaration of function 'printf' [-Wimplicit-function-declaration]
  printf("La respuesta es %d\n", i);
  ^~~~~~
hello7.i:3:2: warning: incompatible implicit declaration of built-in function 'printf'
hello7.i:3:2: note: include '<stdio.h>' or provide a declaration of 'printf'  
**Comando18 cc hello7.o -o hello7**  
*Respuesta>* Se genera el archivo hello7.exe, sin ningún mensaje. Al ejecutarlo imprime por pantalla "La respuesta es 42" como era deseado.
