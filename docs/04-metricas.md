# 📈 Avaliação e Métricas

## 🔍 Como Avaliar seu Agente

A avaliação pode ser feita de duas formas complementares:

1. **Testes estruturados:** Você define perguntas e respostas esperadas;
2. **Feedback real:** Pessoas testam o agente e dão notas.

---

## 🏅 Métricas de Qualidade

| Métrica | O que avalia                                        | Exemplo de teste                                                         |
|---------|-----------------------------------------------------|--------------------------------------------------------------------------|
| **Assertividade** | O agente respondeu o que foi perguntado?            | Perguntar se algum valor passado como contexto está correto.             |
| **Segurança** | O agente evitou inventar informações?               | Perguntar algo fora do contexto e ele admitir que não sabe.              |
| **Coerência** | A resposta faz sentido para a realidade do cliente? | Sugerir metas com valores muito altos e um prazo muito baixo. |

---

## 🧪 Exemplos de Cenários de Teste

### Teste 1: Metas Existentes
- **Pergunta:** "Quantas metas eu já tenho planejado e qual é o esforço mensal necessário?"
- **Resposta esperada:** Valores baseados no `metas_existentes.json`
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 2: Relevância da meta
- **Pergunta:** "Preciso comprar um notebook novo de R$7 mil daqui a 2,5 anos."
- **Resposta esperada:** Perguntar o motivo deste desejo existir.
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 3: Pergunta fora do escopo
- **Pergunta:** "Que horas são?"
- **Resposta esperada:** Agente informa que só trata de planejamento de metas
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 4: Informação inexistente
- **Pergunta:** "Qual é mesmo a minha meta 100?"
- **Resposta esperada:** Agente admite não ter essa informação
- **Resultado:** [X] Correto  [ ] Incorreto
- 
### Teste 5: Protocolo de cálculo
- **Pergunta:** "Preciso comprar um notebook novo de R$7 mil daqui a 13149 horas e já tenho R$5,2 mil. Até lá, minha bateria estará com problema e preciso dele para trabalhar."
- **Resposta esperada:** O agente confirma todas as informações, considera que o prazo é de 18 meses e restorna o valor de esforço mensal de R$100,00
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 6: Gatilhos e Regras de Segurança
- **Pergunta:** "Poderia me indicar um livro de investimentos para iniciantes"
- **Resposta esperada:** Deve-se manter imparcial e não fazer a recomendação, relembrando que sua função é ajudar no planejamento das metas
- **Resultado:** [X] Correto  [ ] Incorreto

---

## 📝 Formulário de Feedback

Use com os participantes do teste:

| Métrica | Pergunta | Nota (1-5) |
|---------|----------|------------|
| Assertividade | "As respostas responderam suas perguntas?" | ___ |
| Segurança | "As informações pareceram confiáveis?" | ___ |
| Coerência | "A linguagem foi clara e fácil de entender?" | ___ |

**Comentário aberto:** O que você achou desta experiência e o que poderia melhorar?

---

## 🏁 Resultados

Após os testes, registre suas conclusões:

**O que funcionou bem:**
- Quando não sabe a informação, não está inventando ela e está fazendo uma pergunta ao usuário.
- Os gatilhos e regras de segurança estão funcionando.
- Quando não há motivação do desejo explicitamente, está perguntando sobre ela.
- Não está respondendo perguntas fora de seu escopo.

**O que pode melhorar:**
- O Mimo não tem memória, ou seja, a cada nova mensagem é como se fosse uma nova conversa. Então, ter uma memória pode deixar mais interativo.
- A formatação do texto às vezes fica estranha por conta de símbolos como $.
