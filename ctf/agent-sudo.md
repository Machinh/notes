# Agent Sudo máquina do tryhackme

# Enumeração
comecei a máquina fazendo reconhecimento, usei nmap para me dar uma luz geral ```nmap 10.10.231.2```
o nmap encontrou 3 serviços no ar -> 21/ftp, 22/ssh, 80/http logo que vi o http fui na página web 
enumerei os subdomínios usando Gobuster ```gobuster dir -u 10.10.231.2 -w common.txt```
não encontrei NADA, fiquei perdido por um tempo tentando entender a pista da página: ```Dear agents,
Use your own codename as user-agent to access the site. From, Agent R```
essa era a única pista que eu tinha, depois de muito tempo pensando pensei em como utilizar o user-agent
do agente "R" depois de dar uma pesquisada na internet usei um parâmetro do curl como spoofing pra tentar
me conectar como o agente "R" ```curl -A "R" -L http://10.10.231.2/``` ao site, não deu certo também mas não foi em vão,recebi isso de resposta: 

```What are you doing! Are you one of the 25 employees? If not, I going to report this incident```
nessa parte eu tinha certeza que não iria mais parar até terminar, mas não foi isso que aconteceu
fiquei um tempinho pensando de novo nessa pista uns 3 minutos, logo depois percebi que eles tinham 25 usuários no total baseado nno "25 employees"
e logo fui testando mais usuários aleatóriamente, assim como fiz com o agente "R" mas nenhum funcionou até eu testar o agente "C" e recebi isso:

```Attention chris, Do you still remember our deal? Please tell agent J about the stuff ASAP. Also, change your god damn password, is weak!```
o nome "Chris" pode ser uma pista, mas eu fui logo no agente "J", obviamente fiz um BF (brute force) na senha dele, a questão era só "no ssh ou no ftp?"
então pensei logo em seguida, na dúvida faz nos dois
