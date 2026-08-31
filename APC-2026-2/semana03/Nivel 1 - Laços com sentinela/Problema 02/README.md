## Semana 03: LMC - Estrutura de Repetição (Contador até -1)

**Objetivo:** Construir um programa em linguagem Assembly capaz de contar e registrar a quantidade de números inseridos pelo usuário. O ciclo de repetição é encerrado quando o valor `-1` é digitado. Para contornar a limitação da máquina, que só avalia desvios baseados em zero, o algoritmo utiliza o artifício matemático de somar `1` a cada entrada para acionar a condição de parada.

### 1. Exemplo de Entrada e Saída (I/O)
A tabela a seguir ilustra o comportamento do programa e a mecânica do contador ignorando o valor da entrada em si:

| INPUT (Entradas) | OUTPUT (Saída) | Explicação da Lógica |
| :--- | :--- | :--- |
| `10`, `1`, `1`, `-1` | `3` | O programa registra a entrada dos três primeiros números, atualizando o contador. O `-1` quebra o laço e a máquina exibe o total contado (3). |
| `15`, `42`, `-1` | `2` | O programa conta o 15 (contador=1) e o 42 (contador=2). Ao ler -1, encerra o ciclo e exibe o 2. |
| `-1` | `0` | O programa lê o -1 na primeira rodada, quebra o laço imediatamente e exibe o valor inicial da variável do contador, que é zero. |

### 2. Fluxograma do Algoritmo
O diagrama reflete as duas fases de processamento em cada rodada: a via de teste para identificar o gatilho de parada e a via de atualização da variável contadora na memória.

![Fluxograma do Contador](fluxograma_Problema01.drawio)


### 3. Código LMC
O programa faz uso da instrução `BRZ` logo após a soma teste e gerencia a atualização do contador manipulando o Acumulador e a RAM com `LDA` e `STA`.

```text
// Programa: Contador de números digitados até o usuário inserir -1
// Autor: Jhenyfer Cleire Melo dos Santos
// Disciplina: APC_2026.2

loop    INP          // O número digitado entra na "mesa de trabalho"
        ADD soma     // Puxa o '1' da RAM e soma para testar se é -1
        BRZ fim      // Decisão: Se a conta deu zero (era -1), desvia para o fim

        LDA count    // O teste passou. Puxa o contador da RAM
        ADD soma     // Puxa o '1' da RAM e soma com o contador
        STA count    // Guarda o contador atualizado de volta na RAM
        BRA loop     // Retorna ao início para receber o próximo número

fim     LDA count    // Puxa o total final da gaveta da RAM
        OUT          // Exibe na tela o total contado
        HLT          // Encerra a execução da CPU

soma    DAT 1        // Constante usada tanto para teste quanto para contagem
count   DAT 0        // Variável que guarda o registro da contagem