# 📘 Caderno Temático: Fundamentos e Conceitos Básicos do n8n
Caderno temático sobre Fundamentos e Conceitos Básicos do n8n criado com NotebookLM para o bootcamp Santander 2026 da DIO.
> Projeto desenvolvido como parte do Desafio de Projeto **"Treinando uma IA de Aprendizagem: Explore o Poder do NotebookLM"** no Bootcamp Santander 2026 - Automação com N8N da [DIO](https://dio.me).

## 🎯 Objetivo
Este repositório reúne um Caderno Temático estruturado com o suporte do **NotebookLM** (IA de aprendizagem do Google), focado em organizar o conhecimento sobre os conceitos base da ferramenta de automação **n8n**.



## 🧠 Aprendizagem Ativa com NotebookLM
Para construir este material:
1. **Curadoria de Fontes:** Seleção de documentações e materiais introdutórios sobre n8n.
2. **Análise com IA:** Utilização do NotebookLM para sintaxe de dados, geração de resumos e perguntas frequentes.
3. **Organização:** Estruturação do conhecimento para consulta rápida durante o bootcamp.



## 📚 Conteúdo do Caderno Temático
### 1. O que é o n8n?
O **n8n** é uma plataforma de automação de fluxos de trabalho (*workflow automation platform*) e integração de sistemas baseada no conceito *Node-to-Node* (nó para nó). Ele permite conectar diferentes aplicativos, serviços e APIs de maneira visual e intuitiva.

A plataforma funciona em um modelo **no-code / low-code**: possibilita criar automações sem a necessidade de escrever código, ao mesmo tempo em que oferece suporte a scripts em **JavaScript** ou **Python** para personalizações e transformações lógicas complexas.

---

### Como o n8n Funciona: Arquitetura e Componentes

O funcionamento do n8n baseia-se em uma arquitetura visual modular e orientada a eventos:

1. **Workflows (Fluxos de Trabalho)**:
   * É a sequência completa de passos criada na interface visual (**Canvas** ou Editor) para automatizar um processo do início ao fim.

2. **Nodes (Nós)**:
   * São os blocos fundamentais de construção das automações. Dividem-se principalmente em:
     * **Trigger Nodes (Gatilhos)**: O ponto de partida obrigatório que determina quando o fluxo deve ser executado. Podem ser disparados por ações manuais (**Manual Trigger**), horários programados (**Schedule/Cron Trigger**), chamadas recebidas em tempo real de APIs externas (**Webhook Trigger**) ou consultas periódicas (**Polling Trigger**).
     * **Action Nodes / Regular Nodes**: Processam, filtram, transformam, consultam ou enviam informações para serviços externos (como Google Sheets, Gmail, Slack, WhatsApp, e-commerces e CRMs).
     * **Code Node**: Permite executar lógicas em JavaScript (Node.js) ou Python nativo para manipulação avançada de dados.
     * **Cluster Nodes e Sub-nós**: Estruturas que combinam um nó raiz com sub-nós para expandir funcionalidades especializadas, como ferramentas e agentes de inteligência artificial.

3. **Fluxo de Dados (*Data Flow*) e Estrutura de Itens**:
   * Os dados fluem de nó em nó organizados em uma estrutura chamada **Items**.
   * Cada item é estruturado contendo a propriedade `json` (para dados em texto/objeto) e, quando aplicável, a propriedade `binary` (para arquivos e mídias em Base64).

4. **Mapeamento de Dados e Expressões**:
   * O n8n utiliza **Expressões** com sintaxe de chaves duplas `{{ ... }}` para passar informações dinamicamente entre os nós (por exemplo, `{{$json.campo}}` ou `{{$node["Nome do Nó"].json.campo}}`).
   * Para facilitar o desenvolvimento, a plataforma dispõe do recurso de **Data Pinning**, que permite "congelar" dados de teste em um nó sem precisar refazer requisições a serviços externos.

5. **Credenciais**:
   * Armazenam de forma segura e criptografada as informações de autenticação (chaves de API, senhas, tokens OAuth 2.0 e segredos) usadas para conectar aos aplicativos.

6. **Subworkflows (Sub-fluxos)**:
   * Permitem que um fluxo principal acione um fluxo secundário usando o nó *Execute Sub-workflow*, favorecendo a modularização e o reuso de automações.

---

### Modelos de Implantação e Licenciamento

* **Auto-hospedado (*Self-Hosted*) vs. Nuvem Oficial (*n8n Cloud*)**: O n8n pode ser utilizado tanto no serviço gerenciado em nuvem quanto em infraestrutura própria (auto-hospedado via Docker ou servidor VPS). A versão *self-hosted* garante total privacidade dos dados, previsibilidade de custo e flexibilidade para liberar importações de bibliotecas externas no nó *Code*.
* **Licença de Uso Sustentável (*Sustainable Use License / Fair-Code*)**: O código do n8n é disponibilizado de forma gratuita para **uso pessoal ou automações de processos internos da própria empresa**. Apenas se a empresa comercializar o n8n como um serviço para terceiros (*Commercial License*) ou embarcar a ferramenta dentro de um software próprio (*Embed License*), torna-se necessária uma licença comercial paga.

---

### 2. Conceitos Fundamentais
Os três conceitos fundamentais que estruturam o funcionamento do n8n são o **Workflow**, o **Node** e o **Trigger**.

---

### 1. Workflow (Fluxo de Trabalho)
* **O que é**: É a automação completa, ou seja, o mapa com a sequência encadeada de passos criada no editor visual (*canvas*) para automatizar um processo do início ao fim.
* **Em palavras simples**: O **Workflow** é a **receita completa** da sua automação. Ele reúne todas as etapas necessárias para conectar sistemas e fazer o trabalho repetitivo por você.

---

### 2. Node (Nó)
* **O que é**: São os blocos individuais de construção que compõem o workflow. Cada nó tem uma função específica no fluxo, como buscar informações, transformar ou filtrar dados, tomar decisões lógicas ou enviar ações para serviços externos (como Google Sheets, Gmail ou Slack).
* **Em palavras simples**: Os **Nodes** são as **peças de Lego** ou as etapas individuais do processo. Conforme você conecta um nó ao outro, as informações passam de etapa em etapa.

---

### 3. Trigger (Gatilho)
* **O que é**: É um nó especial posicionado no início do workflow que serve para disparar e começar a execução da automação quando um evento ou condição específica acontece. Todo fluxo em produção precisa de pelo menos um gatilho para determinar quando deve rodar.
* **Em palavras simples**: O **Trigger** é o **interruptor** ou o alarme de partida da sua automação.
* **Exemplos de gatilhos**:
  * **Manual Trigger**: acionado manualmente por você clicando num botão (ideal para criar e testar).
  * **Schedule Trigger**: acionado em horários ou frequências programadas (como rodar automaticamente todo dia às 8h).
  * **Webhook Trigger**: acionado no exato momento em que um sistema externo envia dados ao n8n em tempo real.
  * **Polling Trigger**: consulta uma aplicação de tempos em tempos para checar se houve novidades.

---

### 3. FAQ para Iniciantes
Aqui está um FAQ com as **5 perguntas e respostas mais comuns** para quem está começando no n8n:

---

### 1. O que é o n8n e para que ele serve?
O **n8n** é uma plataforma de automação de fluxos de trabalho (*workflow automation*) e integração de sistemas baseada no conceito *Node-to-Node* (nó para nó). Ele serve para conectar diferentes aplicativos, serviços e APIs (como Google Sheets, Gmail, Slack, Telegram, WhatsApp e e-commerces) para executar tarefas repetitivas em segundo plano 24 horas por dia. A ferramenta combina uma interface visual intuitiva do tipo *no-code / low-code* com a flexibilidade de adicionar lógicas personalizadas em JavaScript ou Python quando necessário.

---

### 2. O que são Workflow, Node e Trigger no n8n?
Estes são os três conceitos estruturais fundamentais da plataforma:
* **Workflow (Fluxo de Trabalho):** É a receita ou sequência visual completa criada no editor (*canvas*) para automatizar um processo do início ao fim.
* **Node (Nó):** São as etapas ou blocos individuais que compõem o workflow. Cada nó executa uma função específica, como buscar dados, filtrar informações, realizar cálculos ou enviar dados para um aplicativo externo.
* **Trigger (Gatilho):** É um nó especial posicionado no início do fluxo que funciona como o "interruptor" para disparar a automação. Pode ser acionado por uma ação manual (*Manual Trigger*), por horários programados (*Schedule Trigger*), pelo recebimento de dados em tempo real (*Webhook Trigger*) ou por checagem periódica (*Polling*).

---

### 3. Preciso saber programar para usar o n8n?
**Não obrigatoriamente.** O n8n foi projetado para permitir que usuários sem conhecimento em programação criem automações complexas apenas arrastando nós, conectando blocos e mapeando campos através da interface gráfica. No entanto, para desenvolvedores ou cenários avançados que exigem manipulação técnica de dados, o nó **Code** permite escrever scripts em JavaScript ou Python para personalizar o fluxo.

---

### 4. Qual é a diferença entre n8n Cloud e n8n Self-Hosted (Auto-hospedado)?
* **n8n Cloud:** É o serviço gerenciado em nuvem (*SaaS*) oficial mantido pela própria equipe do n8n. É ideal para quem deseja começar rapidamente sem configurar infraestrutura, mas possui limites de execuções dependendo do plano e restrições na importação de bibliotecas externas no nó Code.
* **n8n Self-Hosted:** É a versão instalada no seu próprio servidor ou VPS (geralmente via Docker). Garante total privacidade dos dados, custo fixo imprevisível em escala (sem cobrança por quantidade de execuções de workflows) e liberdade para habilitar a importação de módulos externos de JavaScript e Python no nó Code.

---

### 5. O n8n é gratuito? Como funciona a sua licença?
**Sim, para a imensa maioria do uso interno.** O n8n opera sob a **Sustainable Use License** (baseada no modelo *fair-code*). Essa licença permite usar a versão auto-hospedada de forma totalmente gratuita e ilimitada para fins pessoais ou para automação de processos internos da sua própria empresa. O pagamento de uma licença comercial (como *Commercial License* ou *Embed License*) só é necessário caso você venda o n8n como um serviço pago para terceiros ou o embarque diretamente dentro de um produto de software.

---


## 🛠️ Ferramentas Utilizadas
- **[NotebookLM](https://notebooklm.google.com/):** Assistente de pesquisa e organização com IA.
- **[n8n](https://n8n.io/):** Plataforma de automação de fluxo de trabalho.
- **GitHub:** Hospedagem do portfólio e documentação.

  ## ✒️ Autor
Desenvolvido por **Moisés Lima** durante a jornada no Santander Bootcamp 2026.
