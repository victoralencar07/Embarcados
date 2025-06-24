📚 ECOP11A_Rasp-Attend
Projeto: Controle de Presença via Raspberry Pi como Access Point WiFi
Este projeto tem como objetivo utilizar uma Raspberry Pi como ponto de acesso WiFi (Access Point) para gerenciar a presença de alunos em uma sala de aula. Os alunos deverão inserir nome e matrícula para obter acesso à internet.

🎯 Objetivo Geral
Criar um sistema de login por rede WiFi hospedado na Raspberry Pi, onde os usuários (alunos) se conectam à rede sem senha ou com senha fixa, e são redirecionados para uma tela de login onde devem informar:

Nome Completo
Matrícula
Após o login bem-sucedido, o aluno terá acesso à internet e sua presença será registrada.

🧩 Etapas Realizadas
✅ 1. Instalação do RaspOS Lite
Sistema operacional usado: Raspberry Pi OS Lite (32-bit)
Gravado no SD Card usando Raspberry Pi Imager
Configurações iniciais:
SSH ativado (criando arquivo vazio ssh na partição boot)
Conexão WiFi configurada via wpa_supplicant.conf
IP estático configurado (opcional)

✅ 2. Acesso Remoto via SSH com Chave Pública
Gerado par de chaves SSH:
bash
ssh-keygen -t ed25519 -C "seu_email@example.com"
Adicionada chave pública à Raspberry Pi:

~/.ssh/authorized_keys
Definidas permissões seguras:
bash

chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
profile
Qwen3-235B-A22B
Claro! Abaixo está o conteúdo completo de um arquivo README.md pronto para seu repositório no GitHub, com toda a documentação das etapas realizadas até agora.

Você pode copiar e colar diretamente no GitHub ou salvar localmente como README.md.

📚 ECOP11A_Rasp-Attend
Projeto: Controle de Presença via Raspberry Pi como Access Point WiFi
Este projeto tem como objetivo utilizar uma Raspberry Pi como ponto de acesso WiFi (Access Point) para gerenciar a presença de alunos em uma sala de aula. Os alunos deverão inserir nome e matrícula para obter acesso à internet.

🎯 Objetivo Geral
Criar um sistema de login por rede WiFi hospedado na Raspberry Pi, onde os usuários (alunos) se conectam à rede sem senha ou com senha fixa, e são redirecionados para uma tela de login onde devem informar:

Nome Completo
Matrícula
Após o login bem-sucedido, o aluno terá acesso à internet e sua presença será registrada.

🧩 Etapas Realizadas
✅ 1. Instalação do RaspOS Lite
Sistema operacional usado: Raspberry Pi OS Lite (32-bit)
Gravado no SD Card usando Raspberry Pi Imager
Configurações iniciais:
SSH ativado (criando arquivo vazio ssh na partição boot)
Conexão WiFi configurada via wpa_supplicant.conf
IP estático configurado (opcional)
✅ 2. Acesso Remoto via SSH com Chave Pública
Gerado par de chaves SSH:
bash

ssh-keygen -t ed25519 -C "seu_email@example.com"
Adicionada chave pública à Raspberry Pi:

~/.ssh/authorized_keys
Definidas permissões seguras:
bash

chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys


✅ 3. Configuração da Raspberry Pi como Access Point WiFi
🔧 Configurações Realizadas:
IP Estático para wlan0: 192.168.4.1
Servidor DHCP ativo (dnsmasq)
Serviço HostAPD configurado com:
SSID: Rasp_Attend
Senha: minhasenha123
Arquivos modificados:
/etc/dhcpcd.conf
ini

interface wlan0
static ip_address=192.168.4.1/24
/etc/hostapd/hostapd.conf
ini

interface=wlan0
ssid=Rasp_Attend
hw_mode=g
channel=7
wmm_enabled=0
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=minhasenha123
wpa_key_mgmt=WPA-PSK
rsn_pairwise=CCMP
/etc/dnsmasq.conf
ini


interface=wlan0
dhcp-range=192.168.4.2,192.168.4.20,255.255.255.0,24h

✅ 4. Diagnóstico e Correção de Problemas Comuns
Erro Comum:

Permission denied (publickey)
Solução Aplicada:
Verificação de existência da chave pública no arquivo:


~/.ssh/authorized_keys
Correção de permissões:
bash

chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
Garantia de que os arquivos pertençam ao usuário correto:
bash

sudo chown -R pi:pi 
