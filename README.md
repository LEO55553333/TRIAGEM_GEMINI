# TRIAGEM_GEMINI

Chamada API Gemini para Triagem Processual em Lote

## Instalação

Instale as dependências:

```bash
pip install -r requirements.txt
```

## Configuração da API Key

Crie um arquivo `.env` na pasta raiz `C:\API_gemini` com sua chave de API do Gemini:

```
GEMINI_API_KEY=sua_chave_api_aqui
```

**Importante:** O arquivo `.env` deve estar na pasta raiz junto com o `processo.py`

## Estrutura de Pastas

1. Crie uma pasta chamada `API_Gemini` em `C:`
2. Dentro desta pasta, crie subpastas numeradas:
   - `01`
   - `02`
   - `03`
   - etc.
3. Salve o código Python na pasta raiz `C:\API_gemini`

### Estrutura esperada:

```
C:\API_gemini\
├── processo.py
├── requirements.txt
├── .env
├── 01\
│   ├── prompt.txt
│   └── processo1.pdf
├── 02\
│   ├── prompt.txt
│   └── processo2.pdf
└── 03\
    ├── prompt.txt
    └── processo3.pdf
```

## Configuração por Subpasta

Cada subpasta (`01`, `02`, `03`, etc.) representa uma chamada ao modelo do Gemini.

### Requisitos obrigatórios por subpasta:

- **Um arquivo `prompt.txt`** (com esse nome obrigatoriamente)
  - Este arquivo contém o prompt que será enviado ao LLM
  - Deve ser escrito com os parâmetros da triagem

- **Pelo menos 1 arquivo PDF**
  - Podem ser colocados múltiplos processos
  - **Importante:** Respeitar a janela de contexto do LLM (1 milhão de tokens no Gemini)

## Execução

### Comandos no terminal:

```bash
cd C:\API_gemini
python processo.py
```

## Funcionamento

1. Ao executar `processo.py`, será feita uma chamada API ao Gemini da primeira pasta (`01`)
2. O **prompt** é lido de `prompt.txt`
3. Os **arquivos PDF** dentro da pasta são anexados (ambos compondo o input)
4. A **resposta do Gemini** é salva automaticamente na mesma pasta em um arquivo `.docx`
5. **Um segundo após** a resposta e criação do `.docx`, uma nova chamada é feita para a próxima pasta (`02`)
6. O processo se repete para todas as subpastas existentes

## Classificação Final

Após todas as chamadas individuais:

1. Todos os arquivos `.docx` gerados (potencialmente centenas) podem ser reunidos em uma única pasta
2. Esses arquivos podem se tornar input de uma única chamada final
3. Esta última chamada pode fazer a **classificação única de urgência**

## Notas Importantes

- ⚠️ O arquivo `prompt.txt` é **obrigatório** em cada subpasta
- ⚠️ Respeite o limite de 1 milhão de tokens do Gemini
- ⚠️ Mantenha a estrutura de pastas numeradas (`01`, `02`, `03`...)
- ⚠️ O nome `prompt.txt` não pode ser alterado
