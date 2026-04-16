# Código da Aplicação - Mimo

Esta pasta contém o código-fonte do Mimo.

## Estrutura

```
src/
├── app.py              # Aplicação principal (Streamlit)
└── requirements.txt    # Dependências
```

## Dependências

```
pandas
requests
streamlit
```
## Configurações Necessárias

Para conseguir rodar o código, é preciso:

1. Ter instalado as bibliotecas do `requirements.txt`.
2. Ter instalado o Ollama e o modelo usado `gpt-oss`.

### Instalação das dependêcias

```bash
# Instalar dependências
pip install -r scr/requirements.txt
```

### Instalação do Ollama e do modelo local
A aplicação usa o Ollama para processamento de linguagem natual.

1. Baixe e instale o Ollama em:[https://ollama.com/](https://ollama.com/).
2. Baixe o modelo específico utilizado:

```bash
# Instalar o modelo `gpt-oss` do Ollama
ollama run gpt-oss
```

É possível validar se o modelo `gpt-oss` está disponível locamente com:
```bash
# Teste do modelo `gpt-oss` do Ollama
ollama run gpt-oss "Olá!"
```

## Passo a Passo da Execução

```bash
# Garantir que o Ollama está ativo
ollama serve

# Rodar a aplicação
streamlit run src/app.py
```

## Evidência de Execução

<img width="873" height="776" alt="image" src="https://github.com/user-attachments/assets/9c2675cd-70e7-4f69-837d-db22cd736cfb" />

