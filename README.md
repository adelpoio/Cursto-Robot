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


   
Este readme ampliado oferece uma base sólida para trabalhar com Robot Framework, incluindo a criação de variáveis, keywords personalizadas e testes para interação com formulários incorretos. Consulte a documentação oficial do Robot Framework e SeleniumLibrary para mais informações. Boa sorte com seus testes!
