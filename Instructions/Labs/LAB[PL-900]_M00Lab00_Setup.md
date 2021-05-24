---
lab:
    title: 'Laboratório: Validar ambiente de laboratório'
    module: 'Módulo 0: Introdução ao curso'
---

Módulo 0: Introdução ao curso
=================================

## Laboratório: Validar ambiente de laboratório

### Aviso importante (em vigor em novembro de 2020):
O Common Data Service foi renomeado como Microsoft Dataverse. Alguns termos no Microsoft Dataverse foram atualizados. Por exemplo, o termo entidade agora é tabela. Os campos e registros nos bancos de dados do Dataverse agora são chamados de colunas e linhas.

Embora os aplicativos estejam em processo de atualização da experiência do usuário, algumas referências à terminologia do Microsoft Dataverse, como entidade (agora **tabela**), campo (agora **coluna**) e registro (agora **linha**), podem estar desatualizadas. Lembre-se disso ao trabalhar nos laboratórios. Esperamos atualizar todo o conteúdo em breve. 

Para obter mais informações e uma lista completa dos termos afetados, visite [O que é o Microsoft Dataverse?](https://docs.microsoft.com/pt-br/powerapps/maker/common-data-service/data-platform-intro#terminology-updates)

Cenário
--------

O Bellows College é uma organização educacional com vários edifícios no campus. Atualmente, os visitantes do campus são registrados em um diário de papel. As informações não são capturadas de forma consistente e não há meios de coletar e analisar dados sobre as visitas em todo o campus.

A administração do campus gostaria de modernizar seu sistema de registro de visitantes, onde o acesso aos edifícios fosse controlado pelo pessoal da segurança e todas as visitas fossem pré-registradas e gravadas por seus anfitriões.

Ao longo deste curso, você criará aplicativos e realizará a automação para permitir que a administração e o pessoal da segurança do Bellows College gerenciem e controlem o acesso aos edifícios do campus.

Neste laboratório do Módulo 0, você irá adquirir um locatário de teste da Power Platform e acessar o centro de administração da Power Platform. No centro de administração, você criará o seu ambiente de **Prática** no qual fará a maior parte do trabalho do laboratório.

## Exercício 1 – Configuração

### Tarefa 1 – Adquirir o locatário de teste da Power Platform

1. Copie as **Credenciais do Microsoft 365** do Authorized Lab Hoster.

2. Navegue até <https://powerapps.microsoft.com> e clique em **Comece gratuitamente.**

3. Em **Vamos começar**, insira o endereço de email das suas credenciais do Microsoft 365 na caixa de texto que diz **Insira seu endereço de email corporativo.**

4. Será exibido um aviso informando que você tem uma conta na Microsoft. Selecione **Entrar.**

5. Digite a senha fornecida pelo Authorized Lab Hoster. 

6. Selecione **Sim** para permanecer conectado.

### Tarefa 2 – Criar o ambiente

1.  Acesse <https://admin.powerplatform.microsoft.com> e faça login com as suas credenciais do Microsoft 365 se for solicitado novamente.

2. Selecione **Ambientes** e clique em **+Novo.**

    - Em **Nome**, insira **Prática [Minhas iniciais].** (Exemplo: Prática AJ.)
    
    - Em **Tipo**, selecione **Teste** (não selecione a opção Teste (com base em assinatura)).
    
    - Altere o botão **Criar um banco de dados para este ambiente?** para **Sim.**
    
    - Deixe todas as outras seleções como padrão e clique em **Avançar.**
    
    - Na próxima guia, deixe todas as seleções como padrão e clique em **Salvar.**

3. Seu ambiente de **Prática** agora deve aparecer na lista Ambientes. 

    > O ambiente pode levar alguns minutos para ser provisionado. Se necessário, atualize a página.

# Exercício 2: Provisionar um portal do Power Apps

**Objetivo:** O provisionamento de um portal do Power Apps pode levar algum tempo. Neste exercício, você criará o portal do Power Apps no seu ambiente para que o processo de provisionamento possa ser iniciado. Você usará este portal em um laboratório posterior.

## Tarefa 1: Criar o portal do Power Apps

1.  Faça login em <https://make.powerapps.com>

2.  Se o **Ambiente** exibido no canto superior direito não for seu ambiente de Prática, clique para selecionar o seu Ambiente.

3.  Na página inicial, clique no painel **Portal a partir do zero** em **Criar seu próprio aplicativo**

    > Se você não vir esta opção, tente diminuir o zoom.

4.  Forneça novos detalhes para o portal

    -   Digite **Visitantes do Bellows College** como o **Nome** do portal

    -   Forneça um URL exclusivo; **algumacoisa**.powerappsportals.com (se o nome já estiver sendo usado, escolha outro)

    -   Selecione um **Idioma** para o portal de base

    -   Clique em **Criar**

    > O processo de provisionamento do Portal será executado em 30 a 45 minutos. Não é necessário esperar, pois esse processo continua enquanto você avança para o próximo módulo.
