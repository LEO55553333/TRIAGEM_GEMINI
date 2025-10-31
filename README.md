# TRIAGEM_GEMINI
Chamada Api Gemini Para Triagem Processual em Lote
Instale os requirements.txt
Crie uma pasta chamada API_Gemini em C:
Dentro desta pasta crie novas pastas (01, 02, 03, etc.)
Salve o código Python na pasta raiz C:\API_gemini
Cada subpasta (01, 02, 03, etc) representa uma chamada ao modelo do Gemini
Dentro de cada subpasta deve ter um arquivo prompt.txt (com esse nome obrigatoriamente), que será o prompt enviado ao LLM
Dentro de cada subpasta deve ser colocado ao menos 1 processo em arquivo .pdf
Podem ser colocados muitos processos, desde que a janela de contexto do LLM seja respeitado (1 milhão de tokens, Gemini)
Ao executar o arquivo python processo.py no terminal, será feita uma chamada API ao gemini da primeira pasta 01
O prompt é prompt.txt e os .pdfs dentro da pasta serão os 'anexos' (ambos compondo o input). A resposta do gemini será salva automaticamente nesta mesma pasta, em um arquivo .docx.
Um segundo após a resposta do gemini e criação automática do arquivo .docx, será feita uma nova chamada referente à próxima pasta 02
E assim por diante, por quantas subpastas houver. Sempre com mesma estrutura, o prompt.txt deve estar dentro de cada pasta e os pdfs dos processos a serem triados.
O prompt.txt deve ser escrito com os parâmetros da triagem
Depois todos os arquivos .docx (virtualemente podem ser centenas) podem ser reunidos em uma só pasta e se tornarem input de uma única chamada para fazer a classificação única de urgência.

comandos no terminal
cd c:\API_gemini
python processo.py
