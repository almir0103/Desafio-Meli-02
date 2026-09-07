# Challenge 02 - Prompt de IA para Analise de Logs de Infraestrutura

## Objetivo

Criar um prompt reutilizavel para uma IA capaz de analisar o trecho de log fornecido e produzir um diagnostico técnico objetivo e claro:
1. Mensagens de erro, alerta ou comportamento anômalo.
2. Eventos que possam estar relacionados entre si.
3. Possíveis causas do problema.
4. Impactos potenciais para a infraestrutura.
5. Sugestões simples de diagnóstico e correção.

## Estrutura da entrega

| Arquivo | Descricao |
|---------|-----------|
| [`Prompt.md`](./Prompt.md) | Prompt completo, pronto para colar diretamente na IA |
| [`Meli_log.txt`](./Meli_log.txt) | Trecho de log bruto usado como exemplo de entrada |
| [`Resposta_prompt.pdf`](./Resposta_prompt.pdf) | Resposta esperada da IA ao processar o log de exemplo |

## Como usar

1. Copie o conteudo de [`Prompt.md`](./Prompt.md)
2. Cole na interface de uma IA generativa.
3. Substitua `[COLE O LOG AQUI]` pelo log que deseja analisar
4. Envie e analise a resposta

Para validacao, use o log [`Meli_log.txt`](./Meli_log.txt) como entrada e compare com a resposta [`Resposta_prompt.pdf`](./Resposta_prompt.pdf).

`Resposta_prompt.pdf` representa uma análise de referência do `Meli_log.txt`. Ela deve ser utilizada para validar se a resposta gerada identifica os principais  pontos, eventos, hipoteses, relacoes, e ações esperadas. O retorno pode variar de acordo com o motor de IA utilizado, pois diferentes modelos podem expressar corretamente o mesmo diagnostico de diferentes maneiras.

## Sobre o exemplo de log

O log de exemplo simula um cenario real de producao com dois problemas simultaneos:

- **Falha operacional:** timeout de conexao com banco de dados causando erros HTTP 502 no endpoint `/checkout`
- **Atividade suspeita:** tentativas de brute force SSH a partir de um IP externo, com alerta de SYN flood

Esse tipo de cenario e comum em equipes de infraestrutura e exige analise rapida, correlacao de eventos e priorizacao de acoes.

## Justificativa do prompt

O prompt visa simular a metodologia de acompanhamento de um analista senior:

1. **Resumo Geral** — impacto em poucas linhas para uma visao mais gerencial do cenário.
2. **Tabela de eventos** — visao estruturada para triagem rápida (Horario | Evento | Severidade | Explicação).
3. **Correlação dos Eventos** — diferencia os erros por assunto e facilita na identificação de escalabilidade da demanda (se houver).
4. **Possiveis causas** — Sugere sobre o evento qual a possivel causa (via evidencias ou hipoteses) .
5. **Impactos Potenciais para a Infraestrutura** — indica qual impacto o evento gerou.
6. **Sugestões de Correção** — apresenta as sugestões para contorno do cenário.
7. **Conclusão** — traz o resumo de todo o cenario idenfificado no LOG.

### Proteção inclusa no prompt

- Não crie nenhuma informação que não esteja presente no arquivo.
- Em caso de soluções hipotéticas, sinalizar de maneira explicita como "Hipótese"
- Identifique hosts, serviços, usuários, IPs, códigos de erro e mensagens relevantes, preservando dados técnicos importantes, mas sem expor credencias ou senhas caso apareçam no log.
- Caso o log não tenham todas as informações necessárias informe qual outra informação adicional deve ser coletada.

Essas regras tornam o prompt mais seguro onde logs podem conter dados sensiveis.

## Compatibilidade

O prompt foi gerado para modelos de linguagem capazes de seguir instruçoes de forma estruturada e analisar texto técnico.
