# LMC: Estrutura de Repetição (Somar até Zero)


**Objetivo:** Construir um programa em linguagem Assembly capaz de somar continuamente os números digitados pelo usuário. O ciclo de repetição é encerrado quando o valor `0` é inserido, acionando a condição de parada para exibir na tela a soma total de todos os valores anteriores.

---

### 1. Exemplo de Entrada e Saída (I/O)
Abaixo estão exemplos de como o programa se comporta diante de diferentes entradas, evidenciando o funcionamento do laço de repetição e da regra de parada:

| INPUT (Entradas) | OUTPUT (Saída) | Explicação da Lógica |
| :--- | :--- | :--- |
| `5`, `10`, `3`, `0` | `18` | O programa soma 5 + 10 + 3. Ao identificar a entrada do `0`, o laço é quebrado e o total acumulado (18) é exibido. |
| `7`, `0` | `7` | O programa lê o 7 e soma ao total. Lê o 0, encerra o ciclo e exibe o 7. |
| `0` | `0` | O programa lê o 0 logo na primeira rodada, quebra o laço imediatamente e exibe o valor inicial da variável de soma (0). |

---

### 2. Fluxograma do Algoritmo
O fluxograma abaixo detalha a bifurcação da lógica: o caminho contínuo de soma e salvamento e a rota de desvio ativada pela detecção do zero.

<img width="605" height="674" alt="fluxograma_Problema01 drawio" src="https://github.com/user-attachments/assets/fa4643fb-646b-4f67-91ab-e883bd8facd2" />


---

### 3. Código LMC
O programa utiliza a instrução de desvio condicional `BRZ` para identificar a condição de parada e a instrução `BRA` para manter o fluxo de repetição.

```text
// Programa: Somar números digitados até o usuário digitar 0
// Autor: Jhenyfer Cleire 
// Disciplina: APC_2026.2

loop    INP          // Lê o número digitado e coloca no accumulator
        BRZ fim      // Decisão: se for igual a zero, desvia para o fim
        ADD soma     // Soma o valor do accumulator com o valor da variável soma
        STA soma     // Salva o novo resultado na variável soma
        BRA loop     // Retorna ao início para ler o próximo número

fim     LDA soma     // Carrega o valor total da soma no accumulator 
        OUT          // Mostra o valor da soma na tela
        HLT          // Encerra o programa
        
soma    DAT 0        // A variável soma se inicia igual a zero


// Código sem comentários

loop    INP          
        BRZ fim      
        ADD soma     
        STA soma     
        BRA loop     

fim     LDA soma     
        OUT         
        HLT          
        
soma    DAT 0       
