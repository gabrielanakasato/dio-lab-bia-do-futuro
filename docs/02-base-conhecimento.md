# Base de Conhecimento

## Dados Utilizados

| Arquivo                 | Formato | Utilização no Agente                                                                             |
|-------------------------|---------|--------------------------------------------------------------------------------------------------|
| `gatinhos.json`         | JSON    | Palavras gatilhos das regras de segurança .                                                      |
| `regras_seguranca.csv`  | CSV     | Ações obrigatórias a serem feitas quando determinadas palavras gatilhos são usadas pelo usuário. |
| `metas_existentes.json` | JSON    | Metas que o usuário já possui  .                                                                 |

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

Existem duas possibilidades inserir os dados:
1. Diretamente no prompt (Ctrl + C, Ctrl + V);
2. Carregar os arquivos via código, como no exemplo abaixo em Python:
```python
import pandas as pd
import json

gatilhos = json.load(open('./data/gatilhos.json'))
regras_seguranca = pd.read_csv('./data/regras_seguranca.csv')
metas_existentes = json.load(open('./data/metas_existentes.json'))
```

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

Podemos simplemente colar as informações dos arquivos no nosso prompt para que o Agente tenha o melhor contexto possível.

```
GATILHOS (data/gatilhos.json)
{
  "MERCADO": [
    "dólar", "euro", "cotação", "bitcoin", "selic", "cdi", "câmbio", "moeda"
  ],
  "INVESTIMENTO": [
    "cdb", "ações", "onde investir", "rendimento", "fii", "lci", "lca", "etf", "onde investir", "qual rende mais", "tesouro", "poupança", "onde aplicar"
  ],
  "CONTEUDO_EXTERNO": [
    "livro", "youtube", "curso", "influenciador", "indicação de leitura", "youtuber", "canal", "autor"
  ],
  "SEGURANCA": [
    "senha", "token", "cvv", "cpf", "agência", "documento", "rg", "chave aleatória", "conta corrente", "endereço", "cartão", "login"
  ],
  "LEGAL_JURIDICO": [
    "limpar nome", "justiça", "processo", "advogado", "imposto de renda", "serasa"
  ],
  "RECOMENDACAO_CONSUMO": [
    "nubank", "inter", "itau", "bradesco", "santander", 
    "samsung", "apple", "dell", "hp", "lenovo",
    "qual é melhor", "qual você recomenda", "qual marca", "qual modelo"
  ]
}

REGRAS DE SEGURANÇA (data/regras_seguranca.csv)
categoria;acao_obrigatoria;mensagem_base_mimo
MERCADO;Bloquear busca externa;"Como seu guia de planejamento, eu foco exclusivamente no cálculo do seu esforço mensal baseado em valores fixos. Eu não acompanho oscilações de mercado, cotações de moedas ou taxas. Meu objetivo é ajudar você a organizar o quanto precisa economizar por mês para atingir seu sonho, independentemente das variações externas."
INVESTIMENTO;Recusar indicação de ativos;"Como eu sou um guia de planejamento, meu foco é ajudar você a organizar o 'quanto' e o 'quando'. O 'onde' investir é uma decisão pessoal sua."
CONTEUDO_EXTERNO;Recusar indicação externa e/ou bloquear busca externa;"Para manter nosso foco apenas no seu plano pessoal e matemático, não faço indicações de conteúdos externos. O importante aqui é o hábito que estamos construindo juntos."
SEGURANCA;Emitir alerta de privacidade;"🛑 Pare tudo por um segundo! Como seu guia, a sua segurança é minha prioridade máxima. Nunca solicitarei de dados sensíveis como dados bancários, documentos e senhas. Por favor, mantenha essas informações protegidas e nunca as compartilhe em chats. Vamos continuar focando apenas no planejamento dos valores para sua conquista de forma segura?"
LEGAL_JURIDICO;Declara incompetência jurídica;"Essa é uma dúvida muito importante, mas que foge do meu papel como guia de metas. Questões sobre impostos e legislação mudam muito e são complexas. O ideal é que você consulte especialistas na área jurídica, combinado?"
RECOMENDACAO_CONSUMO;Manter neutralidade técnica.;"Como seu guia financeiro, eu ajudo você a chegar ao valor necessário para atingir sua meta, mas a escolha da marca depende do seu gosto e das suas necessidades."


METAS EXISTENTES (data/metas_existentes.json)
[
  {
    "id": 1,
    "meta": "Celular novo",
    "motivacao": "Em breve meu celular parará de ter atualizações e a bateria está ruim. Preciso dele, pois uso muito no meu trabalho.",
    "valor_total": 7500.00,
    "prazo_meses": 6,
    "valor_acumulado": 5700.00,
    "esforco_mensal": 300.00,
    "prioridade": "Alta"
  },
  {
    "id": 2,
    "meta": "Curso",
    "motivacao": "Certificação para crescimento na carreira",
    "valor_total": 3600.00,
    "prazo_meses": 18,
    "valor_acumulado": 0.00,
    "esforco_mensal": 200.00,
    "prioridade": "Média"
  }
]
```

---

## Exemplo de Contexto Montado

Abaixo está um exemplo do contexto com base nos dados originais da base de conhecimento.

```
GATILHOS
- MERCADO: "dólar", "euro", "cotação", "bitcoin", "selic", "cdi", "câmbio", "moeda"
- INVESTIMENTO: "cdb", "ações", "onde investir", "rendimento", "fii", "lci", "lca", "etf", "onde investir", "qual rende mais", "tesouro", "poupança", "onde aplicar"
- CONTEUDO_EXTERNO: "livro", "youtube", "curso", "influenciador", "indicação de leitura", "youtuber", "canal", "autor"
- SEGURANCA: "senha", "token", "cvv", "cpf", "agência", "documento", "rg", "chave aleatória", "conta corrente", "endereço", "cartão", "login"
- LEGAL_JURIDICO: "limpar nome", "justiça", "processo", "advogado", "imposto de renda", "serasa"
- RECOMENDACAO_CONSUMO: "nubank", "inter", "itau", "bradesco", "santander", "samsung", "apple", "dell", "hp", "lenovo", "qual é melhor", "qual você recomenda", "qual marca", "qual modelo"
[Fim de GATILHOS]

REGRAS DE SEGURANÇA
- MERCADO: Bloquear busca externa
- INVESTIMENTO: Recusar indicação de ativos
- CONTEUDO_EXTERNO: Recusar indicação externa e/ou bloquear busca externa
- SEGURANCA: Emitir alerta de privacidade
- LEGAL_JURIDICO: Declarar incompetência jurídica
- RECOMENDACAO_CONSUMO: Manter neutralidade técnica
[Fim das REGRAS DE SEGURANÇA]

METAS EXISTENTES
Meta 1 - Celular novo
- Motivação: Em breve meu celular parará de ter atualizações e a bateria está ruim. Preciso dele, pois uso muito no meu trabalho.
- Valor Total: R$7.500,00
- Tempo Total (meses): 6
- Valor Acumulado: R$5.700,00
- Esforço Mensal: R$300,00
- Prioridade: Alta

Meta 2 - Curso
- Motivação: Certificação para crescimento na carreira.
- Valor Total: R$3.600,00
- Tempo Total (meses): 18
- Valor Acumulado: R$0,00
- Esforço Mensal: R$200,00
- Prioridade: Média
[Fim das METAS EXISTENTES]
...
```
