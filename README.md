# Como-utilizar-o-Azure-AI-Search
A proposta deste repositório é trazer um tutorial passo a passo para exemplificar a utilização do Azure AI Search para analisar reviews de clientes utilizando a inteligência artificial.

A iniciativa da criação deste repositório foi para registrar a resolução do exercício 'Inteligência de Documentos e Mineração de Conhecimento' que é parte do curso [Microsoft Azure AI Fundamentals](https://web.dio.me/track/microsoft-azure-ai-fundamentals) fornecido pela Digital Innovation One - [DIO](https://www.dio.me/), este em preparação para a certificação AI-900: Microsoft Azure AI Fundamentals.

Espero poder ajudar todos aqueles que por ventura vierem a este repositório.


## Apresentação dos Problemas

O problema que iremos resolver é o mesmo apresentando pela Microsoft Learn com o título 'Explore an Azure AI Search index (UI)', este problema pode ser encontrado [aqui](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/11-ai-search.html).

O problema proposto é o seguinte:

> "Vamos imaginar que você trabalha para a Fourth Coffee, uma rede nacional de cafés. Você foi solicitado a ajudar a construir uma solução de mineração de conhecimento que facilite a busca de insights sobre as experiências dos clientes. Você decide criar um índice do Azure AI Search usando dados extraídos de avaliações de clientes."

## Pré-requisitos para resolução do problema

* Ter uma conta do Microsoft Azure. (Caso você não tenha um conta será necessário criar, para isto siga os passos que serão apresentados abaixo)

* Ter muita vontade e disposição para aprender.


#### Passo a Passo para criar a conta no Microsoft Azure

* Acesse o site da [Microsoft Azure](https://azure.microsoft.com/pt-br/free/search/?ef_id=_k_CjwKCAiA_aGuBhACEiwAly57MQIxpbuFTl1YFmHB1o36Rq5fAlKA8JO9CdOLPuyq_oV_3JBza8E_-hoC4OAQAvD_BwE_k_&OCID=AIDcmmzmnb0182_SEM__k_CjwKCAiA_aGuBhACEiwAly57MQIxpbuFTl1YFmHB1o36Rq5fAlKA8JO9CdOLPuyq_oV_3JBza8E_-hoC4OAQAvD_BwE_k_&gad_source=1&gclid=CjwKCAiA_aGuBhACEiwAly57MQIxpbuFTl1YFmHB1o36Rq5fAlKA8JO9CdOLPuyq_oV_3JBza8E_-hoC4OAQAvD_BwE)
* Clique em Experimente gratuitamente ou no botão Início gratuito.
* Será necessário colocar os dados de sua conta da Microsoft, que em geral é de um e-mail da hotmail ou outlook.
* Siga os passos conforme solicitado.

**OBS**: Será necessário cadastrar um cartão de crédito para aderir ao plano gratuito, inicialmente você terá $200 dólares de crédito ou 30 dias para testar os serviços, prevalecendo o que acabar primeiro.

## Passo a Passo para resolver o problema

Agora que você já tem uma conta da Microsoft Azure, vamos começar:

1. Acesse o [Portal da Azure](https://portal.azure.com/) para começar a resolver o problema.

2. Na aba Azure Services procure por 'Create a Resource'.

![Create a Resource](https://i.ibb.co/XXZsckw/Create-a-Resource.png)

3. Em seguida pesquise por Azure AI Services. 

![Azure AI Services](https://i.ibb.co/HrJq3PZ/Azure-AI-Services.png)

4. Clicaremos em create

![Create Azure AI Services](https://i.ibb.co/Y2V8Rrb/Create-Azure-AI-Services.png)

5. Então colocaremos as seguintes informações e clique em Review + create: 

> **Subscription:** Aqui é a sua inscrição do Microsoft Azure, se você estiver com uma conta gratuita, provavelmente apareça ela como padrão.

> **esource group:** Criar ou selecionar um Grupo de Recursos. (Como provavelmente você não terá um Grupo de Recursos para selecionar, deverá criar um clicando no botão create new, então deverá colocar um nome para o mesmo e clicar em ok. Experimente colocar **LabAISearchRG**, onde LAB é Laboratorio e RG é Resource Group)

> **Region:** Sugiro você colocar a região East US. Que é a mais próximo com custo mais baixo.

> **Name:** Entrar com um nome único para seu Workspace. Neste caso aqui sugiro colocar **lab-aisearch**, mas pode ser qualquer nome a sua escolha.

> **Pricing tier:** Selecionar Standard S0

> Marcar a caixa 'By checking this box I acknowledge that I have read and understood all the terms below' 

![Informações Azure AI Services](https://i.ibb.co/1ZKtPn9/Review-create.png)

6. Clique em create e espere terminar o deployment.

![Create AI Services](https://i.ibb.co/nMCr5kS/Create-AI-Service.png)

7. Após a conclusão o deployment estará completo.

![Deployment completo](https://i.ibb.co/YN2Lgdt/Deployment-complete.png)

8. Agora iremos na aba Azure Services procure por 'Create a Resource' novamente.

![Create a Resource](https://i.ibb.co/XXZsckw/Create-a-Resource.png)

9. Em seguida pesquise por Azure AI Search, após selecioná-lo, clicar em Create em seguida. 

![Azure AI Search](https://i.ibb.co/KWj0pS5/Azure-AI-Search.png)

10. Prencheremos com as seguintes informações e clique em Review + create, em seguida, após a validação clique em create:

> **Subscription:** Aqui é a sua inscrição do Microsoft Azure, se você estiver com uma conta gratuita, provavelmente apareça ela como padrão.

> **Resource group:** Selecionar o Resource group criado anteriormente, que é o **LabAISearchRG**.

> **Name:** Entrar com um nome único para seu Workspace. Neste caso aqui sugiro colocar **lab-aisearch**, mas pode ser qualquer nome a sua escolha.

> **Region:** Sugiro você colocar a região East US. Que é a mais próximo com custo mais baixo.

> **Pricing tier:** Clique em Change Pricing Tier e selecione a opção Basic.

![Review + create AI Search](https://i.ibb.co/FYYHK0Z/Review-create-AI-Search.png)

11. Voltaremos mais uma vez para a aba Azure Services, procuremos por 'Create a Resource'.

![Create a Resource](https://i.ibb.co/XXZsckw/Create-a-Resource.png)

12. Em seguida pesquise por Storage account, após selecioná-lo, clicar em Create em seguida. 

![Storage account](https://i.ibb.co/K7bJdV4/Storage-account.png)

13. Prencheremos com as seguintes informações e clicaremos em Review, em seguida, após a validação clique em create:

> **Subscription:** Aqui é a sua inscrição do Microsoft Azure, se você estiver com uma conta gratuita, provavelmente apareça ela como padrão.

> **Resource group:** Selecionar o Resource group criado anteriormente, que é o **LabAISearchRG**.

> **Storage account name:** Entrar com um nome único para seu storage account. Neste caso não posso sugerir um nome, pois ele não será único. Então você pode escolher um nome a sua escolha.

> **Region:** Sugiro você colocar a região East US. Que é a mais próximo com custo mais baixo.

> **Performace:** Standard

> **Redundacy:** Locally-redundant storage (LRS)

![Detalhes Storage account](https://i.ibb.co/wNCRT2H/Detalhes-Storage-account.png)

14. Após o deployment da criação do storage account está completo. Iremos clicar em Go to resource.

![Go to resource](https://i.ibb.co/92cRmBn/Go-to-resource.png)

15. No menu lateral esquerdo iremos procurar por configuration, após clicar iremos colocar a opção 'Allow Blob anonymous access' como enable e clicar em save logo acima.

![Ativar acesso anonimo](https://i.ibb.co/M1qZ5zd/Ativar-acesso-anonimo.png)

16. Ainda no menu lateral, em Data Storage iremos selecionar containers. Clicaremos em '+ Container' e adicionaremos as seguintes informações e clicaremos em create:

> **Name:** coffeereviews

> **Anonymous access level:** Container (anonymous read access for containers and blobs)

![New container](https://i.ibb.co/gwSxCcw/New-container.png)

17. Após criado o container, iremos acessálo para adicionar alguns arquivos, clique no container criado. 

![container coffee](https://i.ibb.co/gvBbXB3/container-coffee.png)

18. Agora clique em upload e faça upload dos arquivos que estão na pasta reviews deste repositório.

![container coffee](https://i.ibb.co/mHmrc5Q/reviews-arquivos.png)

19. Voltaremos para o menu inicial, na aba Resource, iremos selecionar o nosso Search Service de nome aisearchlab1.

![Selecionar ai Search](https://i.ibb.co/JcT9yhm/selecionar-aisearch1.png)

20. Clicaremos então em import data.

![Import Data](https://i.ibb.co/yXRpqDd/Import-data.png)

21. Nesta tela adicionaremos as seguintes informações e clicaremos em next: add cognitive skills (optional):


> **Data Source:** Azure Blob Storage

> **Data source name:** coffee-customer-data

> **Data to extract:** Content and metadata

> **Parsing mode:** Default

> **Connection string:** Selecione 'Choose an existing connection'. Selecione então o storage account, que nosso caso é labaisearch, selecione então o container coffee-reviews, and e clique em Select.

> **Managed identity authentication:** None

> **Container name:** Este campo será preenchido automaticamente.

> **Blob folder:** deixe em branco.

> **Description:** Reviews para a loja Fourth Coffee.

![IImport Data Informações](https://i.ibb.co/f1Zt55X/Import-data-informa-es.png)

22. Na próxima aba colocaremos as seguintes informações e clicaremos em Next: Customize Targit index:

Em Attach AI Services

> **Attach Cognitive Services**: Já está selecionado por padrão o nosso Azure AI Service Resource.

Em Add enrichments

> **Skillset name**: Mudar para coffee-skillset.

> **Enable OCR and merge all text into merged_content field**: Deixar marcada a caixinha.

> **Source data field**: merged_content.

> **Enrichment granularity level**: Pages (5000 character chunks)

> **Enable incremental enrichment**: Deixar desmarcada

> **Marcar as seguintes caixinhas**: Extract location names, Extract key phrases, Detect sentiment, Generate tags from images, Generate captions from images.

![Add enrichments](https://i.ibb.co/99SWbZs/add-enrichements.png)

Em Save enrichments to a knowledge store

> **Selecione as seguintes caixinhas:** Image projections, Documents, Pages, Key phrases, Entities, Image details, Image references

> **Container name**: knowledge-store

![Save enrichments to a knowledge store](https://i.ibb.co/m87Yr5M/Save-enrichments-to-a-knowledge-store.png)

OBS: Se aparecer um alerta em vermelho como abaixo:

![Alerta](https://i.ibb.co/RvWb7zf/6a-azure-cognitive-search-enrichments-warning.png)

> Selecione Choose an existing connection. Escolha a conta de armazenamento que você criou anteriormente.

> Clique em + Container para criar um novo contêiner chamado knowledge-store com o nível de privacidade definido como Private e selecione Criar.

> Selecione o contêiner knowledge-store e clique em Select na parte inferior da tela.


24. Na próxima preencha com as seguintes informações e clicar em Next: Create an indexer: 

> **index name**: coffee-index.

> **Key**: metadata_storage_path.

> **Suggester name**: em branco.

> **Search mode**: Estará preenchido automaticamente

> **Caixinhas**: Para cada caixinha que estiver preenchida a coluna Retrievable, você deverá preencher a caixinha correspondente da coluna Filterable.

![Index Name](https://i.ibb.co/DKsGV2H/Index-Name.png)

25. Preenche com as seguintes informações e clique em Submit.

> **Name**: coffee-indexer.

> **Schedule**: Once.

> **Description**: Em branco.

> **Advanced options**: Certifique-se de marcar a caixinha 'Base-64 Encode Keys'.

![Create indexer](https://i.ibb.co/c816nZt/create-indexer.png)

26. Clique em Search Explorer.

![Search Explorer](https://i.ibb.co/wspcr4t/Search-Explorer.png)

27. Na barra de Pesquisa iremos pesquisar o seguinte:

**search="&$count=true** - Verificar se a cadeia de busca está on.

![Saber se tá on](https://i.ibb.co/QjZ7Drp/Saber-se-t-on.png)

**search=locations:'Chicago'** - Reviews de clientes de Chicago

**search=sentiment:'negative'** - Reviews de clientes com sentimentos negativos


Parabéns! Você fez todo o processo!



## Meus Contatos

[![LinkedIn](https://img.shields.io/badge/LinkedIn-000?style=for-the-badge&logo=linkedin&logoColor=0E76A8)](https://www.linkedin.com/in/tiagolisboanovais/)

[![Instagram](https://img.shields.io/badge/instagram-000?style=for-the-badge&logo=instagram&logoColor=0E76A8)](https://www.instagram.com/tiagolisboa.ti/)

[![E-mail](https://img.shields.io/badge/-Email-000?style=for-the-badge&logo=microsoft-outlook&logoColor=007BFF)](mailto:tiagolisboanovais)

[![Github](https://img.shields.io/badge/github-000?style=for-the-badge&logo=github&logoColor=0E76A8)](https://github.com/tiagolisboanovais)

