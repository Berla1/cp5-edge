
## Descrição do projeto 

O projeto consiste em um LDR que recebe dados de luminosidade capturados, e um DHT22 que recebe dados de temperatura e humidade. Todas as informações coletadas são enviadas ao servidor externo, nesse caso, o Node-red.

## Requisitos

- Conexão WiFi
- Node-red
- Bibliotecas:
  - PubSubClient
  - WiFi
  - DHT sensor library for ESPx
 
## Utilizando Node-red

<img src="https://cdn.xingosoftware.com/elektor/images/fetch/dpr_1,w_800,h_460,c_fit/https%3A%2F%2Fwww.elektormagazine.com%2Fassets%2Fupload%2Fimages%2F42%2F20200612144414_Node-Red-official-logo.png" alt="Logo formulaE" width = "1000"/>

1. Instale o Node.js através do link https://nodejs.org/pt
   
2. Com o Node instalado o comando `npm install -g --unsafe-perm node-red` pode ser utilizado no terminal para instalar o Node-red.
  
3. Se tudo ocorrer bem na instalação a saída esperada é algo similar a isso:
```
+ node-red@1.1.0
added 332 packages from 341 contributors in 18.494s
found 0 vulnerabilities
```
4. Com a instalação feita, o comando `node-red` deve ser ulitizado para rodar o servidor do Node-red, e se tudo ocorrer como esperado a saída esperada é algo similar a isso:
   ```
   Welcome to Node-RED
    ===================
    
    30 Jun 23:43:39 - [info] Node-RED version: v1.3.5
    30 Jun 23:43:39 - [info] Node.js  version: v14.7.2
    30 Jun 23:43:39 - [info] Darwin 19.6.0 x64 LE
    30 Jun 23:43:39 - [info] Loading palette nodes
    30 Jun 23:43:44 - [warn] rpi-gpio : Raspberry Pi specific node set inactive
    30 Jun 23:43:44 - [info] Settings file  : /Users/nol/.node-red/settings.js
    30 Jun 23:43:44 - [info] HTTP Static    : /Users/nol/node-red/web
    30 Jun 23:43:44 - [info] Context store  : 'default' [module=localfilesystem]
    30 Jun 23:43:44 - [info] User directory : /Users/nol/.node-red
    30 Jun 23:43:44 - [warn] Projects disabled : set editorTheme.projects.enabled=true to enable
    30 Jun 23:43:44 - [info] Creating new flows file : flows_noltop.json
    30 Jun 23:43:44 - [info] Starting flows
    30 Jun 23:43:44 - [info] Started flows
    30 Jun 23:43:44 - [info] Server now running at http://127.0.0.1:1880/red/
    ```
5. Agora você já pode acessar a aplicação através do endereço `http://127.0.0.1:1880/` no seu navegador.

## Utilizando simulação no Wokwi

A simulação pode ser acessada através do link: https://wokwi.com/projects/409891028149852161

Para rodar o projeto, basca clicar no botão de 'play' em verde na simulação do Wokwi, se tudo ocorrer bem as informações serão publicadas no tópico especificado, os valores de luminosidade, temperatura e humidade podem ser editados de maneira manual clicando nos dispositivos LDR e DHT22.

## Conexão entre Node-red e Wokwi

1. Com a plataforma do Node-red aberta, o bloco de "debug" na seção "comum" e três blocos "mqtt in" na seção "rede" devem ser arrastados para o meio do fluxo, e conectados entre si, o resultado deve ser algo semelhante a:
   
   <img src="https://i.imgur.com/oUw23d2.png"/>
2. Com um duplo clique no bloco "mqtt in" o tópico: `/TEF/device010/servo/attrs/r` deve ser inserido no campo de tópico, dessa maneira:

   <img src="https://i.imgur.com/ArgpKaH.png"/>

3. Clicando no botão de + no campo de "Servidor", um nome deve ser passado ao servidor que será criado, pode ser um nome de sua escolha. No campo de servidor, o IP `18.208.160.16` e a porta `1883` devem ser inseridos, e o botão vermelho de adcionar pode ser clicado para adicionar o novo servidor:

   <img src="https://i.imgur.com/Vf4AArF.png" />

4. Agora tudo está pronto para receber dados da simulação do Wokwi, basta clicar no botão vermelho "Implementar" no canto superior direito da tela.

 5. Com a tela dividida entre simulação do Wokwi rodando e o Node-red aberto, os dados serão transmitidos:
    
    <img src="https://i.imgur.com/gZlMAxZ.png"/>


## Detalhe

Este é um projeto acadêmico feito na instituição FIAP em conjunto com a empresa e montadora de carros de Fórmula E Mahindra.

<img src="https://store.fiaformulae.com/on/demandware.static/-/Sites-navigation-catalog-FE-S9/default/dw8427c471/LogosTeams/LogoMahindra2.png" alt="Logo Mahindra" width="300"/><img src="https://play-lh.googleusercontent.com/qRAt8XQzsRcEG7LGb7dwOBTuNocOV-lokZjZot4xwIv6wDfgAeFFB5HKkKb8VqZhHNc=w240-h480-rw" alt="Logo formulaE2" width="200"/> <img src="https://avatars.githubusercontent.com/u/79948663?s=200&v=4" alt="Logo FIAP" width="200"/>



