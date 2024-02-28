# pdc_reto_3
A continuacion, se mostrara el pseudocodigo y diagrama de flujo de los problemas planteados para este reto
## Numeros primos hasta un natural n (pseudocodigo)
```pseudocode
[Variables]
n : entero 
i : entero
t : entero
Inicio
    i := 2
    t := 2
    Leer n
    Para (i hasta n) hacer
        Para (t hasta i^0.5) hacer
            Mientras (t < i^0.5) hacer
                Si modulo (i,t) == 0 entonces
                    Hay_divisor := verdadero
                    Fin si
                Sino 
                    Si t == (i^0.5)-1 entonces
                        Hay_divisor := falso
                    Sino
                        t = t + 1
                    Fin si
                Fin si
            Fin mientras
        Fin para
        Si Hay_divisor == verdadero entonces
            escribir(i "no es numero primo") 
        Sino
            escribir(i "es numero primo")
        FIn si
    Fin Para
Fin
```
## Numeros primos hasta un natural n (diagrama de flujo / flujograma)
```mermaid
graph TD;
A(inicio)
B[Leer número n]
C[i = 2]
D[t = 2]
E[Hacer lista desde i hasta n]
F[Hacer lista desde t hasta i^0.5]
G{¿i%t = 0?}
H[No es primo]
I{¿t = i^0.5-1?}
J[Es primo]
K{¿i = n?}
L(fin)

A --> B
B --> C
C --> D
D --> E
E --> F
F -- para todo i-->  G
G -- si --> H
G -- no --> I
H --> K
I -- no | t + 1 --> G
I -- si --> J
J --> K 
K -- no | i + 1 --> G
K -- si --> L
```
## Raiz cuadrada de un numero n (pseudocodigo)
```pseudocode
[Variables]
n : entero
raiz_cercana : entero
valor_cercano : entero
divisor : entero
numero_digitos_n : entero
digito_1_n : entero
residuo1 : entero
residuo2 : entero
raiz_n : entero
2_digitos_n : entero
Inicio
    raiz_cercana := 1
    valor_cercano := 1
    divisor := 10
    numero_digitos_n := 1
    leer n
    digito_1_n := n // divisor
    Mientras ( digito_1_n > 1) hacer
        numero_digitos_n = numero_digitos_n + 1
        divisor := divisor * 10
    Fin mientras
    Si numero_digitos_n > 2 entonces
        Si modulo (numero_digitos_n, 2) = 1 entonces
            Mientras (raiz_cercana < (digito_1_n^0.5)) hacer
                Si ((digito_1_n - (raiz_cercana^2)) > 0) entonces
                    raiz_cercana = raiz_cercana + 1
                Finsi
            Fin mientras
            residuo1 := (digito_1_n - (raiz_cercana^2)) * 10^(numero_digitos_n-1) + (n - (digito_1_n * 10 ^(numero_digitos_n-1)))
            Mientras ((((20*raiz_cercana)+valor_cercano)*valor_cercano) < residuo1) entonces
                Si (residuo1 - (((20*raiz_cercana)+valor_cercano)*valor_cercano) > 0) entonces
                    valor_cercano = valor_cercano + 1
                Fin si
            Fin mientras
            residuo2 := residuo1 - (((20*raiz_cercana)+valor_cercano)*valor_cercano)
            raiz_n = ((raiz_cercana * 10)+ valor_cercano) + (residuo2 / 2*raiz_cercana)
        Sino
            2_digitos_n := n // (divisor / 10)
            Mientras (raiz_cercana < (2_digitos_n^0.5)) hacer
                Si ((2_digitos_n - (raiz_cercana^2)) > 0) entonces
                    raiz_cercana = raiz_cercana + 1
                Finsi
            Fin mientras
            residuo1 := (2_digitos_n - (raiz_cercana^2)) * 10^(numero_digitos_n-1) + (n - (2_digitos_n * 10 ^(numero_digitos_n-1)))
            Mientras ((((20*raiz_cercana)+valor_cercano)*valor_cercano) < residuo1) entonces
                Si (residuo1 - (((20*raiz_cercana)+valor_cercano)*valor_cercano)) > 0 entonces
                    valor_cercano = valor_cercano + 1
                Fin si
            Fin mientras
            residuo2 := residuo1 - (((20*raiz_cercana)+valor_cercano)*valor_cercano)
            raiz_n = ((raiz_cercana * 10)+ valor_cercano) + (residuo2 / 2*raiz_cercana)
        Fin si
        Fin mientras
    Sino
        Mientras (raiz_cercana < (n^0.5)) hacer
                    Si ((n - (raiz_cercana^2)) > 0) entonces
                        raiz_cercana = raiz_cercana + 1
                    Finsi
        Fin mientras
        residuo1 := (n - (raiz_cercana^2))
        raiz_n := raiz_cercana + (residuo1 / 2*raiz_cercana)
    Fin si
    escribir("La raiz de " n " es aproximadamente " raiz_n)
Fin
```
## Raiz cuadrada de un numero n (diagrama de flujo / flujograma)
```mermaid
flowchart TD
A(inicio)
B[leer n]
C[raiz_cercana = 1]
D[valor_cercano = 1]
E[divisor = 10]
F[numero_digitos_n = 1]
G[digito_1_n = n//divisor]
H{¿digito_1_n > 1?}
I[numero_digitos_n = numero_digitos_n + 1]
J[divisor = divisor * 10]



K{¿numero_digitos_n > 2?}
L{¿numero_digitos_n % 2 = 1?}
M{¿raiz_cercana < n^0.5?}
N{¿n - raiz_cercana^2 > 0?}
O[raiz_cercana = raiz_cercana + 1]
P[residuo1 = n - raiz_cercana^2]
Q[raiz_n = raiz_cercana + residuo1 / 2*raiz_cercana]



R{¿raiz_cercana < digito_1_n^0.5?}
S{¿digito_1_n - raiz_cercana^2 > 0?}
T[raiz_cercana = raiz_cercana + 1]
U[residuo1 = digito_1_n - raiz_cercana^2 * 10^numero_digitos_n-1 + n - digito_1_n * 10^numero_digitos_n-1]
V{¿20*raiz_cercana + valor_cercano * valor_cercano > 0?}
W{¿residuo1 - 20*raiz_cercana + valor_cercano * valor_cercano < residuo1?}
X[valor_cercano = valor_cercano + 1]
Y[residuo2 = residuo1 - 20 * raiz_cercana + valor_cercano * valor_cercano]
Z[raiz_n = raiz_cercana * 10+ valor_cercano + residuo2 / 2*raiz_cercana]



AA[2_digitos_n = n // divisor / 10]


AB{¿raiz_cercana < 2_digitos_n^0.5?}
AC{2_digitos_n - raiz_cercana^2 > 0?}
AD[raiz_cercana = raiz_cercana + 1]
AE[residuo1 = 2_digitos_n - raiz_cercana^2 * 10^numero_digitos_n-1 + n - 2_digitos_n * 10^numero_digitos_n-1]
AF{¿20*raiz_cercana + valor_cercano * valor_cercano > 0?}
AG{¿residuo1 - 20*raiz_cercana + valor_cercano * valor_cercano < residuo1?}
AH[valor_cercano = valor_cercano + 1]
AI[residuo2 = residuo1 - 20 * raiz_cercana + valor_cercano * valor_cercano]
AJ[raiz_n = raiz_cercana * 10+ valor_cercano + residuo2 / 2*raiz_cercana]


A --> B
B --> C
C --> D
D --> E
E --> F
F --> G
G --> H
H -- si --> I
I --> J 
J --> H



H -- no --> K 
K -- si --> L
K -- no --> M
M -- no --> N
N -- si --> O
O --> M
M -- si --> P
P --> Q



L -- si --> R
R -- no --> S
S -- si --> T
T --> R
R -- si --> U

U --> V
V -- no --> W
W --> X
X --> V
V -- si --> Y
Y --> Z



L -- no --> AA
AA --> AB
AB -- no --> AC
AC -- si --> AD
AD --> AB
AB -- si --> AE
AE --> AF
AF -- no --> AG
AG --> AH
AH --> AF
AF -- si --> AI
AI --> AJ
```
