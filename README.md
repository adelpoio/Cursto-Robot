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

Este readme fornece uma base sólida para começar a trabalhar com o Robot Framework. Consulte a documentação oficial do Robot Framework e SeleniumLibrary para aprender mais sobre as possibilidades avançadas dessas ferramentas. Boa sorte com seus testes!


