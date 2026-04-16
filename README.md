# 💎 Mimo - Guia de Metas Financeiras

Este projeto é o projeto final do **Bootcamp Bradesco - Gen AI & Dados** oferecido pela **DIO**.

## ℹ️ Contexto - Projeto Final

Os assistentes virtuais no setor financeiro estão evoluindo de simples chatbots reativos para **agentes inteligentes e proativos**. Neste desafio, você vai idealizar e prototipar um agente financeiro que utiliza IA Generativa para:

- **Antecipar necessidades** ao invés de apenas responder perguntas
- **Personalizar** sugestões com base no contexto de cada cliente
- **Cocriar soluções** financeiras de forma consultiva
- **Garantir segurança** e confiabilidade nas respostas (anti-alucinação)

---

## 💡O que é o Mimo?

O **Mimo** é um agente educativo especializado em planejamento financeiro pessoal. Ele ajuda a estruturar sua meta financeira com a metodologia SMART (Específica, Mensurável, Atingível, Relevante e Temporal).

**O que o Mimo faz:**

✅ Verifica a importância do seu desejo.

✅ Utiliza apenas as informações passadas a ele.

✅ Calcula o Esforço Mensal (R$) necessário dentro do prazo.

✅ Verifica se é o Esforço Mensal (R$) está dentro da sua realidade.

**O que o Mimo NÃO faz:**

❌ Não faz recomendação de investimentos.

❌ Não faz recomendações de produtos específicos.

❌ Não acessa dados bancários reais e sensíveis.

❌ NÃO acompanha oscilações de mercado ou taxas.

❌ NÃO considera juros ou rendimentos nos cálculos.

## 🏗️ Arquitetura

```mermaid
flowchart TD
    A[Usuário] -->|Mensagem| B[Interface]
    B --> C[Agente LLM]
    C --> D[É de cálculo?]
    D --> |Sim| E[Função Matemática Exata]
    D --> |Não| F[Base de Conhecimento]
    E --> G[Validação]
    F --> G
    G --> H[Resposta]
```

**Stack**

| Componente | Descrição                         |
|------------|-----------------------------------|
| Interface | Streamlit                         |
| LLM | Ollama com modelo local `gpt-oss` |
| Dados | Arquivos JSON e CSV  mockados     |

## 📁 Estrutura do Projeto

```
├── 📄 README.md
│
├── 📁 data/                          # Base de Conhecimento
│   ├── gatilhos.json                 # Palavras gatilhos das regras de segurança (JSON)
│   ├── metas_existentes.json         # Metas que o usuário já possui (JSON)
│   └── regras_segurancao.csv         # Ações obrigatórias quando palavras gatilhos são usadas pelo usuário (CSV)
│
├── 📁 docs/                          # Documentação do projeto
│   ├── 01-documentacao-agente.md     # Detalhamento do Mimo
│   ├── 02-base-conhecimento.md       # Estratégia de dados
│   ├── 03-prompts.md                 # System prompt e exemplos
│   ├── 04-metricas.md                # Avaliação de qualidade
│
└── 📁 src/                           # Código da aplicação
    └── README.md                     # README do código
    └── app.py                        # Aplicação streamlit
    └── requirements.txt              # Dependências necessárias
```

## 🚀 Como Executar

### 1. Instalar Ollama

Ollama está disponível em:[https://ollama.com/](https://ollama.com/).

### 2. Instalar modelo local

```bash
ollama run gpt-oss
```

### 3. Instalar as dependências

```bash
pip install -r scr/requirements.txt
```

### 4. Ativar Ollama

```bash
ollama serve
```

### 5. Rodar a aplicação

```bash
streamlit run src/app.py
```

## 🎯 Exemplo de Uso

### Exemplo 1
**Usuário**: 

**Mimo**: 

## 📈 Métricas de Avaliação

| Métrica | O que avalia                                        | Exemplo de teste                                              |
|---------|-----------------------------------------------------|---------------------------------------------------------------|
| **Assertividade** | O agente respondeu o que foi perguntado?            | Perguntar se algum valor passado como contexto está correto.  |
| **Segurança** | O agente evitou inventar informações?               | Perguntar algo fora do contexto e ele admitir que não sabe.   |
| **Coerência** | A resposta faz sentido para a realidade do cliente? | Sugerir metas com valores muito altos e um prazo muito baixo. |

## 🎬 Diferenciais

- **100% local**: usa o Ollama sem enviar dados para APIs externas.
- **Relevância do desejo**: garante que o desejo é relevante e não um impulso.
- **Seguro**: estratégias de anti-alucinação documentadas

## 📝 Documentação Completa
Toda a documentação técnica, estratégias de prompt e casos de teste estão disponíveis na pasta `docs/`.