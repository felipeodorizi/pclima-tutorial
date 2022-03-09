Usage
=====

.. _installation:

Installation
------------

Como Consultar - API 

A ferramenta API (Application Programming Interface, em inglês) tem como objetivo facilitar, para o usuário setorial, o acesso amplo e automatizado de diversos parâmetros de dados das projeções climáticas para o Brasil, de forma flexível quanto ao formato e volume dos dados.

O processo de requisição e extração dos dados seguirão os passos a seguir:

Cadastramento do TOKEN

Para uso em API ‘s o método de autenticação mais recomendado é o base-ado em token. Onde, uma vez que o usuário forneça suas credenciais, o servidor gera um token que autentica o usuário que está fazendo as requi-sições. No portal PCBr, o cadastramento será necessário apenas no primei-ro uso da ferramenta API no portal.

Método para a geração do token

Acessar o formulário disponível no endereço:

http://pclima.inpe.br/analise/API/cadastro.html


Como Consultar - API 

A ferramenta API (Application Programming Interface, em inglês) tem como objetivo facilitar, para o usuário setorial, o acesso amplo e automatizado de diversos parâmetros de dados das projeções climáticas para o Brasil, de forma flexível quanto ao formato e volume dos dados.

O processo de requisição e extração dos dados seguirão os passos a seguir:

1. Cadastramento do TOKEN

Para uso em API ‘s o método de autenticação mais recomendado é o base-ado em token. Onde, uma vez que o usuário forneça suas credenciais, o servidor gera um token que autentica o usuário que está fazendo as requi-sições. No portal PCBr, o cadastramento será necessário apenas no primei-ro uso da ferramenta API no portal.

Método para a geração do token

1 – Acessar o formulário disponível no endereço:

http://pclima.inpe.br/analise/API/cadastro.html

2 – Após acessar o link acima, preencher os campos necessários (Username, Email, etc.), e em seguida clicar no botão POST , conforme é mostrado na figura abaixo (Figura 1). 

Em seguida, você receberá uma página de retorno com a sua chave token – valor mostrado no campo ‘Key’ (Figura 2 ). 

Guarde bem esta chave, você irá usá-la sempre que fizer novas requisições de dados através da aplicação API neste portal.

3 – Você receberá um e-mail de confirmação. Favor, acessar o l i n k recebido em seu e-mail para a confirmação de seu cadastro. O acesso e realização de download dos dados só será possível após a finalização desta etapa.

Pronto! Agora você já pode acessar o Menu API e fazer a requisição dos dados de seu interesse.

