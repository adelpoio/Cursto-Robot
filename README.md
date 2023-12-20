# Projeto de Testes com Robot Framework
Este guia fornecerá instruções passo a passo sobre como iniciar um projeto localmente, configurar as ferramentas necessárias e criar um caso de teste inicial utilizando o Robot Framework.

## Iniciando o Projeto Localmente
1. Clone o Repositório:
bash
git clone https://github.com/seu-usuario/seu-projeto.git
cd seu-projeto

2. Instale as Dependências do Projeto:
bash
pip install -r requirements.txt

## Configurações Necessárias para os Testes
1. Instale o Robot Framework e a Biblioteca SeleniumLibrary:
bash
pip install robotframework
pip install robotframework-seleniumlibrary

2. Baixe o WebDriver do Navegador Escolhido:
Certifique-se de ter o WebDriver apropriado para o navegador escolhido (ChromeDriver, GeckoDriver para Firefox, etc.) e adicione-o ao seu PATH - Neste projeto utilizamos o ChromeDriver.

## Criando um Novo Arquivo de Teste (.robot) 
1. Crie um Novo Arquivo de Teste:
Crie um arquivo com extensão .robot no seu diretório de testes.

2. Estrutura Básica do Teste:
robot
*** Settings ***
Library  SeleniumLibrary

*** Test Cases ***
Meu Primeiro Teste
    Abrir o Navegador e Realizar uma Ação

## Criando um Novo Caso de Teste
1. Utilizando Keywords Nativas:
Adicione as seguintes keywords nativas para abrir o navegador, realizar uma ação e verificar se um elemento está visível:
robot
*** Settings ***
Library  SeleniumLibrary

*** Test Cases ***
Meu Primeiro Teste
    Abrir o Navegador e Realizar uma Ação

*** Keywords ***
Abrir o Navegador e Realizar uma Ação
    Open Browser  http://www.exemplo.com  chrome
    Click Element  id=elemento-de-exemplo
    Input Text     id=caixa-de-texto  Texto de Exemplo
    Element Should Be Visible  id=elemento-visivel
    
## Usando Ferramentas de Desenvolvedor para Identificar Elementos HTML
1. Utilize as Ferramentas de Desenvolvedor do Navegador:
Inspecione a página web para identificar os elementos HTML que serão utilizados como locators nos seus testes.

2. Exemplo de Uso de Locators no Teste:
No exemplo acima, id=elemento-de-exemplo, id=caixa-de-texto e id=elemento-visivel são locators baseados nos atributos id dos elementos HTML.
Lembre-se de personalizar os locators de acordo com os elementos da sua aplicação.

## Criando e Utilizando Variáveis
1. Definindo Variáveis:
Utilize a seção *** Variables *** para definir variáveis que podem ser reutilizadas em todo o arquivo de teste.

2. Utilizando Variáveis em Test Cases e Keywords:
Substitua valores fixos por variáveis, como mostrado no exemplo acima.

## Criando Keywords Específicas
1. Criando Keywords Personalizadas:
Adicione seções *** Keywords *** para definir suas próprias keywords específicas.
Exemplo: Clicar em Elemento e Preencher Caixa de Texto.

## Estruturando Testes para Interação com Usuário e Formulários Incorretos

1. Estrutura para Testes de Formulários Incorretos:
robot
*** Test Cases ***
Teste com Formulário Incorreto
    [Documentation]  Verifica a interação do usuário com um formulário ao preenchê-lo incorretamente
    Abrir o Navegador e Realizar uma Ação
    Preencher Caixa de Texto  ${CaixaTextoID}  InformacaoIncorreta
    Elemento Deve Estar Visível  ${ElementoVisivelID}

2. Criando Keywords para Interação com Formulários:
robot
*** Keywords ***
Preencher Caixa de Texto
    [Arguments]  ${locator}  ${texto}
    Input Text     ${locator}  ${texto}

3. Verificando Elemento Visível com Formulário Incorreto:
robot
Elemento Deve Estar Visível
    [Arguments]  ${locator}
    Wait Until Element Is Visible  ${locator}  10s

## Criando um Novo Teste para Interação com o Usuário
1. Teste para Preenchimento Incorreto do Formulário:
robot
*** Test Cases ***
Teste com Formulário Incorreto
    [Documentation]  Verifica a interação do usuário com um formulário ao preenchê-lo incorretamente
    Iniciar Teste
    Preencher Caixa de Texto  ${CaixaTextoID}  InformacaoIncorreta
    Elemento Deve Estar Visível  ${ElementoVisivelID}
   
2. Keywords Atualizadas para Uso Geral:
robot
*** Keywords ***
Preencher Caixa de Texto
    [Arguments]  ${locator}  ${texto}
    Input Text     ${locator}  ${texto}

Elemento Deve Estar Visível
    [Arguments]  ${locator}
    Wait Until Element Is Visible  ${locator}  10s
    
## Relatórios de Teste e Boas Práticas de Nomenclatura
1. Entendendo Relatórios de Teste:
Execute seus testes e analise os relatórios gerados no final. Eles fornecem insights sobre os resultados e possíveis problemas.

2. Nomenclatura Significativa:
Dê nomes significativos aos seus testes e keywords para facilitar a leitura e compreensão.

## Utilizando Laço FOR e Criando Listas no Robot

1. Exemplo de Uso do Laço FOR e Lista:
robot
*** Variables ***
@{lista_de_dados}   item1  item2  item3

*** Test Cases ***
Utilizando Laco FOR
    :FOR    ${item}    IN    @{lista_de_dados}
    \    Log    Item: ${item}

2. Resultado Esperado:
O exemplo acima imprimirá no log:
makefile
Item: item1
Item: item2
Item: item3

## Utilizando a Biblioteca FakerLibrary para Massa de Dados Dinâmica

1. Instalando a Biblioteca FakerLibrary:
bash
pip install robotframework-faker

2. Exemplo de Uso da FakerLibrary:
robot
*** Settings ***
Library   SeleniumLibrary
Library   FakerLibrary

*** Test Cases ***
Preencher Formulario com Dados Dinamicos
    ${nome}     Generate Random String    8
    ${email}    Generate Email
    ${senha}    Generate Password

    Iniciar Teste
    Preencher Caixa de Texto    ${CaixaTextoID}    ${nome}
    Preencher Caixa de Texto    ${CaixaEmailID}    ${email}
    Preencher Caixa de Texto    ${CaixaSenhaID}    ${senha}
    Elemento Deve Estar Visível  ${ElementoVisivelID}

## Relatórios de Teste e Boas Práticas de Nomenclatura
1. Entendendo Relatórios de Teste:
Execute seus testes e analise os relatórios gerados no final. Eles fornecem insights sobre os resultados e possíveis problemas.

2. Nomenclatura Significativa:
Dê nomes significativos aos seus testes, variáveis e keywords para facilitar a leitura e compreensão.

Este readme ampliado abordou o uso do laço FOR, criação de listas, integração da biblioteca FakerLibrary para criação de massa de dados dinâmica, e reforçou a importância de relatórios de teste e nomenclatura significativa. Consulte a documentação oficial do Robot Framework e SeleniumLibrary para mais informações. Boa sorte com seus testes!
