# Apple-Picker

Team: [Joseph Neiva](https://github.com/Neiva04), [Roberto Santos](https://github.com/RobertoSSantos)

Atividade proposta pelo professor Dr. José Grimaldo, para complemento de nota da primeira unidade na matéria de Inteligência Computacional do curso de engenharia da computação do SENAI CIMATEC.

Na atividade, temos de desenvolver um agente autônomo para controlar o slider e obter o maior score.

## Agente Racional

explicação...

## Funcionamento do Código

Maçãs verdes e vermelhas, representadas por objetos nas respectivas cores, caem com velocidade uniforme ao longo do grid. O número e posição dos objetos variam aleatoriamente.

### Sensores

O código possui dois lasers unidirecionais (um horizontal e outro no slider) capazes de identificar dados dos objetos.

* Distância do objeto mais próximo
* Cor do objeto mais próximo
* Identifica quando não existem objetos no alcance

### Atuadores

O slider para a captura dos objetos move-se lentamente ao longo do eixo horizontal do grid, seu movimento tem um limite por ciclo.

### Performance

Para cada objeto capturado:

* verdes: +1 ponto
* vermelhos: -3 pontos

O objetivo final é obter o melhor score.

## Soluções Propostas

Nessa seção estão registradas todas as soluções propostas pela equipe, e caso implementadas, haverá a exolicação geral das funções e localização da branch.

### Solução 1

Explicação teorica da solução...

#### Implementação

* Implementação Localizada na Branch...

##### Função 1

A função 1 realiza...

```
exemplo = "Bill"
print(exemplo)
```

## Referências

algoritmo do elevador e leitura de disco