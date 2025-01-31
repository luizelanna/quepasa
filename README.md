<p align="center">
	<img src="https://github.com/nocodeleaks/quepasa/raw/main/src/assets/favicon.png" alt="Quepasa-logo" width="100" />	
	<p align="center">Quepasa é um software de código aberto, totalmente gratuito, para troca de mensagens com a plataforma Whatsapp</p>
</p>
<hr />
<p align="left">
</p>
<hr />
<p align="left">
	<img src="https://whatsapp.com/favicon.ico" alt="WhatsAPP-logo" width="32" />
	<span>Grupo WhatsaAPP Chatwoot : </span>
	<a href="https://chat.whatsapp.com/CLKge3hmHmmBcIL04mBzmT" target="_blank">Grupo</a>
<hr />
<p align="left">
	<img src="https://whatsapp.com/favicon.ico" alt="WhatsAPP-logo" width="32" />
	<span>Grupo WhatsaAPP Quepasa: </span>
	<a href="https://chat.whatsapp.com/Cv5WfmujRzE09yQ6hagYim" target="_blank">Grupo</a>
</p>
<hr />
<p align="left">
	<img src="https://whatsapp.com/favicon.ico" alt="WhatsAPP-logo" width="32" />
	<span>Grupo WhatsaAPP N8N: </span>
	<a href="https://telinkei.com/gp-n8n-zap" target="_blank">Grupo</a>
</p>
<hr />
<hr />

**Gostou do Tutorial? Faça sua Contribuição**

<img src="https://github.com/EngajamentoFlow/quepasa/blob/main/Contribui%C3%A7%C3%A3o.png" alt="Quepasa-logo" width="200" />
</p>

**PIX CNPJ**

```
45959142000119	
```

<hr />
<hr />


**Manual de Instalação ChatWoot**

sudo apt update && apt upgrade -y
</p>
wget https://get.chatwoot.app/linux/install.sh
</p>
chmod +x install.sh
</p>
./install.sh --install
</p>
Use as opções abaixo
</p>
yes
</p>
chatwoot.dominio.com.br
</p>
contato@dominio.com.br
</p>
yes para todos
</p>
<hr />

**Alterando Idioma e ativando sua tela de cadastro**

</p>
cd /home/chatwoot/chatwoot
</p>
nano .env
</p>
Altere a linha
</p>
DEFAULT_LOCALE=pt_BR
</p>
ENABLE_ACCOUNT_SIGNUP=true
</p>
sudo systemctl restart chatwoot.target
</p>
Acesse: seudominio.com.br
</p>
Faça seu cadastro
</p>

<hr />

**Habilitando configurações ocultas do Chatwoot**

</p>
No banco de dados PostgreSQL
</p>
sudo -u postgres psql
</p>
\c chatwoot_production
</p>
update installation_configs set locked = false;
</p>
\q
</p>

<hr />

**NOMES CHATWOOT TERMOS E POLITICA DE PRIVACIDADE**

**Acesse super Admin**
</p>
https://seudominio.com.br/super_admin
</p>
Opção>installation_configs
</p>
LOGO
</p>
LOGO_THUMBNAIL
</p>
NOMES CHATWOOT:
</p>
Alterando nomes na plataforma
</p>
INSTALLATION_NAME
</p>
BRAND_NAME
</p>
TERMOS E POLITICA DE PRIVACIDADE
</p>
TERMS_URL
</p>
PRIVACY_URL
</p>
BRAND_URL
</p>
WIDGET_BRAND_URL
</p>

<hr />
<hr />

**Manual de Instalação N8N**


</p>
sudo apt update && sudo apt upgrade y
</p>
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
</p>
sudo apt-get install -y nodejs
</p>
node -v
</p>
sudo npm install n8n -g
</p>
npm update -g n8n
</p>
sudo apt install npm
</p>
npm install pm2 -g
</p>
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
</p>
sudo apt install ./google-chrome-stable_current_amd64.deb
</p>
sudo nano /etc/nginx/sites-available/n8n
</p>
</p>
</p>

```
server {

  server_name n8n.dominio.com.br;

  location / {

    proxy_pass http://127.0.0.1:5678;

    proxy_http_version 1.1;

    proxy_set_header Upgrade $http_upgrade;

    proxy_set_header Connection 'upgrade';

    proxy_set_header Host $host;

    proxy_set_header X-Real-IP $remote_addr;

    proxy_set_header X-Forwarded-Proto $scheme;

    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_cache_bypass $http_upgrade;

    proxy_buffering off;

    proxy_cache off;

  }

  }
  ```

</p>
</p>
</p>
sudo ln -s /etc/nginx/sites-available/n8n /etc/nginx/sites-enabled
</p>
sudo certbot --nginx
</p>
sudo service nginx restart
</p>
</p>
pm2 start n8n --cron-restart="0 0 * * *" -- start
</p>

