# AutoejerciciosconIA
<pre>

	<p align=center>
Tecnológico Nacional de México
Instituto Tecnológico de Tijuana

Departamento de Sistemas y Computación
Ingeniería en Sistemas Computacionales

Semestre:
Agosto - Diciembre 2023

Materia:
Lenguajes de interfaz

Docente:
M.C. Rene Solis Reyes 

Unidad:
2

Título del trabajo:
Ejercicios 2.3 Corridas de programas ARM32

Estudiante:
Marquez Santillan Jose Eduardo 21210395

	</p>

</pre>

<pre>

	<p align=left>
//♦----------------------------------------DOC---------------------------------------------♦

/*
Ejemplos de makeloop para desamblar
Jose Eduardo Marquez Santillan 
9/10/23
*/
//♦----------------------------------------C---------------------------------------------♦
    
    #include <stdio.h>  // Incluyendo el archivo de encabezado de entrada/salida estándar para funciones como printf.

/**
 * Esta función crea un bucle que imprime los números del 1 al n.
 *
 * @param n: Un entero que representa el límite superior del bucle.
 */
void makeLoop(int n) {
    for (int i = 1; i <= n; i++) {
        printf("%d ", i);  // Imprimiendo el número actual.
    }
    printf("\n");  // Imprimiendo una nueva línea después del bucle.
}

int main() {
    int n = 10;  // Ejemplo: Establece el límite superior del bucle en 10.
    printf("Bucle del 1 al %d:\n", n);
    makeLoop(n);  // Llamando a la función makeLoop con el límite superior especificado.
    return 0;
}
      
//♦----------------------------------------ARM---------------------------------------------♦

Disassembly of section .init:
000102ec <_init>:
   102ec:    e92d4008     push    {r3, lr}      ; Prolog: Guarda los registros r3 y lr en la pila.
   102f0:    eb000023     bl      10384 <call_weak_fn>  ; Llama a la función call_weak_fn.
   102f4:    e8bd8008     pop     {r3, pc}      ; Epílogo: Restaura los registros r3 y pc (lr) desde la pila y retorna.

Disassembly of section .plt:
000102f8 <.plt>:
   102f8:    e52de004     push    {lr}          ; Guarda lr en la pila.
   102fc:    e59fe004     ldr     lr, [pc, #4]  ; Carga el valor de lr desde la dirección en pc + 4.
   10300:    e08fe00e     add     lr, pc, lr    ; Suma pc y lr, almacenando el resultado en lr.
   10304:    e5bef008     ldr     pc, [lr, #8]  ; Carga la dirección de la función desde la dirección apuntada por lr + 8.

0001030c <printf@plt>:
   1030c:    e28fc600     add     ip, pc, #0, 12 ; Suma pc y 0, almacenando el resultado en ip.
   10310:    e28cca10     add     ip, ip, #16, 20 ; Suma 16 + 20 a ip (0x10000), almacenando el resultado en ip.
   10314:    e5bcfcf8     ldr     pc, [ip, #3320]! ; Carga la dirección de printf desde la dirección apuntada por ip + 3320.
