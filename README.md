# 🐾 Gatou Dessa pra Melhor — Gestão Centralizada

![Status do Projeto](https://img.shields.io/badge/Status-Conclu%C3%ADdo-brightgreen)
![Python](https://img.shields.io/badge/Python-3.8+-blue)
![CustomTkinter](https://img.shields.io/badge/UI-CustomTkinter-purple)
![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL%20(Aiven)-blue)

O **Gatou Dessa pra Melhor** é um sistema desktop moderno e intuitivo desenvolvido em Python para o gerenciamento centralizado e registro de óbitos felinos. Com uma estética voltada para o *Dark Mode* roxo, o aplicativo oferece uma interface amigável para funerárias pet ou clínicas veterinárias organizarem dados de tutores, gatinhos e homenagens pós-vida.

---

## 📸 Interface do Aplicativo

Substitua o caminho abaixo pela imagem real do seu aplicativo rodando:

<img width="1917" height="991" alt="image" src="https://github.com/user-attachments/assets/ac635e60-a8e5-4527-9326-3abe2dc75892" />

*Painel de controle com abas para visualização de registros e formulário de cadastro.*

---

## ✨ Funcionalidades

* **Painel de Registros (Tabela):** Listagem em tempo real de todos os felinos registrados utilizando o componente `Treeview` totalmente estilizado para o tema escuro.
* **Registrar Novo Óbito (Formulário):** Tela dedicada para a inserção de novos registros com validação de campos obrigatórios.
* **Controle Lúdico de Vidas:** Menu dinâmico para selecionar quantas das 7 vidas o felino gastou antes de partir.
* **Persistência em Nuvem:** Integração direta com banco de dados PostgreSQL hospedado na plataforma Aiven.
* **Sincronização Automática:** Atualização imediata dos dados na tabela após novos cadastros ou por meio do botão manual de atualização.

---

## 🛠️ Tecnologias Utilizadas

* **[Python](https://www.python.org/):** Linguagem base do projeto.
* **[CustomTkinter](https://github.com/TomSchimansky/CustomTkinter):** Biblioteca de UI para criação de interfaces modernas em Dark Mode.
* **[Tkinter (ttk)](https://docs.python.org/3/library/tkinter.html):** Componentes adicionais e estilização de tabelas de dados.
* **[psycopg2](https://www.psycopg.org/):** Adaptador de banco de dados PostgreSQL para Python.
* **[PostgreSQL (Aiven)](https://aiven.io/):** Banco de dados relacional hospedado na nuvem.

---

## 🚀 Como Executar o Projeto

### Pré-requisitos
Antes de começar, certifique-se de ter o Python instalado em sua máquina e uma instância do PostgreSQL (como no Aiven) configurada com as tabelas correspondentes.

### 1. Clonar o Repositório

git clone [https://github.com/seu-usuario/gatou-dessa-pra-melhor.git](https://github.com/seu-usuario/gatou-dessa-pra-melhor.git)
cd gatou-dessa-pra-melhor
#2. Instalar as Dependências
Instale as bibliotecas necessárias utilizando o pip:

Bash
pip install customtkinter psycopg2-binary
#3. Configurar o Banco de Dados
No código fonte do arquivo principal, localize os métodos carregar_dados e salvar_dados. Substitua os campos vazios dentro de psycopg2.connect pelas suas credenciais reais do painel Aiven:

Python
conn = psycopg2.connect(
    host="seu-host.aivenblog.com",
    database="seu_banco",
    user="seu_usuario",
    password="sua_senha",
    port="sua_porta"
)
⚠️ Nota de Segurança: Nunca envie suas credenciais reais para repositórios públicos do GitHub! Use variáveis de ambiente em projetos de produção.

#4. Rodar o Aplicativo
Bash
python seu_arquivo.py
🗄️ Estrutura do Banco de Dados (SQL sugerido)
Para que o aplicativo funcione perfeitamente, o seu banco de dados precisa ter uma estrutura semelhante a esta:

SQL
CREATE TABLE clientes (
    id SERIAL PRIMARY KEY,
    nome_dono VARCHAR(255) NOT NULL
);

CREATE TABLE gatos (
    id SERIAL PRIMARY KEY,
    cliente_id INT REFERENCES clientes(id) ON DELETE CASCADE,
    nome_gato VARCHAR(255) NOT NULL,
    data_falecimento DATE,
    idade_no_falecimento VARCHAR(100),
    vidas_gastas INT,
    causa_morte VARCHAR(255),
    lembranca_escolhida VARCHAR(255)
);
#✒️ Autor
Desenvolvido por walinhos.
