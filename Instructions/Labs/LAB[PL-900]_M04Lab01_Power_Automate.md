---
lab:
    title: 'Laboratório 6: Saiba como criar uma solução automatizada'
    module: 'Módulo 4: Introdução ao Power Automate'
---

# Módulo 4: Introdução ao Power Automate
## Laboratório: Saiba como construir uma solução automatizada

### Aviso importante (Em vigor a partir de novembro de 2020):
O Common Data Service foi renomeado para Microsoft Dataverse. Algumas terminologias no Microsoft Dataverse foram atualizadas. Por exemplo, entidade agora é tabela. Os campos e registros nos bancos de dados do Dataverse agora são chamados de colunas e linhas.

Alguns aplicativos estão atualizando a experiência do usuário, portanto algumas referências à terminologia do Microsoft Dataverse, como entidade (agora **tabela**), campo (agora **coluna**) e registro (agora **linha**) podem estar desatualizadas. Lembre-se disso ao participar do laboratório. Esperamos atualizar todo o conteúdo em breve. 

Para obter mais informações e uma lista completa de termos afetados, visite [O que é o Microsoft Dataverse?](https://docs.microsoft.com/pt-br/powerapps/maker/common-data-service/data-platform-intro#terminology-updates)

## Cenário

Bellows College é uma organização educacional com um campus com diversos edifícios. Atualmente, os visitantes do campus são registrados em um diário de papel. As informações não são coletadas de maneira coerente e não há como coletar e analisar os dados dos visitantes em todo o campus. 

A administração do campus pretende modernizar o sistema de registro de visitantes. Hoje em dia, o acesso aos edifícios é controlado pela equipe de segurança e todas as visitas precisam ser pré-registradas e lançadas pelos anfitriões.

Ao longo deste curso, você criará aplicativos e usará a automação para que as equipes de administração e segurança do Bellows College possam gerenciar e controlar o acesso aos edifícios do campus. 

Neste laboratório, você criará fluxos do Power Automate para automatizar várias partes do gerenciamento do campus. 

# Etapas gerais do laboratório

Para concluir o projeto é imprescindível implementar os seguintes requisitos:

* O código exclusivo atribuído a cada visitante deve ser disponibilizado antes da visita.
* A equipe de segurança precisa receber notificações de visitantes que ultrapassam os horários programados.

## Pré-requisitos

* Conclusão do **Módulo 0 Laboratório 0 - Validar ambiente do laboratório**
* Conclusão do **Módulo 2 Laboratório 1 - Introdução ao Microsoft Dataverse**
* Aplicativo Campus Staff criado no **Módulo 3 Laboratório 2 – Como construir um aplicativo de tela, parte 2** (teste)
* Contato John Doe criado com um endereço de email pessoal no **Módulo 3 Laboratório 4 - Como construir um aplicativo baseado em modelo** (teste)

## Considere estes itens antes de começar

-   Qual o mecanismo de distribuição mais adequado para os códigos de visitantes?
-   Como medir o tempo de permanência excedente e aplicar políticas rígidas?

# Exercício \#1: Criar fluxo de Notificação de visita

**Objetivo:** Neste exercício será criado um fluxo no Power Automate que implementa o requisito. O visitante deverá receber um email com o código exclusivo atribuído à visita.

## Tarefa \#1: Criar fluxo

1.  Abra a solução Gerenciamento de Campus.

    -   Faça login em <https://make.powerapps.com>

    -   Selecione o **ambiente.**

    -   Selecione **Soluções**.

    -   Clique para abrir a solução **Gerenciamento de Campus**.

2.  Clique em **Novo** e selecione **Fluxo na nuvem**. Isso abrirá o editor de fluxo do Power Automate em uma nova janela.

3. Pesquise por *Atual* e selecione o conector **Common Data Service (Ambiente atual)**.

4. Selecione o gatilho **Quando um registro é criado, atualizado ou excluído**.

   * Selecione **Criar** em **Condição do gatilho**
   
   * Selecione **Visitas** em **Nome da tabela**
   
   * Selecione **Organização** em **Escopo**
   
   * Na etapa de ativação, clique nas reticências (**...**) e clique em **Renomear**. Renomeie esse gatilho **"Quando uma visita é criada"**. Essas ações são importantes para que todos com permissão para editar o fluxo entendam o propósito da etapa sem precisar de maiores detalhes.

5.  Clique em **Nova etapa**. Esta etapa é necessária para recuperar as informações dos visitantes, inclusive o endereço de email.

6. Pesquise por *Atual* e selecione o conector **Common Data Service (Ambiente atual)**.

7. Selecione **Obter uma linha por ID**. 

   * Selecione **Contatos** em **Nome da tabela**
   
   * No campo **ID de linha**, selecione **Visitante (Valor)** na Lista de conteúdo dinâmico.
   
   * Neste momento, clique nas reticências (**...**) e clique em **Renomear**. Renomeie esta ação **"Criar visitante"**. Essas ações são importantes para que todos com permissão para editar o fluxo entendam o propósito da etapa sem precisar de maiores detalhes.

8. Clique em **Nova etapa**. Essa é a etapa que criará e enviará o email ao visitante.

9. Procure por *email*, selecione o conector **Email** e a ação **Enviar uma notificação por email** 

   * Se precisar Aceitar os Termos e as Condições para usar esta ação, clique em **Aceitar**.
   
   * Selecione o campo **Para** e escolha **Email** na Lista de conteúdo dinâmico. Observe que está abaixo do cabeçalho **Criar visitante**. Isso significa que você está selecionando o email relacionado ao Visitante que foi consultado na etapa anterior. 

   * Insira **Sua visita agendada ao Bellows College** no campo **Assunto**.

   * Insira o seguinte texto no **Corpo do email**:  
        
        > O conteúdo dinâmico precisa ser inserido onde os campos são nomeados entre colchetes. É recomendado copiar e colar todo o texto primeiro e, em seguida, adicionar o conteúdo dinâmico nos locais corretos.
   
        ```
        Prezado(a) {First Name},

        Você tem uma visita agendada ao Bellows Campus de {Scheduled Start} até {Scheduled End}.

        Seu código de segurança é {Code}. Não o compartilhe. Você deverá informar esse código durante sua visita.

        Atenciosamente,

        Administração do Campus
        Bellows College
        ```
   
10.  Selecione o nome do fluxo **Sem Título** na parte superior e renomeie como `Notificação de visita`

11. Clique em **Salvar**

    Deixe esta guia de fluxo aberta para a próxima tarefa. Seu fluxo deve ser parecido com o seguinte:

![Fluxo de notificação de visitantes do Power Automate](media/4-power-automate-notification.png)

## Tarefa \#2: Validar e testar o fluxo

1.  Abra uma nova guia no navegador e acesse <https://make.powerapps.com>

2.  Clique em **Aplicativos** e selecione o aplicativo que você criou **Equipe do Campus**

3.  Deixe esta guia aberta, volte para a guia anterior com o fluxo. 

4.  Na barra de comandos, clique em **Testar**. Selecione **Manualmente** e, em seguida, **Salvar e Testar**.

5.  Deixe a guia de fluxo aberta e volte para a guia anterior com o aplicativo **Equipe do Campus**.

6.  Clique em **+** para adicionar um novo Registro de visita

7.  Insira **John Doe** em **Nome** e escolha um **Edifício**

8.  Escolha **John Doe** como **Visitante**

9.  Escolha as datas de **Início programado** e **Fim programado** para qualquer data no futuro.

10.  Clique no ícone **Marca de seleção** para salvar a nova visita

11.  Volte para a guia anterior com o teste do fluxo em andamento. Observe a execução do fluxo. Se houver algum erro, volte e compare seu fluxo com o exemplo acima. Se o email for enviado com sucesso, você o receberá em sua caixa de entrada. 

12.  Clique na seta para voltar na barra de comando

13.  Na seção **Detalhes**, note que o **Status** está configurado como **Ligado**. Significa que seu fluxo será executado sempre que uma nova visita for criada, até que você desligue. Sempre que for executado, o fluxo será adicionado à lista do **Histórico de execução dos últimos 28 dias**.

14.  Desligue o fluxo clicando em **Desligar** na barra de comandos. Pode ser necessário pressionar as reticências (**...**) para ver esta opção.

15.  Fechar esta janela.

# Exercício #2: Criar fluxo de Varredura de segurança

**Objetivo:** Neste exercício será criado um fluxo no Power Automate que implementa o requisito. Uma varredura de segurança deve ser realizada a cada 15 minutos e a equipe de segurança deve ser notificada se algum dos visitantes ultrapassar o horário programado.

## Tarefa #1: Criar um fluxo para recuperar registros

1. Abra a solução Gerenciamento de Campus.

   -   Faça login em <https://make.powerapps.com>

   -   Selecione **Ambiente.**

   -   Selecione **Soluções**.

   -   Clique para abrir a solução **Gerenciamento de Campus**.

2. Clique em **Novo** e selecione **Fluxo na nuvem**. Isso abrirá o editor de fluxo do Power Automate em uma nova janela.

3. Pesquise por *recorrência*, selecione o conector **Agenda** e, em seguida, escolha o gatilho **Recorrência**.

4. Defina **Intervalo** como **15 minutos**

5. Clique em **Nova etapa**. Pesquise por *Atual* e selecione o conector **Common Data Service (Ambiente atual)**. Selecione a ação **Listar linhas**.

   * Insira **Visitas** como **Nome da tabela**
   
   * Clique em **Mostrar opções avançadas**

   * Insira a seguinte expressão como **Filtrar linhas**

   ```
     statecode eq 0 and bc_actualstart ne null and bc_actualend eq null and Microsoft.Dynamics.CRM.OlderThanXMinutes(PropertyName='bc_scheduledend',PropertyValue=15)
   ```
   
   * Comandos específicos:
       * **statecode eq 0** filtra por visitas ativas (quando o status está como Ativo)
       * **bc_actualstart ne null** pesquisa apenas visitas em que o Início Real tem um valor. Ex.: fizeram check-in
       * **bc_actualend eq null** pesquisa apenas visitas que não fizeram check-out (Término Real não tem valor) 
       * **Microsoft.Dynamics.CRM.OlderThanXMinutes(PropertyName='bc_scheduledend',PropertyValue=15)** apenas visitas que deveriam ter sido concluídas há mais de 15 minutos.

   * Neste momento, clique nas reticências (**...**) e clique em **Renomear**. Renomeie esta ação **"Listar as visitas ativas que terminaram há mais de 15 minutos"**. Essas ações são importantes para que todos com permissão para editar o fluxo entendam o propósito da etapa sem precisar de maiores detalhes.

6.  Clique em **Nova etapa**. Pesquise por *Aplicar*, selecione a ação **Aplicar a cada** 

7.  Selecione **valor** no conteúdo dinâmico do campo **Selecionar saída para etapas anteriores**. Note que está abaixo do cabeçalho cinza **Listar visitas ativas que terminaram há mais de 15 minutos**. Significa que você está selecionando a lista de visitas que foi consultada na etapa anterior. 

8.  Recuperar dados do Edifício relacionados ao respectivo registro

    * Clique em **Adicionar uma ação** dentro de Aplicar a cada sequência.
    
    * Pesquise por *Atual* e selecione o conector **Common Data Service (Ambiente atual)**. 
    
    * Selecione **Obter uma linha por ID**.
    
    * Selecione **Edifícios** como **Nome da entidade**
    
    * Selecione **Edifício (Valor)** como **ID do Item** no conteúdo Dinâmico
    
    * Clique em **...** ao lado de **Obter um registro**, selecione **Renomear**. Digite **Criar edifício** como nome da etapa
    
9.  Recuperar dados de Visitante do registro relacionado

    * Clique em **Adicionar uma ação** dentro de Aplicar a cada sequência.
    
    * Pesquise por *Atual* e selecione o conector **Common Data Service (Ambiente atual)**.
    
    * Selecione **Obter uma linha por ID**.
    
    * Selecione **Contatos** em **Nome da entidade**
    
    * Selecione **Visitante (Valor)** em **ID do item** no conteúdo dinâmico
    
    * Clique em **...** ao lado de **Obter um registro**, selecione **Renomear**. Digite **Criar visitante** como nome da etapa
    
11.  Enviar notificação por email

     * Clique em **Adicionar uma ação** dentro de Aplicar a cada sequência. Adicione a ação **Enviar uma notificação por email** pela conexão **Email**.

12.  Insira seu endereço de email em **Para**

13.  Insira o seguinte texto no campo **Assunto**. **Nome Completo** é um conteúdo dinâmico da etapa **Criar visitante**.

   ```
   O tempo de visita de {Full Name} foi excedido
   ```
   
14.  Insira o seguinte texto no campo **Corpo da mensagem**. **Nome** é um conteúdo dinâmico da etapa **Criar edifício**.

   ```
   O tempo de permanência foi excedido no edifício {Name}.
         
   Atenciosamente,
         
   Segurança do Campus
   ```

17.  Selecione o nome do fluxo **Sem título** no canto superior esquerdo e renomeie-o para **Varredura de segurança**

18.  Clique em **Salvar**

    Seu fluxo deve ser semelhante ao seguinte:

![Fluxo programado de varredura de segurança - parte 1](media/4-power-automate-security-sweep-flow.png)

## Tarefa #2: Validar e testar o fluxo

Seu fluxo começará a enviar mensagens (para o email que você especificou ao criar o contato John Doe anteriormente) se houver visitas que correspondam aos requisitos definidos no fluxo.

1. Verifique se você tem registros de visitas que:

   1. Têm status ativo
   
   2. O Fim Programado expirou (em mais de 15 minutos)
   
   3. O Início Real tem um valor.
   
   > **Observação**: Para visualizar esses dados, acesse make.powerapps.com em uma nova guia. Clique em Soluções no painel esquerdo para localizar sua solução. Selecione a entidade Visita, depois selecione a guia Dados. Clique em Visitas ativas no canto superior direito para exibir o seletor de visualização e selecione Todos os campos.
   
2. Acesse seu fluxo de **Varredura de Segurança**, caso ainda não esteja lá.

3. Ao abrir o fluxo, clique em **Testar**.

4. Selecione **Manualmente**.

5. Clique em **Salvar e Testar** e **Executar fluxo**.

6. Ao concluir o fluxo, clique em **Concluído**. 

7. Expanda **Aplicar a cada** e, em seguida, expanda a etapa **Enviar uma notificação por email**. Verifique os valores de **Assunto** e **Corpo do email**.

8. Selecione a seta voltar para os detalhes do fluxo de Varredura de segurança. Selecione **Desligar** na barra de comando. Isso evita que o fluxo seja executado através de um agendamento no sistema de teste.

# Desafios

* Adicione Início Real e Término Agendado ao corpo do email.
* Como garantir que uma formatação de interface de data amigável seja usada no corpo do email?
* É possível gerar uma tabela com informações sobre os tempos de permanência excedidos e enviar um único email?
* É possível gerar um código de barras para o código de visita? Quando isso é útil?