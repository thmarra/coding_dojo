# Desafio 1 - The Goose Game 

https://github.com/claranet-it/goose-game-kata

O Jogo do Ganso é um jogo onde dois ou mais jogadores movem peças em uma pista rolando um dado. O objetivo do jogo é chegar à casa número sessenta e três antes de qualquer outro jogador e evitar obstáculos. ([wikipedia](https://en.wikipedia.org/wiki/Game_of_the_Goose))

## Funcionalidades

### 1. Adicionar jogadores
Como jogador, quero ser adicionado ao jogo para poder jogar.

**Cenários:**
1. Adicionar Jogador

``cucumber

Se não houver nenhum participante,
o usuário digita: "adicionar jogador Pippo"
o sistema responde: "jogadores: Pippo"
o usuário digita: "adicionar jogador Pluto"
o sistema responde: "jogadores: Pippo, Pluto"

``

2. Jogador Duplicado

``cucumber

Se já houver um participante "Pippo"

o usuário digita: "adicionar jogador Pippo"
o sistema responde: "Pippo: jogador já existente"

```

### 2. Mover um jogador
Como jogador, quero mover o marcador no tabuleiro para que o jogo progrida.

**Cenários:**

1. Início

``cucumber

Se houver dois participantes, "Pippo" e "Pluto", na casa "Início",
o usuário digita: "mover Pippo 4, 2"
o sistema responde: "Pippo rola 4, 2. Pippo se move da casa Inicial para a 6"
o usuário digita: "mova Plutão 2, 2"
o sistema responde: "Plutão rola 2, 2. Plutão se move da casa Inicial para a 4"
o usuário digita: "mova Pippo 2, 3"
o sistema responde: "Pippo rola 2, 3. Pippo se move da casa 6 para a 11"

```
### 3. Vitória
Como jogador, eu venço o jogo se parar na casa "63"

**Cenários:**
1. Vitória

```pepino

Se houver um participante "Pippo" na casa "60"
o usuário digita: "mova Pippo 1, 2"
o sistema responde: "Pippo rola 1, 2. Pippo se move da casa 60 para a 63. Pippo vence!!" ```

2. Vencendo com o lançamento exato dos dados
```cucumber

Se houver um participante "Pippo" na casa "60"
o usuário digita: "mover Pippo 3, 2"
o sistema responde: "Pippo rola 3, 2. Pippo se move de 60 para 63. Pippo quica! Pippo retorna para 61"

```
### 4. O jogo lança os dados
Como jogador, quero que o jogo lance os dados para mim para economizar esforço

**Cenários:**

1. Lançamento de dados
```cucumber

Se houver um participante "Pippo" na casa "4"

assumindo que os dados tirem 1 e 2
quando o usuário digita: "mover Pippo"

o sistema responde: "Pippo rola 1, 2. Pippo se move de 4 para 7"

```

### 5. Espaço "6" é "A Ponte"
Como jogador, quando chego à casa "A Ponte", pulo para a casa "12"

**Cenários:**
1. Chegar à "Ponte"

``pepino

Se houver um participante "Pippo" na casa "4"

assumindo que os dados tirem 1 e 1
quando o usuário digitar: "mover Pippo"

o sistema responde: "Pippo rola 1, 1. Pippo se move da casa 4 para a Ponte. Pippo pula para a casa 12"

``

### 6. Se você parar em "O Ganso", mova-se novamente
Como jogador, quando chego a uma casa com a imagem de "O Ganso", avanço novamente pela soma dos dois dados rolados anteriormente

As casas 5, 9, 14, 18, 23 e 27 têm a imagem de "O Ganso"

**Cenários:**
1. Salto Único
```pepino

Se houver um participante "Pippo" na casa "3"

assumindo que os dados tirem 1 e 1
quando o usuário digitar: "mover Pippo"

o sistema responde: "Pippo rola 1, 1. Pippo se move da casa 3 para a 5, O Ganso. Pippo se move novamente e vai para a casa 7"

```