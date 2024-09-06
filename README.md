
# UFABC ANTLR Custom Language Java Compiler to C

```
Nome: Matheus Araujo
RA: 11201920270
e-mail: matheus.victor@aluno.ufabc.edu.br
```

Este repositório contém o código de um compilador feito para a disciplina de Compiladores 2024 usando Java 11 e ANTLR de uma linguagem customizada que cria saída C usando ANTLR e Java.

## Exemplo:

`CustomLang_input.customlang`:
```
DEF a;
DEF b;
DEF c <- 2.0;
WRITE("Digite o valor de A: ");
READ(a);
WRITE("Digite o valor de b: ");
READ(b);

WRITE("C está predefinido com valor: ", c);

DEF d <- a + b * c;
WRITE("Resultado: ");
WRITE("a + b * c = ", d);
```

Resultado `output.c`:

```
#include <stdio.h>
#include <stdlib.h>

int main() {
double a;
double b;
double c = 2.0;
printf("Digite o valor de A: ");
if (scanf("%lf", &a) != 1) {
    fprintf(stderr, "Error: Invalid input. Expected a decimal number.\n");
    exit(1);
}
printf("Digite o valor de b: ");
if (scanf("%lf", &b) != 1) {
    fprintf(stderr, "Error: Invalid input. Expected a decimal number.\n");
    exit(1);
}
printf("C está predefinido com valor: ""%lf\n", c);
double d = a + b * c;
printf("Resultado: ");
printf("");
printf("a + b * c = ""%lf\n", d);
return 0;
}
```

## Features

- Declaração de variáveis tipo double (`DEF a;`)
- Assignment de variáveis tipo double (`DEF c <- 2.0;`)
- Leitura com  assignment de variáveis tipo double (`READ(a);`)
- Expressões e operações seguindo ordem (`DEF d <- a + b * c;`)
- Print na tela (`WRITE("Result:", d);`)

## Como executar

### 1. Instale o ANTLR:
https://github.com/antlr/antlr4/blob/master/doc/getting-started.md#installation

### 2. Altere o arquivo `CustomLang_input.customlang`:

Exemplo:
```
DEF a;
DEF b;
DEF c <- 2.0;
WRITE("Digite o valor de A: ");
READ(a);
WRITE("Digite o valor de b: ");
READ(b);

WRITE("C está predefinido com valor: ", c);

DEF d <- a + b * c;
WRITE("Resultado: ");
WRITE("a + b * c = ", d);
```

### 3. Execute o compilador para a linguagem:
```
java Compiler CustomLang_input.customlang
```

Isso vai gerar o novo output.c:
```
#include <stdio.h>
#include <stdlib.h>

int main() {
double a;
double b;
double c = 2.0;
printf("Digite o valor de A: ");
if (scanf("%lf", &a) != 1) {
    fprintf(stderr, "Error: Invalid input. Expected a decimal number.\n");
    exit(1);
}
printf("Digite o valor de b: ");
if (scanf("%lf", &b) != 1) {
    fprintf(stderr, "Error: Invalid input. Expected a decimal number.\n");
    exit(1);
}
printf("C está predefinido com valor: ""%lf\n", c);
double d = a + b * c;
printf("Resultado: ");
printf("");
printf("a + b * c = ""%lf\n", d);
return 0;
}
```

### 4. Compile e execute o código gerado:
```
gcc output.c -o output && ./output
```

### 5. Resultado do exemplo:

```
Digite o valor de A: 1
Digite o valor de b: 3
C está predefinido com valor: 2.000000
Resultado: a + b * c = 7.000000
```