# Turma Valinor — sede

Este repositório não tem código. Ele guarda os **acordos de trabalho** da turma e é onde
as cerimônias de sprint acontecem, em forma de issue.

O código vive nos repositórios de cada projeto, e todos eles aparecem num quadro único:

**Quadro da turma:** https://github.com/orgs/mentoria-mithril/projects/6

---

## Como o trabalho anda

Uma sprint dura **uma semana** e vira no dia do encontro. Não existe tarefa que "está
sendo feita" fora do quadro: se não tem card, não existe.

### O quadro

| View | Para quê |
| --- | --- |
| **Backlog** | tudo que ainda não entrou em sprint, agrupado por projeto |
| **Sprint atual** | o Kanban da semana, em colunas de `Status` |
| **Por pessoa** | a mesma sprint, agrupada por responsável — é aqui que se vê quem está com o quê |
| **Roadmap** | as sprints na linha do tempo |

Colunas de `Status`, e o que cada uma quer dizer:

1. **Backlog** — existe, ninguém pegou, não é desta semana.
2. **Sprint backlog** — é desta semana, ainda não começou.
3. **Em progresso** — tem alguém trabalhando **agora**. Card em progresso sem responsável é erro.
4. **Em review** — o PR está aberto esperando revisão.
5. **Bloqueado** — parou por algo fora do seu controle. **Escreva no card o que travou** — bloqueio silencioso é bloqueio que ninguém resolve.
6. **Concluído** — o PR foi mergeado em `dev` e a Definição de Pronto foi cumprida.

Regras de convivência no quadro:

- **Um card em progresso por pessoa.** Se você precisa começar outra coisa, mova a
  primeira de volta ou explique no encontro.
- **Mova o card quando o estado muda, não na véspera do encontro.** O quadro serve para
  quem olha durante a semana.
- Card só entra em `Em progresso` se tiver **critérios de aceite** escritos.

### Do card ao merge

```
issue no quadro
   ↓
feat/<numero-da-issue>-descricao-curta        branch curta, morre em ≤ 3 dias
   ↓  PR
dev                                            branch de integração, é o padrão do repo
   ↓  PR de release
main                                           só recebe release, vinda de dev
```

- Branch a partir de `dev`, nomeada `feat/`, `fix/` ou `refactor/`, começando pelo número
  da issue: `feat/42-entrega-de-desafio`.
- **PR pequeno.** Acima de ~400 linhas alteradas o PR volta sem review — quebre em dois.
- **Duas aprovações: um colega e o mentor.** O review do colega vem primeiro. Não existe
  push direto em `dev` nem em `main`.
- A descrição do PR responde três perguntas: **o que muda, por que, e como testei**.
- `main` só recebe PR vindo de `dev`. Qualquer outra origem é recusada automaticamente.

### Definição de Pronto

Um card só vai para **Concluído** quando **todas** valem:

1. Os critérios de aceite da issue estão atendidos.
2. O PR foi aprovado por um colega **e** pelo mentor, e mergeado em `dev`.
3. Alguém além de quem escreveu rodou e viu funcionando.
4. Se houve uso de IA, quem abriu o PR **sabe explicar cada trecho do código** — e vai
   ser perguntado sobre isso no encontro.

---

## Cerimônia de virada de sprint

Toda semana, no encontro, uma única sessão encadeia três coisas. A issue com o checklist é
aberta automaticamente pelo workflow `cerimonia-de-sprint.yml`, algumas horas antes.

| Momento | Duração | O que acontece |
| --- | --- | --- |
| **Review** | ~20 min | Demo do que ficou pronto. Quem fez mostra funcionando — não mostra código em tela, mostra a coisa rodando. Não vale "está quase". |
| **Retro** | ~15 min | O que ajudou, o que atrapalhou, e **uma** ação concreta com dono e prazo para a próxima sprint. |
| **Planning** | ~25 min | Carry-over do que não fechou, repriorização do backlog com o PO (o mentor) e compromisso da sprint nova. |

O relatório que abre a Review sai de `scripts/github/virada-de-sprint.sh` (no repositório
de material da mentoria): o que fechou, o que não fechou e com quem, o que está bloqueado
e os cards em progresso sem dono.

### O que se espera de cada pessoa na cerimônia

- Chegar com o **próprio** quadro em ordem — não gastar a Review arrumando cards.
- Saber dizer, sem consultar nada, **em que ponto** a sua fatia está.
- Trazer o bloqueio **antes** do encontro, não durante.

---

## Papéis que rotacionam

Trocam a cada sprint, na Planning, e ficam registrados na issue da cerimônia.

- **Tech Lead da semana** — decide os cortes técnicos em disputa e **defende as decisões
  no encontro seguinte**. Não é quem programa mais; é quem responde "por que foi feito assim".
- **Revisor da semana** — revisa pelo menos um PR de cada outra dupla.

---

## Avaliação

A nota é individual e sai do **seu rastro nos repositórios**, não do produto final:

| Eixo | Onde é medido |
| --- | --- |
| Funcionamento | os PRs que você abriu fazem o que prometem, inclusive nos casos de borda |
| Engenharia | o diff dos seus PRs: separação de camadas, teste de verdade, ausência de gambiarra |
| Processo | histórico do git: PRs pequenos e frequentes, commits atômicos, branch curta, review feito nos outros |
| Comunicação | descrição dos seus PRs, qualidade dos reviews que você deixou, defesa técnica no encontro |

Quem não deixa rastro não tem nota — e é por isso que o quadro e o PR não são burocracia.

---

Mentor / Product Owner: [@douglasmeneses](https://github.com/douglasmeneses).
