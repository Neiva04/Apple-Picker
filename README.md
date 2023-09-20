# Apple-Picker

Team: [Joseph Neiva](https://github.com/Neiva04), [Roberto Santos](https://github.com/RobertoSSantos)

Atividade proposta pelo professor Dr. José Grimaldo, para complemento de nota da primeira unidade na matéria de Inteligência Computacional do curso de engenharia da computação do SENAI CIMATEC.

Na atividade, temos de desenvolver um agente autônomo para controlar o slider e obter o maior score.

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

Nessa seção estão registradas todas as soluções propostas pela equipe, e caso implementadas, haverá a explicação geral das funções.

### Solução 1 - Movimento Eterno

Nessa solução, buscamos movimentar o slider por toda a tela e ele capturar as maçãs durante o movimento.

##### Função eternal_movement

Responsável por movimentar o slider ao longo da tela a partir de um inidicador direcional para sabermos se vai para a esquerda ou direita.

```
def eternal_movement(self, current_pos):
        # Calculate the new position
        new_pos = current_pos + self.direction * self.max_lever_displacement
        
        # Check for borders
        if new_pos <= 0:  # Left border
            new_pos = 0
            self.direction = 1  # Change direction to right
        elif new_pos >= self.arena_width - lever_width:  # Right border
            new_pos = self.arena_width - lever_width
            self.direction = -1  # Change direction to left
        
        return new_pos
```

### Solução 2 - Seguir lista 

Nessa solução, o slider se movia de acordo com os elementos de uma lista de maçãs

#### Função enqueue_apple

Essa função lista as maças verdes na ordem em que são detectadas, localizada na classe de Modelo de Mundo

'''
from collections import deque

class WorldModel:
    def __init__(self):
        self.queue = deque()

    def enqueue_apple(self, apple):
        # Only enqueue green apples
        if apple[2] == good_apple_color:
            self.queue.append(apple[0])  
'''

### Solução Final - Verde Mais Próximo

Nessa solução, mantemos um movimento eterno controlado, inciamos com esse pardrão de movimentação, porém, conforme as maçãs são detectadas pelo scanner o slider para e aguarda a colisão

#### Função decision

a função decision é responsável por todo movimento do slider nessa solução.

'''
def decision(self, lever_pos, laser_scan, side_laser_scan, score):
         # If there's a green apple in the laser range, move towards it
        if laser_scan and laser_scan["color"] == "green":
            apple_x_position = closest_apple[0]
            if apple_x_position > lever_pos + lever_width/2:
                return min(lever_pos + self.max_lever_displacement, self.arena_width - lever_width)
            elif apple_x_position < lever_pos + lever_width/2:
                return max(lever_pos - self.max_lever_displacement, 0)
        
        # For now, just use the eternal_movement method to decide the lever's position
        desired_lever_pos = self.eternal_movement(lever_pos)
        return desired_lever_pos
'''
