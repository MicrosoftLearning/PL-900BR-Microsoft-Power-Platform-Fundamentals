---
lab:
    title: 'Laboratório 2: Como criar um aplicativo de tela, Parte 1'
    module: 'Módulo 3: Introdução ao Power Apps'
---

# Módulo 3: Introdução ao Power Apps

## Laboratório: Como criar um aplicativo de tela, Parte 1

### Aviso importante (vigente a partir de novembro de 2020):
O nome do Common Data Service passou a ser Microsoft Dataverse. Algumas terminologias no Microsoft Dataverse foram atualizadas. Por exemplo: "entidade" passou a ser “tabela”. Os campos e registros nos bancos de dados do Dataverse agora são chamados de colunas e linhas.

A experiência do usuário nos aplicativos ainda está em processo de atualização, mas algumas referências à terminologia do Microsoft Dataverse podem estar desatualizadas, como entidade (agora **tabela**), campo (agora **coluna**) e registro (agora **linha**). Lembre-se disso ao trabalhar nos laboratórios.

Para saber mais e ver a lista completa dos termos alterados, veja [O que é o Microsoft Dataverse?](https://docs.microsoft.com/pt-br/powerapps/maker/common-data-service/data-platform-intro#terminology-updates)

# Cenário

O Bellows College é uma instituição educacional com vários edifícios no campus. Atualmente as visitas ao campus são anotadas em papel. O registro das informações não é consistente e não existe nenhum recurso para coletar e analisar os dados das visitas em todo o campus. 

A administração do campus quer modernizar o sistema de registro de visitantes, com controle do acesso aos edifícios pelo pessoal de segurança, além de exigência de notificação prévia e registro de todas as visitas pelos anfitriões.

Ao longo deste curso, você vai criar aplicativos e fazer automações para permitir que a administração e a equipe de segurança do Bellows College gerenciem e controlem o acesso aos edifícios no campus.  

Na parte 1 deste laboratório, você vai projetar no Power Apps um aplicativo de tela que pode ser usado pela equipe da instituição para gerenciar as visitas dos convidados.

# Macroetapas do laboratório

Seguiremos o esquema abaixo para projetar o aplicativo de tela:

-   Criar o aplicativo a partir de dados usando o modelo de fator forma do telefone
-   Configurar uma página de detalhes com informações da visita
-   Configurar uma página de edição para criar visitas
-   Configurar um controle de galeria para mostrar as visitas
-   Adicionar filtragem na fonte de dados da galeria para mostrar apenas visitas futuras

## Pré-requisitos

* Conclusão do **Módulo 0 Laboratório 0 – Validar ambiente do laboratório**
* Conclusão do **Módulo 2 Laboratório 1 – Introdução ao Microsoft Dataverse**

## Questões importantes antes de prosseguir

-   Qual é o fator forma predominante para o público-alvo?
-   Estimar o número de registros que serão armazenados no sistema 
-   Como limitar os registros selecionados para melhorar o desempenho do aplicativo e a adoção do usuário?

# Exercício 1: criar o aplicativo de tela dos funcionários

**Objetivo:** Neste exercício você vai criar um aplicativo de tela a partir de um modelo e, em seguida, vai modificá-lo para incluir os dados necessários.

## Tarefa 1: criar o aplicativo de tela

Nesta tarefa você vai criar um aplicativo de tela usando o modelo de layout do telefone com base no Microsoft Dataverse. Ao usar Visitas como uma tabela selecionada do Dataverse, o modelo gera um aplicativo Galeria – Exibir – Editar para gerenciar visitas ao campus.

1.  Exiba os aplicativos no seu ambiente.

    -   Entre em <https://make.powerapps.com>.

    -   Selecione o **ambiente** no canto superior direito, se ele ainda não estiver definido
        para o seu ambiente de Prática.

    -   Selecione **Aplicativos**.

2.  Crie um novo aplicativo de tela.

    -   Clique em **Novo aplicativo** e selecione **Tela**.

    -   Selecione **Layout do telefone** em **Common Data Service**.

3.  Selecione **Criar** na conexão do **Common Data Service**.

4.  Selecione a tabela **Visitas**.

5.  Clique em **Conectar**.

6.  A janela **Boas-vindas ao Power Apps Studio** pode ser exibida. Clique em **Ignorar**.

7.  Salve o aplicativo

    -   Clique em **Arquivo \> Salvar**.

    -   Digite **[Seu sobrenome] Equipe do Campus** como o nome do aplicativo.

    -   Clique em **Salvar**.

## Tarefa 2: configurar o formulário Detalhes das visitas

Nesta tarefa você configurará o formulário Detalhes para exibir informações sobre os registros de visitas individuais.

1. Selecione a seta **Voltar** canto esquerdo para voltar às definições do aplicativo.

2. Expanda **DetailScreen1** em **Modo de exibição de árvore**.

3.  Selecione **DetailForm1**.

4.  Selecione **Editar campos**, próximo de **Campos** no painel à direita.

5.  Clique em **Adicionar campo**.

6.  Selecione os seguintes campos:

    * Fim real
    
    * Início real
    
    * Prédio 
    
    * Código
    
    * Fim programado
    
    * Início programado
    
    * Visitante
    
7.  Clique em **Adicionar**.

8.  Para reordenar os campos no painel **Campos**, arraste e solte os nomes dos campos para cima e para baixo. A ordem recomendada é:
    * Código, Nome, Prédio, Visitante, Início programado, Fim programado, Início real, Fim real
    >**Dica:** Para recolher um campo, clique na seta para baixo ao lado do nome do campo.

9.  Para remover o campo **Criado em**, clique nas reticências (**...**) ao lado do nome do campo e selecione **Excluir**. 

10.  Feche o painel **Campos**.
 
11.  Para salvar o trabalho em andamento, clique em **Arquivo** e depois em **Salvar**. Use a seta de voltar para retornar ao aplicativo.

## Tarefa 3: configurar o formulário Editar visitas

Nesta tarefa você configurará o formulário para editar linhas com as informações sobre as visitas individuais.

1.  Expanda **EditScreen1** em **Modo de exibição de árvore**.

2.  Selecione **EditForm1**.

3.  Selecione o campo **Criado em** e clique na tecla **Del** para removê-lo.

4.  Selecione **Editar campos** no painel de propriedades.

5.  Clique em **Adicionar campo**.

6.  Selecione os seguintes campos:

    * Prédio 
    
    * Fim programado
    
    * Início programado
    
    * Visitante
    
7.  Clique em **Adicionar**.

8.  Para reordenar os campos no painel **Campos**, arraste e solte os nomes dos campos para cima e para baixo. A ordem recomendada é:
    
    * Nome, Prédio, Visitante, Início programado, Fim programado
    >**Dica:** Para recolher um campo, clique na seta para baixo ao lado do nome do campo. 

9.  Feche o painel **Campos**.

10.  Para salvar o trabalho em andamento, clique em **Arquivo** e depois em **Salvar**. Use a seta de voltar para retornar ao aplicativo.

Sua tela deve ter uma aparência semelhante à seguinte.

![Formulário de edição de tela](media/2-canvas-edit-form.png)

## Tarefa 4: configurar a galeria Visitas

Nesta tarefa você configurará a galeria pré-gerada para exibir o título, a data de início e a data de término da visita. 

1.  Expanda **BrowseScreen1** em **Modo de exibição de árvore**.

2.  Selecione **BrowseGallery1**.

3.  Selecione a propriedade **TemplateSize** no painel Propriedades avançadas à direita.

4.  Substitua a expressão com o seguinte texto: `Min(150, BrowseGallery1.Height - 60)`. Isso garante que haja espaço suficiente para informações adicionais.

5.  Na visualização do aplicativo, selecione o primeiro campo ‘Data e Hora’ na galeria.

6.  Na barra da fórmula, na parte superior, troque **ThisItem.’Created On** por `ThisItem.'Scheduled Start'`.

7.  Selecione novamente o campo.

8.  Pressione **CTRL + C** e depois **CTRL + V** para copiar o campo.

9.  Usando o mouse ou o teclado, mova o controle copiado para baixo e o alinhe com os outros controles na galeria, abaixo do outro campo Data e Hora.

10.  Na barra da fórmula, na parte superior, troque **ThisItem.’Scheduled Start’** por `ThisItem.'Scheduled End'`.

11.  Para salvar o trabalho em andamento, clique em **Arquivo** e depois em **Salvar**. Use a seta de voltar para retornar ao aplicativo.

## Tarefa 5: adicionar um filtro de data

Como o número de visitas cresce continuamente, os usuários precisam de um recurso para filtrar a galeria de visitas. Por exemplo, quando o usuário quer ver somente as visitas futuras. Nesta tarefa, você adicionará a funcionalidade de exibir somente as visitas a partir de uma data selecionada pelo usuário.

1. Selecione **BrowseScreen1**.

2. Selecione o menu **Inserir**, na parte superior.

3. Clique em **Inserir** e selecione **Seletor de data**.

4. Usando o teclado ou o mouse, posicione o controle abaixo da caixa de pesquisa.

5. Selecione **BrowseGallery1**. 

6. Redimensione e mova o controle da galeria para que fique abaixo do seletor de data e cubra a tela. Para fazer isso, você pode clicar no ícone de redimensionamento, na parte superior central do controle da galeria, e redimensionar o controle para iniciar após o seletor de data.

7. Depois de selecionar **BrowseGallery1**, clique na guia **Avançado** do painel Propriedades.

8. Localize a propriedade **Itens** e clique na caixa de texto.

9. Na expressão, localize **[@Visits]** e substitua por `Filter(Visits,'Scheduled End' >= DatePicker1.SelectedDate)`. A expressão completa deverá ter a aparência a seguir.

   ```
   SortByColumns(
   	Search(
        Filter(
        	Visits,
            'Scheduled End' >= DatePicker1.SelectedDate
           ),
           TextSearchBox1.Text,
       	"bc_code","bc_name"
       ),
     "bc_code",
     If(SortDescending1, Descending, Ascending)
   )
   ```
   
10. Para salvar o trabalho em andamento, clique em **Arquivo** e depois em **Salvar**. Use a seta de voltar para retornar ao aplicativo.

Sua tela deve ter uma aparência semelhante à seguinte.

![Tela de filtro da galeria](media/2-canvas-browse.png)

# Exercício 2: concluir o aplicativo

Neste exercício, você testará o aplicativo e o adicionará o aplicativo à sua solução se ele se ele estiver aprovado.

## Tarefa 1: testar o aplicativo

1.  Inicie o aplicativo.

    -   Selecione **BrowseScreen1** e pressione Função **F5**, ou clique no ícone **Executar** no canto superior direito para exibir o aplicativo.
    
    -   O aplicativo é carregado e exibe a lista de visitas. 
    
    -   Selecione datas diferentes no controle seletor de datas para testar o filtro.
    
    -   Selecione uma visita e verifique se o formulário de exibição funciona corretamente.
    
    -   Retorne para a galeria e pressione **+** para criar uma visita. Verifique se o formulário de edição contém colunas obrigatórias, incluindo visitante, prédio e datas programadas de início e fim.
    
    -   Preencha as informações e envie. Verifique se o novo registro aparece na galeria.
    
    -   Crie pelo menos mais 2 visitas.
    
    -   Pressione a tecla **ESC** ou clique no ícone **X** para fechar o modo de visualização.

2.  Salve e publique o aplicativo.

    -   Clique em **Arquivo** e, se o botão Salvar for exibido, clique em **Salvar**.

    -   Clique em **Publicar**.

    -   Clique em **Publicar esta versão**.

    -   Use a seta **Voltar** para retornar ao aplicativo.

    -   Feche a janela ou a guia **Designer** do navegador.

    -   Se solicitado, clique em **Sair** ao tentar fechar a janela do navegador.

## Tarefa 2: adicionar o aplicativo à solução e publicar. 

1. Abra a solução Gerenciamento do campus.

   * Entre em <https://make.powerapps.com>.
   
   * Se o ambiente exibido no canto superior direito não for o seu ambiente de prática, selecione seu **Ambiente**. 
   
   * Selecione **Soluções**.
   
   * Clique para abrir a solução **Gerenciamento do campus**.
   
2. Selecione **Adicionar existente**, depois clique em **Aplicativo** e em **Aplicativo de tela**.

3. Selecione a guia **Soluções externas**.

4. Selecione o aplicativo **Equipe do campus**, clique em **Adicionar**.

5. Selecione **Publicar todas as personalizações**.

# Desafios

* Exiba um calendário de todas as visitas e filtre por intervalo de datas
* Implemente no aplicativo a funcionalidade de criar e gerenciar contatos
* Como exibir vários encontros durante uma única visita?

