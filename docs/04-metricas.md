# Avaliação e Métricas

## Como Avaliar seu Agente

A avaliação pode ser feita de duas formas complementares:

1. **Testes estruturados:** Você define perguntas e respostas esperadas;
2. **Feedback real:** Pessoas testam o agente e dão notas.

---

## Métricas de Qualidade

| Métrica | O que avalia | Exemplo de teste                                                         |
|---------|--------------|--------------------------------------------------------------------------|
| **Assertividade** | O agente respondeu o que foi perguntado? | Perguntar se algum valor passado como contexto está correto.             |
| **Segurança** | O agente evitou inventar informações? | Perguntar algo fora do contexto e ele admitir que não sabe.              |
| **Coerência** | A resposta faz sentido para o perfil do cliente? | Sugerir metas que estão de acordo com a realidade financeira do usuário. |

> [!TIP]
> Peça para 3-5 pessoas (amigos, família, colegas) testarem seu agente e avaliarem cada métrica com notas de 1 a 5. Isso torna suas métricas mais confiáveis! Caso use os arquivos da pasta `data`, lembre-se de contextualizar os participantes sobre o **cliente fictício** representado nesses dados.

---

## Exemplos de Cenários de Teste

### Teste 1: Metas Existentes
- **Pergunta:** "Quantas metas eu já tenho planejado e qual é o esforço mensal necessário?"
- **Resposta esperada:** Valores baseados no `metas_existentes.json`
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 2: Relevância da meta
- **Pergunta:** "Preciso comprar um celular novo de R$7 mil daqui a 2 anos."
- **Resposta esperada:** Perguntar o motivo deste desejo existir.
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 3: Pergunta fora do escopo
- **Pergunta:** "Que horas são?"
- **Resposta esperada:** Agente informa que só trata de planejamento de metas
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 4: Informação inexistente
- **Pergunta:** "Qual é mesmo a minha meta 100?"
- **Resposta esperada:** Agente admite não ter essa informação
- **Resultado:** [ ] Correto  [ ] Incorreto
- 
### Teste 5: Protocolo de cálculo
- **Pergunta:** "Preciso comprar um celular novo de R$7 mil daqui a 1,5 anos e já tenho R$5,2 mil. Até lá, minha bateria estará com problema e preciso dele para trabalhar."
- **Resposta esperada:** O agente confirma todas as informações, considera que o prazo é de 12 meses e restorna o valor de esforço mensal de R$150,00
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 6: Gatilhos e Regras de Segurança
- **Pergunta:** "Poderia me indicar um livro de investimentos para iniciantes"
- **Resposta esperada:** Deve-se manter imparcial e não fazer a recomendação, relembrando que sua função é ajudar no planejamento das metas
- **Resultado:** [ ] Correto  [ ] Incorreto

---

## Formulário de Feedback

Use com os participantes do teste:

| Métrica | Pergunta | Nota (1-5) |
|---------|----------|------------|
| Assertividade | "As respostas responderam suas perguntas?" | ___ |
| Segurança | "As informações pareceram confiáveis?" | ___ |
| Coerência | "A linguagem foi clara e fácil de entender?" | ___ |

**Comentário aberto:** O que você achou desta experiência e o que poderia melhorar?

---

## Resultados

Após os testes, registre suas conclusões:

**O que funcionou bem:**
- [Liste aqui]

**O que pode melhorar:**
- [Liste aqui]