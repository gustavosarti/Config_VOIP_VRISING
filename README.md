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

1. Encontre a pasta save-data/Settings
2. Cole ou crie o arquivo `ServerVoipSettings.json`.
3. Adicione o codigo abaixo com as informações obtidas no vivox.
4. Reinicie o servidor e estará funcionando.
5. Para mais informações: https://mhuijskens.com/vrising/Vivox_V-Rising_How_To.pdf
  
   

**Template do `ServerVoipSettings.json`:**
```json
{
 "VOIPEnabled": true,
 "VOIPIssuer": "",
 "VOIPSecret": "",
 "VOIPVivoxDomain": "mtu1xp.vivox.com",
 "VOIPAPIEndpoint": "",
 "VOIPAppUserId": "notneeded-notused",
 "VOIPAppUserPwd": "notneeded-notused",
 "VOIPConversationalDistance": 14,
 "VOIPAudibleDistance": 40,
 "VOIPFadeIntensity": 2.0
}
