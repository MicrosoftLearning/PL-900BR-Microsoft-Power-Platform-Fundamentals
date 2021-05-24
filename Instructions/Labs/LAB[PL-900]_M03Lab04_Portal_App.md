---
lab:
    title: 'Laboratório 5: Como criar um portal do Power Apps'
    module: 'Módulo 3: Introdução ao Power Apps'
---

# Módulo 3: Introdução ao Power Apps

## ‘Laboratório 4: Como criar um portal do Power Apps'

### Aviso importante (vigente a partir de novembro de 2020):
O nome do Common Data Service passou a ser Microsoft Dataverse. Algumas terminologias no Microsoft Dataverse foram atualizadas. Por exemplo: "entidade" passou a ser “tabela”. Os campos e registros nos bancos de dados do Dataverse agora são chamados de colunas e linhas.

A experiência do usuário nos aplicativos ainda está em processo de atualização, mas algumas referências à terminologia do Microsoft Dataverse podem estar desatualizadas, como entidade (agora **tabela**), campo (agora **coluna**) e registro (agora **linha**). Lembre-se disso ao trabalhar nos laboratórios. Estamos trabalhando para o conteúdo estar totalmente atualizado em breve. 

Para saber mais e ver a lista completa dos termos alterados, veja [O que é o Microsoft Dataverse?](https://docs.microsoft.com/pt-br/powerapps/maker/common-data-service/data-platform-intro#terminology-updates)

# Cenário

O Bellows College é uma instituição educacional com vários edifícios no campus. Atualmente as visitas ao campus são anotadas em papel. O registro das informações não é consistente e não existe nenhum recurso para coletar e analisar os dados das visitas em todo o campus.

A administração do campus quer fornecer aos visitantes informações sobre os prédios do campus. Os visitantes poderão ver a lista de prédios em um site, que será construído usando um portal do Power Apps.

Neste laboratório, você vai disponibilizar um portal do Power Apps e criar uma página da Web de portais que mostra uma lista com os prédios do campus.

# Macroetapas do laboratório

Seguiremos o esquema abaixo para projetar o portal do Power Apps:

* Provisionar um portal do Power Apps no ambiente do Dataverse
* Criar e configurar uma página da Web para mostrar a lista de prédios
* Criar um novo tema e aplica-lo ao portal

## Pré-requisitos

* Conclusão do **Módulo 0 Laboratório 0 – Validar ambiente do laboratório**
* Conclusão do **Módulo 2 Laboratório 1 – Introdução ao Microsoft Dataverse**

## Questões importantes antes de prosseguir

* Os aplicativos de portais do Power Apps são sempre iniciados a partir de um modelo em vez de um aplicativo em branco. O portal já deve ter sido criado no Módulo 0 Laboratório 0. Quando você provisionar um portal, ele já tem páginas, menus e um tema padrão. 

# Exercício 1: criar uma página da Web do portal

**Objetivo:** neste exercício você vai criar uma nova página da Web que exibe alguns conteúdos estáticos, bem como uma lista de prédios do Dataverse.

## Tarefa 1: navegar até o portal

1.  Acesse <https://make.powerapps.com>.

2.  Confirme se você está no seu ambiente de prática. Se não estiver, troque de ambiente (no canto superior direito).

3.  Clique em **Aplicativos**.

4.  Localize o aplicativo que tem o **Tipo** igual a **Portal**

5.  Clique no nome do aplicativo para abrir o portal

    > Você deve ser redirecionado para a página de aterrissagem do site do portal com uma mensagem de boas-vindas. Navegue pelo portal para ver o que foi criado por padrão quando você provisionou o portal. 

## Tarefa 2: criar uma página da Web

1.  Abra o Estúdio dos portais do Power Apps

    -   Entre em <https://make.powerapps.com> (confira se já está aberto nas suas guias).

    -   Selecione **Aplicativos**.
    
    -   Localize o aplicativo que tem o **Tipo** igual a **Portal**

    -   Clique nas reticencias (**...**) à direita do nome do aplicativo de portais e selecione **Editar**.

    > Agora você está no Estúdio dos portais do Power Apps. É aqui que você pode modificar e criar o conteúdo do portal.

2.  Crie uma página nova.

    -   Na barra de comando, selecione **Nova página**.

    -   Passe o mouse sobre **Layouts fixos** e escolha **Página com título**

3.  No painel de propriedades, em **Exibição**, troque o **Nome** de **Nova página nova (1)** para `Diretório de prédios`.

4.  Em **URL parcial**, troque o valor para `diretorio-de-predios` e pressione a tecla Tab (para iniciar o salvamento automático).

    > O título da página agora deve ser **Diretório de prédios**.
    
## Tarefa 3: adicionar conteúdos estáticos

1.  Adicione uma seção à página da Web.

    -   Na tela (área que exibe a página da Web), selecione a seção **Cópia da página**. Essa é a caixa grande que cerca as 2 frases de texto que estão no meio da página.

    -   Na caixa de ferramentas (lado esquerdo), selecione o ícone **Componentes**.

    -   Escolha **Seção com duas colunas** na área **Layout da seção**.

2.  Adicione textos estáticos.

    -   Na tela (área que exibe a página da Web), selecione a coluna à esquerda

    -   Na caixa de ferramentas (lado esquerdo), selecione o ícone **Componentes**.

    -   Selecione **Texto** na área **Componentes do portal**.

    -   Na nova área de texto, insira o seguinte texto:
          ```
          Abaixo está o diretório de prédios.
          ```
    -   Selecione a caixa de texto acima daquela que você acabou de editar e clique em **Excluir** na barra de comandos para remover o texto padrão.

3. Adicione uma Imagem.

    -   Na tela (área que exibe a página da Web), selecione a coluna à direita

    -   Na caixa de ferramentas (lado esquerdo), selecione o ícone **Componentes**.

    -   Selecione **Imagem** na área **Componentes do portal**.

    -   No painel de propriedades, clique em **Selecionar uma imagem**. Localize e selecione **Product A.png**.
    
    -   No painel de propriedades, clique no menu suspenso da seção **Formatação** e troque a **Largura** para 70% (lembre-se de digitar o símbolo %). Faça as alterações no dimensionamento da imagem até atingir o resultado desejado.

4.  Clique em **Navegar pelo site** para ver como a página está.  Agora existe uma opção **Diretório de prédios** no menu principal.

    > Você precisa configurar o navegador para aceitar pop-ups.

## Tarefa 4: adicionar um componente de lista

1.  Volte até a guia anterior e continue a partir da etapa 2. Se não for possível, siga as etapas abaixo para retornar a esse local.

    -   Entre em <https://make.powerapps.com> (confira se já está aberto nas suas guias).

    -   Localize o aplicativo que tem o **Tipo** igual a **Portal**

    -   Clique nas reticências (**...**) e escolha **Editar**.
    
    -   Na caixa de ferramentas (lado esquerdo), selecione a opção **Páginas**. 

    -   Localize e selecione a página **Diretório de prédios** criada anteriormente.
    
2.  Adicione uma lista de componentes à página Lista de prédios.

    -   Selecione a seção com as duas colunas.

    -   Na caixa de ferramentas (lado esquerdo), selecione o ícone **Componentes**.

    -   Escolha **Seção com uma coluna** na área **Layout de seção** (uma seção será exibida abaixo da imagem e do texto na página da Web).

    -   Selecione a nova seção de coluna na tela.

    -   Na caixa de ferramentas (lado esquerdo), selecione o ícone **Componentes**.

    -   Escolha **Lista** na área **Componentes do portal** (uma lista será exibida na nova seção).
    
3.  Configure o componente da lista.

    -   Selecione o componente lista na tela.

    -   No painel de propriedades (lado direito), digite `Lista de prédios` no campo **Nome**

    -   No campo **Tabela**, escolha **Building (bc_building)** na lista suspensa.

    -   Em **Visualizações**, escolha **Prédios ativos**.

    -   Não mexa nas demais as configurações padrão
    
4.  Clique em **Navegar pelo site** para visualizar a página. 

    > A lista de prédios do seu banco de dados Dataverse é exibida na página da Web.

# Exercício 2: mudar o tema do portal

**Objetivo:** Neste exercício você vai criar um novo tema para alterar o esquema de cores do portal. 

## Tarefa 1: aplicar e editar um tema

1.  Volte até a guia anterior e continue a partir da etapa 2. Se não for possível, siga as etapas abaixo para retornar a esse local.

    -   Entre em <https://make.powerapps.com> (confira se já está aberto nas suas guias).

    -   Localize o aplicativo que tem o **Tipo** igual a **Portal**

    -   Clique nas reticências (**...**) e escolha **Editar**.
    
2.  Aplique e personalize um tema básico.

    -   Na caixa de ferramentas (lado esquerdo), selecione o ícone **Temas**.
    
    -   Clique no botão **Habilitar tema básico** para ativar este recurso.
    
    -   Em uma das predefinições, clique nas reticências (**...**) e escolha **Personalizar**.
    
    -   É criada uma cópia do tema básico. 
    
    -   No painel de propriedades, troque as cores e analise o impacto das alterações no seu portal.
    
    -   Renomeie o tema.
    
3.  Na barra de comando, clique em **Configuração de sincronização**.

O layout do aplicativo deve ser similar ao exibido abaixo:

![Exemplo de portal](media/9-portallabresult.jpg)

# Desafios

* Crie uma exibição diferente dos Prédios que mostra somente o Nome do prédio. Selecione **Navegar pelo site** no estúdio do portal para ver as alterações.
* Na caixa de ferramentas, clique no ícone **Temas** e edite o CSS do seu tema personalizado.
* Crie uma página com o componente **Formulário** e modifique o componente **Lista** para adicionar ou editar linhas do Dataverse com o formulário.
* Ative as **Permissões da entidade** nas **Configurações** de um componente **Lista**. O que acontece com os dados?
* No estúdio do portal, selecione o ícone Editor de código-fonte `</>` para ver o código-fonte da página. Se você conhecer HTML, faça algumas modificações e visualize os resultados.
