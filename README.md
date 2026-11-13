# FinBot

Assistente educacional para aprender conceitos sobre investimentos no Brasil. Este projeto está sendo desenvolvido passo a passo como parte das aulas.

## Links do projeto

| O quê | Link |
|---|---|
| Chat publicado (Streamlit Cloud) | COLE_AQUI_O_LINK_DO_APP_NO_STREAMLIT |
| API publicada (Render) | COLE_AQUI_O_LINK_DA_API_NO_RENDER |
| Documentação da API | COLE_AQUI_O_LINK_DA_API_NO_RENDER/docs |

No plano gratuito, a API "dorme" depois de um tempo sem uso: a primeira pergunta pode demorar cerca de 1 minuto.

## Etapa atual

Na Aula 3, o FinBot utiliza LangGraph com memória de curto prazo (`MongoDBSaver` / checkpointer), memória de longo prazo (perfil do usuário no MongoDB Atlas), histórico de conversas na barra lateral do Streamlit e prompts versionados no Langfuse.

## Requisitos

- Python 3.12+
- Uma chave de API da Groq
- Conta no Langfuse
- Cluster gratuito no MongoDB Atlas

## Como configurar no Windows

Abra o projeto no VS Code e, no terminal integrado, confirme que está na pasta principal `finbot`. Execute os comandos abaixo, um de cada vez:

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements-dev.txt
pip install -r frontend/requirements.txt
Copy-Item .env.example .env
```

Depois, abra o arquivo `.env` no VS Code e preencha `GROQ_API_KEY`, `LANGFUSE_PUBLIC_KEY`, `LANGFUSE_SECRET_KEY` e `MONGO_URL`. Não compartilhe essas chaves e não as coloque neste README.

## Como executar

Com o ambiente virtual ativado e o `.env` configurado:

```powershell
# Publicar prompts no Langfuse
python -m scripts.publicar_prompts

# Iniciar a API FastAPI
uvicorn app.main:app --reload

# Em outro terminal (com .venv ativo), iniciar o front em Streamlit
streamlit run frontend/streamlit_app.py
```

## Como executar os testes

Com o ambiente virtual ativado, rode:

```powershell
pytest -v
```

## Segurança

O arquivo `.env` contém chaves privadas e não deve ser enviado ao GitHub. O arquivo `.env.example` contém apenas o modelo das configurações e pode ser publicado.

## Próximas etapas

Este projeto será ampliado nas aulas seguintes com ferramentas de mercado (Aula 4), RAG (Aula 5) e multiagentes (Aula 6).
