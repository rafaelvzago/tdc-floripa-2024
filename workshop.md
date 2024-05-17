## Visão Geral do Laboratório

Este laboratório demonstrará como a combinação de diversas tecnologias de Inteligência Artificial/Aprendizado de Máquina (IA/ML) pode gerar uma solução valiosa para um problema de negócio. As informações, códigos, modelos e técnicas apresentados ilustram como um primeiro protótipo poderia ser desenvolvido, e não representam a única forma de atender aos requisitos estabelecidos.

### Aviso Legal

Este laboratório é um exemplo do que um cliente pode construir utilizando o OpenShift AI. O OpenShift AI não possui recursos específicos relacionados ao Processamento de Sinistros de Seguro.

O laboratório utiliza modelos de linguagem de grande porte (LLM) e modelos de processamento de imagens. Esses modelos não estão incluídos no produto OpenShift AI e são fornecidos apenas para fins de demonstração neste laboratório.

A qualidade dos modelos é suficiente para um protótipo. A escolha do modelo ideal para um ambiente de produção é uma tarefa complexa que exige experimentação e ajustes, aspectos que não serão abordados neste laboratório.

## Estrutura do Workshop

| Nome             | Duração | Tipo                     | Descrição                                                                                                                  |
| ---------------- | ------- | ------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| Contexto         | 5       | Apresentação             | Descreveremos o estado final desejado, a experiência do usuário e a arquitetura subjacente. Utilizaremos mockups para melhor visualização. |
| Conexão e Setup  | 10      | Hands-On                 | Os participantes se conectarão, validarão o ambiente e configurarão o projeto.                                             |
| LLM              | 20      | Hands-On                 | Verificaremos o resumo, o sentimento e a comparação de modelos, além de realizar exercícios de prompt engineering e validação do pipeline.       |
| Processamento de Imagem | 20      | Hands-On                 | Realizaremos verificações de reconhecimento de carros, exercícios de retreinamento e implantação de modelos.                     |
| Web App          | 20      | Hands-On                 | Implantaremos e atualizaremos o aplicativo web.                                                                             |
| Produtização      | 5       | Apresentação + Discussão | Discutiremos quais recursos poderiam agregar valor e quais outras ações poderiam ser realizadas seguindo os mesmos padrões.               |

## Cenário

Somos uma grande seguradora multinacional em processo de transformação digital, buscando modernizar práticas e utilizar novas tecnologias. Uma pequena equipe foi incumbida de analisar o processo atual de sinistros e propor melhorias.

As descobertas serão apresentadas à diretoria e, se convincentes, a equipe receberá recursos para implementar as recomendações. As próximas seções deste capítulo apresentam os materiais que foram apresentados à diretoria.

## Análise do Processo Atual de Sinistros

Os sinistros podem ser recebidos por diversos canais (email, fax, telefone, formulário web), mas todos precisam ser transcritos para o formulário web para padronização.

O processamento é feito por peritos (humanos), que levam em média 7 horas por sinistro. Estima-se que erros humanos causem perdas de US$ 2,5 milhões/ano, e fraudes, mais US$ 3,5 milhões/ano.

Existem muitas ineficiências, como a "fadiga por carga de trabalho", que leva os peritos a cometerem erros devido à natureza repetitiva do trabalho. Além disso, o treinamento de novos peritos nas políticas específicas da empresa é demorado.

Codificar parte desse conhecimento em um software é altamente desejável.

## Melhorias Propostas

**Recomendações:**

* Implementação progressiva e gradual.
* Utilizar ferramentas e técnicas de IA/ML para auxiliar os peritos (em vez de substituí-los completamente).
* Oferecer suporte para tarefas repetitivas e de baixo nível.
* Identificar áreas que precisam de revisão.
* Ajudar na análise e extração de dados.

**Objetivos:**

* Reduzir o tempo médio de processamento de 7h/sinistro para 2h/sinistro.
* Reduzir o erro humano em 80%.
* Melhorar a detecção de fraude em 25%.

**Requisitos:**

* Medir o desempenho com mais precisão, tanto no início quanto após cada mudança/melhoria.

## Exemplos do Trabalho de Prototipagem

Os exemplos abaixo ilustram o que esperamos alcançar com a versão protótipo do processo aprimorado.

