# Projeto de Semáforo com Arduino Uno

---

## 1. Introdução

Este projeto consiste em uma simulação de semáforo utilizando o Arduino Uno. Ele controla a sequência de um semáforo com as cores vermelha, amarela e verde, alternando-as de acordo com uma temporização específica.

## 2. Componentes Utilizados

| Componente                | Quantidade | Descrição                                                                                              |
|---------------------------|------------|--------------------------------------------------------------------------------------------------------|
| Arduino Uno               | 1          | Plataforma de microcontrolador utilizada para controlar o circuito.                                    |
| LED vermelho              | 1          | LED de cor vermelha.                                                                                   |
| LED amarelo               | 1          | LED de cor amarela.                                                                                    |
| LED verde                 | 1          | LED de cor verde.                                                                                      |
| Resistores                | 3          | Limitam a corrente que passa pelos LEDs, evitando que queimem. Valor típico: 220Ω a 330Ω.             |
| Protoboard                | 1          | Facilita a conexão dos componentes sem a necessidade de solda.                                         |
| Jumpers macho-fêmea       | 6          | Conectam os LEDs e resistores.                                                                         |
| Jumper macho-macho        | 1          | Liga o GND do Arduino à protoboard.                                                                    |
| Molde de sinal de madeira | 1          | Para montagem visual do semáforo, conferindo um visual mais realista ao projeto.                       |


## 3. Montagem do Circuito

1. **Conectando os LEDs**:
   - Insira os LEDs vermelho, amarelo e verde na protoboard. As pernas mais longas dos LEDs são o positivo (anodo) e as mais curtas são o negativo (catodo).
   
2. **Ligando os Resistores**:
   - Conecte um resistor ao anodo de cada LED para limitar a corrente, evitando danos.
   
3. **Conectando ao Arduino**:
   - Conecte a outra ponta dos resistores aos pinos digitais do Arduino:
     - LED vermelho ao pino digital 2.
     - LED amarelo ao pino digital 3.
     - LED verde ao pino digital 4.
   - Conecte todos os catodos dos LEDs ao GND do Arduino utilizando o jumper macho-macho e a protoboard para centralizar as conexões.

## 4. Código Arduino

O código controla o ciclo do semáforo, alternando entre as luzes vermelha, amarela e verde com uma temporização definida.

```cpp
// Definição dos pinos para cada LED
const int vermelho = 2;
const int amarelo = 3;
const int verde = 4;

void setup() {
  // Configura os pinos como saída
  pinMode(vermelho, OUTPUT);
  pinMode(amarelo, OUTPUT);
  pinMode(verde, OUTPUT);
}

void loop() {
  // 6s no vermelho
  digitalWrite(vermelho, HIGH);
  digitalWrite(amarelo, LOW);
  digitalWrite(verde, LOW);
  delay(6000); // 6 segundos

  // 2s no amarelo
  digitalWrite(vermelho, LOW);
  digitalWrite(amarelo, HIGH);
  digitalWrite(verde, LOW);
  delay(2000); // 2 segundos

  // 2s no verde 
  digitalWrite(vermelho, LOW);
  digitalWrite(amarelo, LOW);
  digitalWrite(verde, HIGH);
  delay(2000); // 2 segundos

  // +2s verde
  digitalWrite(vermelho, LOW);
  digitalWrite(amarelo, LOW);
  digitalWrite(verde, HIGH);
  delay(2000); // 2 segundos adicionais

  // 2s no amarelo
  digitalWrite(vermelho, LOW);
  digitalWrite(amarelo, HIGH);
  digitalWrite(verde, LOW);
  delay(2000); // 2 segundos
}
```
## 5. Video de demonstração no YouTube:

Link: https://www.youtube.com/watch?v=UnzogHcp3z4

## 6. Explicação do Funcionamento do Código

