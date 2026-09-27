# Inverted Classroom

Este repositório reúne duas skills que refletem duas partes do fluxo: uma conduz o aprendizado; a outra ajuda a criar e aperfeiçoar skills por meio de testes e avaliação.

## Skills

### `inverted-classroom`

Local: `.agents/skills/inverted-classroom/SKILL.md`

É uma abordagem de estudo liderada pelo aluno e baseada em tentar primeiro. Em vez de começar com uma aula expositiva ou receber respostas prontas, o aluno recupera o que já sabe, pratica e explica seu raciocínio. O tutor observa as tentativas, identifica lacunas e então oferece perguntas, dicas e explicações direcionadas.

O curso é adaptado ao objetivo, ao conhecimento prévio, ao tempo disponível e à profundidade desejada. Antes de criar materiais, a skill coleta essas informações e confirma onde os arquivos poderão ser criados. Depois, organiza um percurso com módulos pequenos, exercícios autorais, revisões espaçadas e um registro durável do progresso e dos equívocos a revisitar.

**Fluxo de aprendizagem**

1. Definir objetivo, ponto de partida, tempo, profundidade e pasta de destino.
2. Confirmar o plano e criar um espaço de curso organizado e navegável.
3. Tentar responder perguntas de recuperação e previsão antes de consultar a explicação.
4. Resolver exercícios próprios — incluindo tarefas de programação quando pertinentes — e executar verificações que não contenham a solução.
5. Conversar sobre o raciocínio, testar a compreensão em novos exemplos e receber primeiro dicas, depois explicações quando necessário.
6. Registrar evidências, dúvidas e conceitos frágeis; programar revisitas e adaptar o próximo módulo ao que foi demonstrado.

A conclusão não é determinada por ter lido uma página ou passado em testes isolados: exige explicar a ideia e transferi-la para outro contexto. A intenção é construir competência duradoura, não apenas cobrir conteúdo.

### `skill-creator`

Local: `.pi/skills/skill-creator/SKILL.md`

Ajuda a criar skills novas ou melhorar skills existentes. A skill trata a criação como um ciclo iterativo: entender a intenção e quando a skill deve ser acionada, escrever uma versão inicial, testá-la com pedidos realistas, comparar resultados e revisá-la com base em evidências e feedback humano.

**Fluxo de criação e melhoria**

1. Esclarecer o que a skill deve permitir fazer, em que situações deve ser usada e qual resultado se espera.
2. Escrever ou revisar as instruções, mantendo clara a finalidade e os critérios de acionamento.
3. Preparar casos de teste representativos; quando apropriado, comparar execuções com e sem a skill (ou com a versão anterior).
4. Avaliar os resultados com critérios verificáveis e análise qualitativa, observando também tempo, uso de tokens e padrões entre casos.
5. Apresentar os resultados para revisão humana, incorporar o feedback e repetir o ciclo enquanto houver melhorias úteis.
6. Opcionalmente, otimizar a descrição para melhorar quando a skill é acionada e empacotá-la para distribuição.

A intenção é evitar escrever instruções e presumir que funcionam. A skill propõe validar o comportamento em situações concretas, envolver a pessoa usuária na avaliação e melhorar de forma geral — sem ajustar as instruções excessivamente a um único exemplo.

## Como as duas se complementam

A `inverted-classroom` aplica um método de aprendizagem: tentativa, prática, explicação guiada e revisita. A `skill-creator` aplica um método de desenvolvimento: intenção, rascunho, avaliação, feedback e iteração. Ambas priorizam participação ativa e evidências; nenhuma deve confundir exposição ao material com domínio ou uma primeira versão com resultado validado.

## Estrutura

```text
.agents/skills/inverted-classroom/SKILL.md
.pi/skills/skill-creator/SKILL.md
README.md
```

Cada `SKILL.md` contém as instruções completas da respectiva skill.