### Utilizando um LLM para Resumo de Texto

Permite uma leitura mais rápida pelo perito.
[Image of text summary LLM]

 A imagem demonstra como um modelo de linguagem (LLM) pode resumir um e-mail longo e confuso de um cliente sobre um acidente de carro em um formato claro e conciso. Isso permite que o perito de seguros compreenda rapidamente os detalhes-chave do acidente (data, local, danos, testemunhas), agilizando o processo de análise e processamento da reivindicação.

### Utilizando um LLM para extração de informações

!(Image-of-information-extraction-LLM.svg)

A imagem demonstra como um modelo de linguagem (LLM) pode extrair informações-chave de um email sobre um acidente de carro e preencher automaticamente um formulário estruturado. No exemplo, o LLM extraiu corretamente a data do acidente, local, tipo de sinistro e modelo do carro do remetente, economizando tempo e reduzindo o risco de erros manuais no cadastro da ocorrência.

## Exemplos do Trabalho de Prototipagem (Continuação)

### Utilizando um LLM para Análise de Sentimento

Detectar o tom do texto e potencialmente agir sobre ele.
[Image of LLM sentiment analysis example]

### Utilizando Reconhecimento de Imagem para Enquadrar Veículos em Fotos

Analisar imagens fornecidas pelo cliente.
[Image of image recognition of vehicle]

### Utilizando Reconhecimento de Imagem para Detectar Danos

Avaliação de danos com base na imagem.
[Image of image recognition of damage]

### Aplicativo Web para Revisar/Processar Sinistros

Um aplicativo que integra essas ferramentas e permite que os usuários processem as solicitações recebidas de forma mais eficiente.
[Image of a web application that ties in these tools]

## Resultados

A diretoria foi convencida! A empresa decidiu financiar totalmente o projeto, permitindo a transição da fase de prototipagem para a produção. E a boa notícia é que vocês foram contratados para fazer parte da equipe que construirá e implementará a solução completa!

## Criando Seu Projeto e Servidor de Pipeline Utilizando o OpenShift AI

Abaixo estão as instruções para configurar seu ambiente de trabalho, para isso acesse: 

1. [Demo Redhat Site](https://demo.redhat.com/)
2. Faça login com seu usuário e senha
3. Pesquise por "Streamline Insurance Claims with Openshift AI"
4. Inicie o seu ambiente de trabalho para aprendizagem.

### Instruções para Configuração

Como etapa preliminar, cada um de vocês irá:

1. **Criar um Projeto de Ciência de Dados:** Isso ajudará a manter seus arquivos organizados.
2. **Criar uma Conexão de Dados:** Necessária para o servidor de pipeline armazenar seus artefatos.
3. **Implantar um Servidor de Pipeline de Ciência de Dados:** É melhor criá-lo desde o início.
4. **Iniciar um Workbench:** Usaremos para revisar o conteúdo e os notebooks.
5. **Clonar o Repositório Git em Seu Workbench:** Este contém todo o código do protótipo.

As instruções abaixo guiarão você por essas etapas.

### Criando um Projeto

1. No OpenShift AI Dashboard, navegue até o menu **Data Science Projects** à esquerda.
2. Crie um projeto com o **mesmo nome** do seu ID de usuário (por exemplo, `user1`).
3. **Importante:** Utilize o nome de usuário correto (`user1`, `user2`, etc.), pois isso é crucial para o funcionamento correto do projeto.
4. Deixe o nome do recurso inalterado.
5. Opcionalmente, insira seu nome e sobrenome na descrição do projeto.

### Criando uma Conexão de Dados para o Servidor de Pipeline

1. Adicionaremos uma conexão de dados que aponta para uma instância Minio no cluster, que atuará como um Armazenamento de Objetos simples.
2. Clique em **Add data connection** e insira as seguintes informações fornecidas pela painel.

### Criando um Servidor de Pipeline

1. No seu Projeto de Ciência de Dados, clique em **Create a pipeline Server**.
2. Selecione a Conexão de Dados criada anteriormente (Shared Minio - pipelines) e clique em **Configure**.
3. Aguarde a implantação do servidor de pipeline. Quando estiver pronto, você verá uma mensagem de confirmação na tela.

Com isso, seu servidor de pipeline estará pronto e implantado.

