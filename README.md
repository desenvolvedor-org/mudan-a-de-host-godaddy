# Aprenda a mudar de host godaddy sem perder usuarios.
No novo host adicione um dominio que voce nao tenha acesso
exclua o ssl dele, e prociga os passos.

# Primeira forma facil.
## Passo 1
1.1 delete todas as pasta .well-known<br>
1.2 Faça o backu de todos os arquivos e banco de dados<br>

## Passo 2
2.1 verificar a dns do site que voce quer transferir<br>
CNAME	autoconfig	mydominio.org.	10800 segundos<br>
CNAME	autoconfig.admin	mydominio.org.	10800 segundos<br>
CNAME	autodiscover	mydominio.org.	10800 segundos<br>
CNAME	autodiscover.admin	mydominio.org.	10800 segundos<br>
CNAME	webmail	mydominio.org.	10800 segundos<br>
CNAME	webmail.admin	mydominio.org.	10800 segundos<br>
CNAME	_domainconnect	_domainconnect.gd.domaincontrol.com. 1 hora<br>
MX	@	mail.mydominio.org. (Prioridade: 0) 1 hora<br>
TXT	@	v=spf1 a mx ptr include:secureserver.net ~all	1 hora<br>
TXT	admin	v=spf1 a mx ptr include:secureserver.net ~all 1 hora<br>
SRV	_autodiscover._tcp.@	0 0 443 cpanelemaildiscovery.cpanel.net.	1 hora<br>
SRV	_autodiscover._tcp.admin	0 0 443 cpanelemaildiscovery.cpanel.net.	1 hora<br><br>
![Captura de tela 2024-06-27 181854](https://github.com/desenvolvedor-org/mudan-a-de-host-godaddy/assets/66024189/829ca102-caea-4c38-b648-9a574e541c29)
<br><br>
2.2 se caso nao tiver com essas DNS acrescentar<br>
2.3 se caso tive a DNS: {A	@	Parked	600 segundos] deletar por que ela faz uma transferencia insegura.<br>
2.4 transferir todo o backup e banco de dados para o novo host, inclusive fazer a conexao com o banco de dados ja<br>

## Passo 3
3.1 criar um SSL free por seguraça no site: https://www.sslforfree.com/<br>
3.2 baixar o certificado para seu coomputador<br>
3.3 no novo sevidor addicionar o novo site<br>
3.4 verificar a conclusao da mudaça de ip de host no DNS do dominio e no site https://www.whatsmydns.net/<br>
3.5 aguarda termina a mudaça de ip e propagaçao de DNS. nunca excluir o nome de dominio do antigo host, so pode redefinir o host antigo com tudo dentro.<br>

## Passo 4
4.1 depois de concluida a propagaçao do dns instalar os novos certificados SSL<br>
4.2 pode tentar usar o Run auto SSL do Cpanel<br>
4.3 se nao funcionar a opçao 4.2 adicionar manualmente.<br>
4.4 terminar a instaçao com o acme intall automatico de SSL<br>
4.5 se caso o acme nao funcionar por causa do limite execedido deixa o acme funcionando no cron que depois de um tempo ele atualiza todos.


# Segunda forma dificil.
## Passo 1
delete todas as pasta .well-known<br>
1.1 Faça o backu de todos os arquivos e banco de dados<br>

## Passo 2
2.1 Desconecte e exclua todo o vinculo do site no host antigo.<br>
2.2 no cpainel exclua todos os vinculos em dominius e ssl.<br>
2.3 limpe as dns do antigo host<br>

## Passo 3
3.1 coloque todos os backups com os mesmo nome de pastas<br>
3.2 adicione o dominio no novo host<br>

## Passo 4
4.1 na DNS acrescente as DNS abaixo:<br>
CNAME	autoconfig	mydominio.org.	10800 segundos<br>
CNAME	autoconfig.admin	mydominio.org.	10800 segundos<br>
CNAME	autodiscover	mydominio.org.	10800 segundos<br>
CNAME	autodiscover.admin	mydominio.org.	10800 segundos<br>
CNAME	webmail	mydominio.org.	10800 segundos<br>
CNAME	webmail.admin	mydominio.org.	10800 segundos<br>
CNAME	_domainconnect	_domainconnect.gd.domaincontrol.com. 1 hora<br>
MX	@	mail.mydominio.org. (Prioridade: 0) 1 hora<br>
TXT	@	v=spf1 a mx ptr include:secureserver.net ~all	1 hora<br>
TXT	admin	v=spf1 a mx ptr include:secureserver.net ~all 1 hora<br>
SRV	_autodiscover._tcp.@	0 0 443 cpanelemaildiscovery.cpanel.net.	1 hora<br>
SRV	_autodiscover._tcp.admin	0 0 443 cpanelemaildiscovery.cpanel.net.	1 hora<br><br>
![Captura de tela 2024-06-27 181854](https://github.com/desenvolvedor-org/mudan-a-de-host-godaddy/assets/66024189/829ca102-caea-4c38-b648-9a574e541c29)
<br><br>
veja o modelo que deve ficar:<br><br>
![Captura de tela 2024-06-27 184054](https://github.com/desenvolvedor-org/mudan-a-de-host-godaddy/assets/66024189/5109e2a8-f50a-48aa-a28a-bfc6150c61ed)
<br>
![Captura de tela 2024-06-27 184242](https://github.com/desenvolvedor-org/mudan-a-de-host-godaddy/assets/66024189/1dd9d2f7-a9d8-4bd2-92bd-8b9125966e71)
<br>
![Captura de tela 2024-06-27 184333](https://github.com/desenvolvedor-org/mudan-a-de-host-godaddy/assets/66024189/e4450652-008d-43a4-9e09-18251f4973fc)
<br><br>
## Passo 5
5.1 exclua o ssl automatico<br>
5.2 adicione o novo ssl no run auto ssl.<br>
5.3 aguarde 20 minutos para o dns se propagar<br>
5.4 teste no navegador tor em 5 minutos para ver a DNS se propagando