2. Menu API (http://pclima.inpe.br/analise/API/)

O item API na página inicial da plataforma, apresenta o seguinte Menu:

Em cada item do MENU, há diversas opções mostradas em azul claro. Selecione a combinação desejada em cada item, adicione o Token e clique em “GERAR URL”.

Após essa etapa será gerado os comandos no formato Wget, no formato cURL e no formato JSON. Os comandos Wget e cURL são mostrados abaixo. 

Escolha o formato Wget ou cURL e execute-o em sua janela de comandos para iniciar o download dos dados. 

Pronto! Verificar em sua janela de comando se o download foi 100% concluído com sucesso.

Escolha o formato JSON para a utilização no Pacote Python 

Utilizando o Pacote PCLIMA Python

O que é um biblioteca Python?

Uma Biblioteca do Python é uma coleção de módulos de script acessíveis a um programa Python para simplificar o processo de programação e remover a necessidade de reescrever os comandos mais usados. Eles podem ser usados chamando-os / importando-os no início de um script.

Como instalar e utlilizar uma biblioteca Python?

No desenvolvimento de projetos Python, precisemos instalar diversas bibliotecas para diferentes necessidades. Porém, não é viável que a instalação dessas bibliotecas seja feita de forma manual, já que o processo de cada uma delas podem ser, no mínimo, complicadas. Para isso, o Python possui uma ferramenta para gerenciamento de pacotes chamado PIP.

PIP é um gerenciador de pacotes para projetos Python. É com ele que instalamos, removemos e atualizamos pacotes em nossos projetos.

O PIP possui uma página (https://pypi.org/) onde nós conseguimos buscar os pacotes disponíveis para a utilização. Nela podemos pesquisar por um pacote específico ou até uma palavra chave. 

Para a instalação do pacote PClima utilizando o PIP, temos o seguinte comando:

pip install apipclima

Após a instalação da biblioteca, basta utilizar o comando import.

Instalação do Token para a biblioteca PCLIMA.

Copiar o Token, no arquivo $HOME/.pclimaAPIrc (em ambiente Unix/ Linux/Mac).

Em Windows colocar o arquivo .pclimaAPIrc no diretório inicial do usuário (ex. C:\User\Cliente)

Conteúdo do arquivo:

Comando HELP

Ele nos fornece uma breve explicação de como implementar o método e informar qual a utilidade dele.

import pclima as pcl
help(pcl) 

Exemplo de uso da API Python 

import pclima as pcl
Client = pcl.Client()
data = Client.getData( { “formato”: “CSV”, “conjunto”: “PR0002”, “modelo”: “MO0003”, “experimento”: “EX0003”, “periodo”: “PE0000”, “cenario”: “CE0001”, “variavel”: “VR0001”, “frequenciaURL”: “Anual”, “frequencia”: “FR0001”, “produto”: “PDT0001”, “localizacao”: “Ponto”, “localizacao_pontos”: “-23.56/-46.62”, “varCDO”: “tasmax” } )
Client.save(data,”file.csv”) 

Utilização da biblioteca Python para intervalo de tempo

Em alguns casos de utilização do Wget e cURL é necessário a recuperação de dados somente definindo um ano ou um mês específico. Utilizando a Biblioteca Python é possível a recuperação de intervalos de tempos, como veremos no exemplo:

Alterar o ano do JSON gerado na Plataforma (“http://pclima.inpe.br/ analise/API/”)

{ “formato”: “NetCDF”, “conjunto”: “PR0002”, “modelo”: “MO0003”, “experimento”: “EX0003”, “periodo”: “PE0000”, “cenario”: “CE0001”, “variavel”: “VR0001”, “frequenciaURL”: “Diario”, “frequencia”: “FR0004”, “produto”: “PDT0001”, “localizacao”: “Area”, “localizacao_pontos”: “-54.39/-42.39/-26.62/-18.23”, “varCDO”: “tasmax”, “ano”: “1961” }

Para

{ “formato”: “NetCDF”, “conjunto”: “PR0002”, “modelo”: “MO0003”, “experimento”: “EX0003”, “periodo”: “PE0000”, “cenario”: “CE0001”, “variavel”: “VR0001”, “frequenciaURL”: “Diario”, “frequencia”: “FR0004”, “produto”: “PDT0001”, “localizacao”: “Area”, “localizacao_pontos”: “-54.39/-42.39/-26.62/-18.23”, “varCDO”: “tasmax”, “ano”: “1961-1963” } 

Nos Casos de CSVPontos e CSVPontosT (Transposta) com a frequência diária é necessário para a recuperação de dados a definição do ano e do mês. Nesses casos também podemos utilizar o intervalo de datas como abaixo:

{ “formato”: “CSVPontos”, “conjunto”: “PR0002”, “modelo”: “MO0003”, “experimento”: “EX0003”, “periodo”: “PE0000”, “cenario”: “CE0001”, “variavel”: “VR0001”, “frequenciaURL”: “Diario”, “frequencia”: “FR0004”, “produto”: “PDT0001”, “localizacao”: “Area”, “localizacao_pontos”: “-54.39/-42.39/-26.62/-18.23”, “varCDO”: “tasmax”, “ano”: “1961-1962“, “mes”: “01-05” } 


