# - Simulação de Escalonamento Round Robin

Este projeto simula o algoritmo de escalonamento **Round Robin** para processos, com a inclusão de trocas de contexto. O objetivo principal é calcular o tempo de vida, tempo de espera e o tempo total de execução dos processos, considerando a implementação do algoritmo de escalonamento preemptivo.

## Descrição

O código implementa a simulação do escalonador Round Robin, onde um conjunto de processos é executado em ordem cíclica, com cada processo recebendo uma fatia de tempo (`quantum`). Se um processo não terminar dentro dessa fatia, ele é interrompido e adicionado novamente ao final da fila para ser executado posteriormente. O código também conta o tempo de espera e o tempo de vida de cada processo.

### Estruturas de Dados

A estrutura `Processo` contém as seguintes informações:

- `id`: Identificador único do processo.
- `tempo_execucao`: Tempo total de execução do processo.
- `tempo_restante`: Tempo restante para a execução do processo.
- `tempo_inicio`: Tempo de início da execução do processo.
- `tempo_termino`: Tempo em que o processo termina a execução.
- `tempo_chegada`: Tempo de chegada do processo no sistema.

### Funções

1. **ordenar_por_chegada(Processo processos[], int num_processos)**
   - Função que ordena os processos com base no tempo de chegada, para garantir que os processos sejam executados na ordem de chegada.

2. **verificar_e_adicionar_troca_contexto(Processo fila[], int fila_inicio, int fila_fim, int tempo_total, int troca_contexto)**
   - Função que verifica se é necessário adicionar o tempo de troca de contexto, com base no número de processos na fila e no parâmetro `troca_contexto`.

3. **round_robin(Processo processos[], int num_processos, int quantum, int troca_contexto)**
   - Função que implementa o algoritmo de escalonamento Round Robin. Ela gerencia o tempo de execução dos processos, calcula o tempo de vida e de espera, e imprime o resultado de cada processo.

### Variáveis

- **tempo_vida[]**: Vetor que armazena o tempo de vida de cada processo.
- **tempo_espera[]**: Vetor que armazena o tempo de espera de cada processo.
- **fila_inicio**: Índice da primeira posição na fila de processos.
- **fila_fim**: Índice da última posição na fila de processos.
- **total_trocas**: Contador do número de trocas de contexto realizadas durante a execução.

### Cálculos Realizados

- **Tempo de Vida**: O tempo de vida de cada processo é calculado como a diferença entre o tempo de término e o tempo de chegada.
- **Tempo de Espera**: O tempo de espera de cada processo é calculado como o tempo de vida menos o tempo de execução do processo.
- **Tempo Total**: O tempo total de execução é calculado levando em consideração o tempo de execução de todos os processos, incluindo as trocas de contexto.

## Execução

No código, são definidos quatro processos com os seguintes dados de exemplo:

```c
Processo processos[] = {
    {1, 10, 10, -1, 0, 5},  
    {2, 30, 30, -1, 0, 15},
    {3, 20, 20, -1, 0, 10},
    {4, 40, 40, -1, 0, 0} 
};