**EXECUTE COMANDO ABAIXO PARA NÃO CAIR QUANDO REINICIAR A VPS**

</p>
sudo pm2 startup ubuntu -u root && sudo pm2 startup ubuntu -u root --hp /root && sudo pm2 save
</p>
cd 
</p>
git clone https://github.com/EngajamentoFlow/quepasa
</p>
export N8N_EDITOR_BASE_URL=https://seudominio.com.br
</p>
export WEBHOOK_URL=https://seudominio.com.br
</p>
nano /root/.n8n/.env
</p>
Abaixo altere C8Q_QP_DEFAULT_USER=coloque email do Quepasa, C8Q_CW_PUBLIC_URL=dominiochatwoot
</p>

```
# enable a single conversation per contact, for all life time, not just a ticket
C8Q_SINGLETHREAD=false

# used by ChatwootToQuepasa
C8Q_QUEPASAINBOXCONTROL=7

# used by ChatwootToQuepasa | QuepasaToChatwoot
C8Q_QUEPASACHATCONTROL=6

# used by ChatwootToQuepasa
C8Q_CHATWOOTPROFILEUPDATE=1

# used by QuepasaToChatwoot
C8Q_POSTTOCHATWOOT=4

# used by QuepasaToChatwoot
C8Q_POSTTOWEBCALLBACK=8

# used by QuepasaToChatwoot
C8Q_CHATWOOTTOQUEPASAGREETINGS=3

C8Q_QP_DEFAULT_USER=coloque email do Quepasa

# get initial from $N8N_HOST, otherwise from here
C8Q_CW_PUBLIC_URL=dominiochatwoot
```

</p>
ln -s ./.n8n/.env .env
</p>
pm2 restart all --update-env
</p>


<hr />
<hr />

**Manual de Instalação API Quepasa**

</p>

```
git clone https://github.com/nocodeleaks/quepasa /opt/quepasa-source
bash /opt/quepasa-source/helpers/install.sh
```


</p>

</p>
sudo nano /etc/nginx/sites-available/quepasa
</p>


```
server {

  server_name quepasa.dominio.com.br;

  location / {

    proxy_pass http://127.0.0.1:31000;

    proxy_http_version 1.1;

    proxy_set_header Upgrade $http_upgrade;

    proxy_set_header Connection 'upgrade';

    proxy_set_header Host $host;

    proxy_set_header X-Real-IP $remote_addr;

    proxy_set_header X-Forwarded-Proto $scheme;

    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    
    proxy_cache_bypass $http_upgrade;

  }

  }
```

sudo ln -s /etc/nginx/sites-available/quepasa /etc/nginx/sites-enabled
</p>
</p>
sudo certbot --nginx
</p>
sudo service nginx restart
</p>
</p>

<hr />

**Ativando SSL da API Quepasa**

nano /opt/quepasa-source/src/.env
</p>
Alterar linha 1
</p>
WEBSOCKETSSL=false
</p>
para
</p>
WEBSOCKETSSL=true
</p>
systemctl restart quepasa
</p>

<hr />

***Execute esse processo abaixo parra deixar mais rapida sua API**

nano /etc/hosts

Adicione isso na primeira linha 
127.0.0.1       localhost app.dominio.com.br conector.dominio.com.br api.dominio.com.br

<hr />

**Instalação Finalizadas**

</p>
quepa.dominio.com.br/setup
</p>
Faça os cadastros em todos eles
</p>

</p>

<hr />
<hr />

**Baixe Worflows**

</p>
https://github.com/nocodeleaks/quepasa
</p>
Worflows esta na pasta 
</p>
extra/n8n+chatwoot
</p>

<hr />
<hr />

**Configue os Worflows no N8N**

Adicione nodes ao seu N8N
</p>
n8n-nodes-chatwoot
</p>
n8n-nodes-quepasa
</p>
Acesse opção Credenciais, adicione suas credenciais Postgres, salve.
</p>
Adicione seu email NO COLOCAR DADOS

<hr />

</p>

**Criando sua Caixa de Entrada**

</p>
Envia uma mensagem para Contato Criado
</p>
Quepasa Control
</p>
/qrcode
</p>
Leia QRCODE
</p>

<hr />
<hr />

**Pronto tudo Funcionando**

<hr />
<hr />

**Gostou do Tutorial? Faça sua Contribuição**

<img src="https://github.com/EngajamentoFlow/quepasa/blob/main/Contribui%C3%A7%C3%A3o.png" alt="Quepasa-logo" width="200" />
</p>


**PIX CNPJ**

```
45959142000119	
```

<hr />
<hr />
