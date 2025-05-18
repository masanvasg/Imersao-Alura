# Imersao-Alura
Projeto de Chatbot Coolab/Phyton em console. Coleta dados para personalização. Usa a IA generativa Gemini  para sugerir tópicos de conversa e interagir em uma dinâmica de perguntas e respostas. e finaliza quando o usuário digita "fim".

Meu primeiro chatbot (QUE LEGAL)

Um chatbot simples em Python que usa IA para conversar com o usuário, personalizando a interação e sugerindo tópicos.

Descrição Detalhada

Este projeto implementa um chatbot interativo que roda diretamente no console/terminal. Ele foi desenvolvido em Python/Coolb e utiliza um modelo de inteligência artificial generativa (como a API do Google Gemini) para criar respostas dinâmicas.

O bot inicia a interação coletando algumas informações básicas do usuário, como nome, idade, ocupação e o estilo de conversa preferido (informal, acadêmico, formal). Essas informações são usadas para tentar personalizar a experiência.

Em um momento chave da conversa, o chatbot emprega a IA para sugerir tópicos de conversa que podem ser relevantes para o perfil do usuário. O usuário pode então escolher um desses tópicos ou iniciar um diálogo livre com suas próprias perguntas.

A conversa continua em um formato de perguntas e respostas, onde o usuário digita sua mensagem, o bot a envia para a IA e exibe a resposta, até que o usuário decida encerrar a interação digitando a palavra "fim".

Funcionalidades

* Coleta inicial de informações do usuário (nome, idade, ocupação, estilo).
* Personalização básica da interação com base nos dados do usuário.
* Utiliza IA generativa para sugerir tópicos de conversa.
* Diálogo contínuo de perguntas e respostas com a IA.
* Opção para encerrar a conversa a qualquer momento ("fim").
* (Opcional: Adicione aqui outras funcionalidades específicas se tiver)

Tecnologias Utilizadas

Python ([Versão que você usou, ex: 3.9])
Biblioteca `google-generativeai` (para interação com a API Gemini)
Biblioteca `python-dotenv` (recomendado para gerenciar chaves de API - veja Configuração)
API de um modelo de IA Generativa (Ex: Google Gemini)
Notebook Colab

Pré-requisitos

Para rodar este projeto localmente, você precisará ter instalado:

Python 3.6 ou superior
pip (gerenciador de pacotes do Python)

Instalação

Siga os passos abaixo para obter e configurar o projeto:

1.  Clone este repositório para sua máquina local:
    ```bash
    git clone https:Projeto.ipynb
    ```
2.  Navegue até o diretório do projeto:
    ```bash
    cd Imersão-Alura
    ```
3.  Instale as dependências necessárias. Se você gerou um arquivo `requirements.txt` (com `pip freeze > requirements.txt`), use:
    ```bash
    pip install -r requirements.txt
    ```
    Caso contrário, instale manualmente as bibliotecas principais:
    ```bash
    pip install google-generativeai python-dotenv
    ```

Configuração da Chave da API

Este projeto precisa de uma chave de API para se comunicar com o modelo de IA. É “fortemente recomendado” não incluir sua chave diretamente no código por motivos de segurança, especialmente se o repositório for público.

1.  Obtenha sua chave de API no Google AI Studio (https://aistudio.google.com/) ou plataforma equivalente.
2.  Crie um arquivo no diretório raiz do projeto chamado `.env`.
3.  Dentro do arquivo `.env`, adicione a seguinte linha (substitua `SUA_CHAVE_DA_API_AQUI` pela sua chave real):
    ```dotenv
    GEMINI_API_KEY=SUA_CHAVE_DA_API_AQUI
    ```
4.  No topo do seu arquivo Python principal (`seu_script.py`), adicione o código para carregar a chave da variável de ambiente antes de configurar a API:
    ```python
    import os
    from dotenv import load_dotenv
    import google.generativeai as genai

    # Carrega as variáveis do arquivo .env
    load_dotenv()

    # Configura a API com a chave
    API_KEY = os.getenv('GEMINI_API_KEY')
    if not API_KEY:
        print("Erro: Chave da API GEMINI_API_KEY não encontrada nas variáveis de ambiente ou no arquivo .env.")
        print("Por favor, crie um arquivo .env com GEMINI_API_KEY=SUA_CHAVE.")
        exit() # Sai do programa se a chave não for encontrada

    genai.configure(api_key=API_KEY)

    # Inicializa o modelo e o chat
    model = genai.GenerativeModel('gemini-pro') # Use o nome do modelo correto
    chat = model.start_chat(history=[])
    ```
Nota: Adapte o nome da variável de ambiente (`GEMINI_API_KEY`) e a forma de configurar a API (`genai.configure`) se estiver usando uma API diferente da Google Gemini)*

Como Rodar

Execute o script principal a partir do terminal na pasta do projeto:

```bash
python [nome_do_seu_arquivo_principal.py]

