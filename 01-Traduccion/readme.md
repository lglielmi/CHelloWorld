**Comando 1**  cc hello2.c -E -P -o hello2.i  
*Respuesta en consola>* ninguna  
*Respuesta en carpeta>* genera archivo hello2.i  
*Comparación entre hello2.c y hello2.i>* en .i desaparecieron los comentarios realizados en .c y se enlistan todas las declaraciones de las librerias declaradas con #include.  
**Comando 2** cc hello3.c -E -P -o hello3.i  
*Respuesta en consola>* ninguna  
*Respuesta en carpeta>* genera archivo hello3.i    
*Comparación entre hello3.c y hello3.i>* Entre hello3.i y hello3.c no hay diferencias (excepto por los comentarios de cabecera que fueron eliminados en hello3.i, pero es un caso particular mio debido a que yo cree a hello3.c así).  
**Comando 3** cc hello3.i -S -o hello3.s
*Respuesta en consola>*  
hello3.i: In function 'main':  
hello3.i:4:2: warning: implicit declaration of function 'prontf' [-Wimplicit-function-declaration]  
  prontf("La respuesta es %d\n");  
  ^~~~~~  
hello3.i:4:2: error: expected declaration or statement at end of input  
  
 Retornó un warning por la declaración implicita de la funcion prontf y un error porque nunca se cierra la llave en el programa.
 *Respuesta en carpeta>* No genera archivo hello3.s
 **Comando 4** cc hello4.c -E -P -o hello4.i
 En hello4.c se cerró la llave que faltaba en hello3.c  
 *Resultado>* Genera archivo hello4.i
 **Comando 5** cc hello4.i -S -o hello4.s
 *Resultado>* Debido a que no se hizo ningún cambio con respecto al warning anterior, este se repitió, sin embargo se generó el archivo hello4.s
 hello4.i: In function 'main':  
hello4.i:4:2: warning: implicit declaration of function 'prontf' [-Wimplicit-function-declaration]  
  prontf("La respuesta es %d\n");  
  ^~~~~~  
