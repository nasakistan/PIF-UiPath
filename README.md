# 🧾 Processamento Inteligente de Faturas (UiPath)

Projeto RPA de nível corporativo para extração e validação de dados de notas fiscais em PDF, integrando Inteligência Artificial e revisão humana (Action Center).

---

## ⚡ Como Funciona (Arquitetura)

O sistema é baseado no **REFramework** e dividido em duas etapas principais:

* **1. Dispatcher:** Varre pastas locais e carrega os PDFs na Fila do Orchestrator.
* **2. Performer (O Cérebro):**
* **Extração IA:** Usa OCR e Machine Learning para ler e extrair o Número da Nota, CNPJ e Valor Total.
* **Validação Humana (Action Center):** Se a IA não tiver certeza da leitura (confiança < 80%), o robô "dorme" e envia a nota para um operador humano corrigir manualmente no painel web.
* **Integração API:** Após a aprovação, o robô "acorda", monta um JSON com os dados validados e envia para um sistema externo via Webhook (POST).



---

## 🛠️ Tecnologias e Aprendizados

* **Tech:** UiPath Studio, REFramework, Document Understanding, Action Center e integrações WebAPI.
* **Destaques:** Domínio sobre suspensão e retomada (resume) do robô, mescla condicional de dados da IA com os da revisão humana e requisições HTTP dentro da máquina de estados.

---

## 🚀 Como Executar em 4 Passos

1. **Setup:** Atualize o arquivo `Config.xlsx` com os nomes da sua Fila, Storage Bucket e a Chave de API.
2. **Alimente a Fila:** Execute o `Dispatcher.xaml` para enviar os PDFs de amostra.
3. **Inicie o Processamento:** Execute o `Main.xaml` (Performer).
4. **Supervisione:** Acesse o **Action Center** no Orchestrator e aprove manualmente as extrações que caíram para validação humana.