1. **Definição dos pinos**:
   - Cada LED é associado a um pino digital no Arduino: vermelho no pino 2, amarelo no pino 3 e verde no pino 4.
   - Essas variáveis armazenam os números dos pinos, tornando o código mais legível.

2. **Função `setup()`**:
   - A função `setup()` é executada uma vez ao iniciar o Arduino e define os pinos dos LEDs como saídas, para que possam ser acionados para acender ou apagar os LEDs.

3. **Função `loop()`**:
   - A função `loop()` executa o ciclo do semáforo continuamente, alternando entre as cores com base nos tempos especificados:
     - **6 segundos no vermelho**: O LED vermelho é aceso enquanto os outros LEDs permanecem apagados.
     - **2 segundos no amarelo**: O LED amarelo é aceso e o vermelho apagado.
     - **2 segundos no verde**: O LED verde é aceso.
     - **+2 segundos no verde**: O LED verde permanece aceso por mais 2 segundos para simular um tempo extra para pedestres atravessarem.
     - **2 segundos no amarelo**: O LED amarelo acende novamente antes de reiniciar o ciclo.
   - Cada mudança de estado é acompanhada por uma função de atraso que espera o tempo especificado antes de passar para o próximo estágio.

## 7. Testes e Ajustes

Para garantir o funcionamento correto do projeto:
- Verifique todas as conexões para garantir que cada LED está no pino correto e possui um resistor.
- Execute o código e observe se o ciclo segue os tempos estabelecidos:
  - Vermelho (6s), Amarelo (2s), Verde (2s), Verde (mais 2s), Amarelo (2s).

## 8. Conclusão

Este projeto oferece uma introdução prática ao uso do Arduino para controlar LEDs em uma sequência lógica, simulando um semáforo. Ele ensina conceitos básicos de programação, temporização e eletrônica.







### Avaliador: Julia Alves de Jesus

| Critério                                                                                                 | Contempla (Pontos) | Contempla Parcialmente (Pontos) | Não Contempla (Pontos) | Observações do Avaliador |
|---------------------------------------------------------------------------------------------------------|--------------------|----------------------------------|--------------------------|---------------------------|
| Montagem física com cores corretas, boa disposição dos fios e uso adequado de resistores                | Até 3              | Até 1,5                            | 3                        |                           |
| Temporização adequada conforme tempos medidos com auxílio de algum instrumento externo                  | Até 3              | Até 1,5                          | 3                        |                           |
| Código implementa corretamente as fases do semáforo e estrutura do código (variáveis representativas e comentários) | Até 3              | Até 1,5                          | 3                        |                           |
| Extra: Implmeentou um componente de liga/desliga no semáforo e/ou usou ponteiros no código | Até 1              |  Até 0,5                         |  1                        | OBS: Extra é colocar o sinal dentro do molde de madeira                           |
|  |                                                             |  | |**Pontuação Total** 10 |


### Avaliador: Fernando Soares de Oliveira

| Critério                                                                                                 | Contempla (Pontos) | Contempla Parcialmente (Pontos) | Não Contempla (Pontos) | Observações do Avaliador |
|---------------------------------------------------------------------------------------------------------|--------------------|----------------------------------|--------------------------|---------------------------|
| Montagem física com cores corretas, boa disposição dos fios e uso adequado de resistores                | Até 3              | Até 1,5                            | 3                        |                           |
| Temporização adequada conforme tempos medidos com auxílio de algum instrumento externo                  | Até 3              | Até 1,5                          | 3                        |                           |
| Código implementa corretamente as fases do semáforo e estrutura do código (variáveis representativas e comentários) | Até 3              | Até 1,5                          | 3                        |                           |
| Extra: Implmeentou um componente de liga/desliga no semáforo e/ou usou ponteiros no código | Até 1              |  Até 0,5                         |  1                        | OBS: Extra é colocar o sinal dentro do molde de madeira                           |
|  |                                                             |  | |**Pontuação Total** 10 |
