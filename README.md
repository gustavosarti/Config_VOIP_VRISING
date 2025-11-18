# Configuração de VoIP (Vivox) para Servidor Dedicado V Rising

Este guia explica como ativar o chat de voz (VoIP) nativo em um servidor dedicado de V Rising. O jogo utiliza o serviço **Vivox** da Unity, e este tutorial mostrará como se registrar gratuitamente, obter as chaves de API necessárias e configurar seu servidor.

## Arquivo de Exemplo

Este repositório contém um arquivo de modelo:
* `ServerVoipSettings.json.example`

O objetivo é que você siga os passos abaixo para obter suas chaves, baixe (ou copie) o conteúdo deste arquivo, renomeie-o para `ServerVoipSettings.json`, preencha com suas chaves e o coloque na pasta correta do seu servidor.

> **⚠️ AVISO DE SEGURANÇA:** O arquivo final `ServerVoipSettings.json` conterá sua `VOIPSecret` (Chave Secreta). **Nunca** envie este arquivo para um repositório **público**. Use este template apenas como exemplo.

---

## Passo a Passo para Ativar o VoIP

O processo é dividido em três partes: obter as credenciais na Unity, configurar o servidor e ativar a opção no jogo.

### Parte 1: Obtendo as Credenciais no Painel da Unity (Vivox)

Você precisa de 4 chaves de API de um projeto Vivox.

1.  Acesse o [Unity Dashboard](https://dashboard.unity3d.com) e crie uma conta gratuita ou faça login.
2.  No painel principal, clique em **"Create project"**. Dê um nome a ele (ex: "Meu Servidor V Rising").
3.  Após criar o projeto, no menu à esquerda, clique em **"Products"** (ou "Explore services").
4.  Encontre e selecione **"Voice and Text Chat (Vivox)"**.
5.  Na tela de configuração (`Select engine`), mantenha **"Unity"** selecionado e confirme.
6.  Na etapa **"Link Unity project"**, você pode **IGNORAR** tudo. Apenas clique em **"Next"** (Próximo) no final da página. Esta etapa é para desenvolvedores de jogos, não para servidores dedicados.
7.  Você chegará à página final, que mostrará suas **"Credenciais"** (Credentials). Você verá 4 chaves. Mantenha esta página aberta.

Você precisará copiar os seguintes 4 valores:
* `Servidor` (Server / API Endpoint)
* `Domínio` (Domain)
* `Emissor do token` (Token Issuer)
* `Chave do token` (Token Key)

### Parte 2: Configurando o Servidor

Agora, vamos dizer ao seu servidor V Rising para usar essas chaves.

1.  **Pare o seu servidor dedicado.** (Este é um passo crucial!)
2.  Acesse a pasta de saves do seu servidor. O caminho padrão no Windows é:
    `%USERPROFILE%\AppData\LocalLow\Stunlock Studios\VRisingServer\Saves\`
3.  Entre na pasta da versão (ex: `v1`, `v2` ou `v3`).
4.  Entre na pasta do seu save (o `SaveName` definido no seu `ServerHostSettings.json`, por exemplo, `FOFOCA`).
5.  Dentro da pasta do seu save, crie uma nova pasta chamada `Settings` (se ela ainda não existir).
6.  O caminho final será parecido com: `...\Saves\v1\FOFOCA\Settings`
7.  Crie um novo arquivo de texto dentro da pasta `Settings` e renomeie-o para `ServerVoipSettings.json`.
8.  Abra este arquivo e cole o conteúdo do `ServerVoipSettings.json.example` (ou copie o código abaixo) e **preencha** com as 4 chaves que você obteve na Parte 1.

**Template do `ServerVoipSettings.json`:**
```json
{
  "VOIPEnabled": true,
  "VOIPIssuer": "COLE_SEU_EMISSOR_DO_TOKEN_AQUI",
  "VOIPSecret": "COLE_SUA_CHAVE_DO_TOKEN_AQUI",
  "VOIPVivoxDomain": "COLE_SEU_DOMINIO_AQUI",
  "VOIPAPIEndpoint": "COLE_SEU_SERVIDOR_(API_ENDPOINT)_AQUI",
  "VOIPConversationalDistance": 25,
  "VOIPAudibleDistance": 40,
  "VOIPFadeIntensity": 1.5
}
