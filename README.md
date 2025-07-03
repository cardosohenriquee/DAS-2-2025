# DAS2-2025
HENRIQUE MARQUES CARDOSO

# AULA 27/02 #

Cache fica entre a aplicação e o banco. 
Cache guarda informação em memória, é consultado antes de consultar o banco.
Cache pode sobrecarregar a memória ram
Abre a mão de durabilidade pela performance

Banco, fonte de memória persistente

Primeira forma normal - reduzir redundância


aumentar disponibilidade de um sistema que tem limitação na linguagem - aumentar o número de computadores 
scale out - utiliza de servidores extras durante período pré definido afim de aumentar disponibilidade

# AULA 06/03 #


Trade Off - Fornecido pela nuvem, aloca servidores em momentos de pico de acesso e depois retira os mesmos do ar
IAC Infraestructure as code
Acoplamento é quando uma parte não pode ser substituida, pois outras partes precisam dela

ELB (Elastic Load Balancing) Distribuição de tarefas, melhorando perfomance
Se a máquina não estiver ativa, o load balance não envia os dados
Fazendo com que elas sejam facilmente substituiveis, sem acoplamento

Serviço precisa rodar em algum ambiente, pode não ser na máquina, por conta da disponibilidade

escalabilidade horizontal
replicas de leitura de bancos --> gargalo do banco relacional

# AULA 10/03

região - região que possui uma infra da aws
zone - conjunto de datacenters
az - diversas zonas

local zone < az

shared responsibility
aws - infrasestrutura de hardware
cliente - todo o resto

provedor de identidade forte
proteger dados em transito e repouso
segurança em todas camadas
people away from data
rastreabilidade
preparar para eventos de segurança
automatizar segurança

customer ---> iam policy ---> data

least privilege - dba mexe no banco e apenas - usuário mexe apenas oonawawdsaawde 

# AULA 13/03

responsabilidade compartilhada --> cada parte tem sua responsabilidade (aws - hardware, cliente - software)

console --> inteface web da aws
acesso cosole
acesso programático --> assume um sfotware para controlar o console
via aws cli, swa sdk ou api rest

access key
secret acesses key --> mostrada apenas uma vez na hora da criação, podendo editar, excluir e criar novas

criar grupos para padronização de permissão
facilita gerenciamento

# AULA 17/03

usuário root - usuário Deus
padrão de permissionamento --> RBAC - de acordo com o papel, suas permissões são definidas

policies gerenciada --> pronta para uso e manutenção da aws proativa
arn amazon resource name 

policie de recurso --> vai no recurso e escreve um documento com as permissões pelo código --> não tem permissão para mexer em permissão via IAM

verificar permissões na hora da ação
usuário sem permissão nem loga na plataforma

tipo de armazenamento
- armazenamento por bloco (suportam edição no meio do arquivo) EBS
- armazenamento por arquivo (máquina trocando arquivos através do servidor) EFS ou FXs
- armazenamento em objeto (tag) S3

# AULA 20/03 #

limite bucket
5 tera por objeto - standard


arquivos são chamados de objeto porque o s3 guarda binario mais metadado
buckets globalmente únicos
nome do arquivo faz parte da url publica

pastas são os prefixos - não existe pasta
5gb< multipart uploads


storage class - forma com que o s3 guarda informação
define preço e disponibilidade do arquivo

# classe quentes, acesos instantaneo ao objeto #
GENERAL PUPOSE - s3 standard - preço de download mais barato, preço de armazenamento mais caro de todos - nenhum alteração feita na configuração

INTELLIGENT TIERING - s3 intelligence tireinf - 

INFREQUENT ACCESS - s3 standard ia - poucos acessos no mês, armazenamento mais barato e download mais caro que s3 standard

INFREQUENT ACCESS - s3 one zone ia - arquivo de fácil disponibilidade -perde na durabilidade (11 9's) ao invés de fazer 3 cópias, faz uma - armazenamento mais barato e download mais caro que s3 standard

# classe frias - acesso não instantaneo #
ARCHIVE - s3 glacier instant retrieval - volta o arquivo em milisegundos - armazenamento e download caro

ARCHIVE - s3 glacier flexible retrieval - tempo menor de download - minutos a horas para voltar o arquivo - um pouco mais caro para guardar, mas volta mais rápido

ARCHIVE - s3 glaicer deep archive - 12 a 48 horas para download, backup de 10 anos, notas fiscais antigas - armazenamento mais barato download caro

ARCHIVE - s3 on outposts - servidor físico para empresas - máximo 96 hacks

# AULA 24/03 #

lifecycles s3 - conjunto de regras para transacionar entre classes ou apagar um arquivo MEGA IMPORTANTE

s3 permite versionar os objetos
nasce com versão desligada, se habilita não tem como desabilitar, da para pausar

chave unica impede a exclusão de arquivos
se o arquivo for marcado como apagado, não tem como buscar 

CORS - proteção para arquivos
navegador faz a checagem do CORS

foi mal sor hj n prestei atenção

# AULA 27/03 #

... configurando projeto em py

https://docs.github.com/en/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet
dica do documentação comandos vscode

# AULA 05/05 #

VPC - Virtual private cloud - pertence a uma única região
software defined network - SDN da aws

CIDR block - definir tamanho da rede

topologia de rede fisicas que conecta sevidores, encima cria uma camada de abstração para criar as conexões que quiser

Conta do aws - primeiro nivel de isolamento
Regiões - segundo nível de isolamento
    - o que está em uma região não conversa com outra região
Az's  conjunto de datacenter - terceiro nível de isolamento

subnet - subdivisão da vpc - CIDR único

todos dispositivo gerenciado pode ter uma tabela de rotas 
no aws toda vpc tem sua tabela de rotas padrão
 - a regra é fixa e você não pode alterar
 - esse regra permite comunicação local entre dispositivos
 - ip privado estático para cada recurso/subrede
 - subnets vivem dentro de um az
 - duas redes com a mesma mascara não conversam

 subnet publica - recursos dentro dela, estão visíveis para internet de fora pra dentro e vice-versa

 # AULA 08/05 #

public subnet
cada maquina tem o ip privado e o publico, a maquina não sabe o ip publico

nat - requisição chega pelo ip publico, passa pelo nat 
nat faz a troca de pacote do ip, troca do publico para privado e vice-versa
5 ips publicos por região

private subnets - maquina não encontra internet, internet não encontra máquina

gateway, subnet ppublic, regra para gateway
dentro da public subnet, nat gateway (nat atras de outro nat)
nat gateway so aceita requisições do ip privado, se for de fora, da um drop na hora

banco de dados - privado
bath processing - privado
aplicação web - público (melhor para ocasião)
nat gateway = publico

security group - configura ao criar o servidor
fica junto da aplicação dentro subnet privada
regra apenas inbound
tio da catraca

network ACL - fica na rede da AAWS 
tem duas regras, inbound e outbound
stateless
imigração passaporte

# AULA 12/05 #

If a subnet is associated with a route table that has a route to an internet gateway, it is known as a public subnet.

# AULA 19/05 #

full mesh architecture - vpcs conversam entrem si
hub and spoke architecture - vpc fala com hub que fala com vpc e vice versa

transit gateway - gerenciador central
regional, vive dentro de uma região da aws
pode gerenciar até 5000 attachments, por exemplo VPCs, vpn

peering para duas redes na mesma região da aws, é gratuíto
saindo da região, existe um custo para o peering
peering não suporta transitividade A conversa com B e B com C, mas não A com C

# AULA 26/05 #

IAM Groups
grupos com determinadas permissões que podem ao participarem do grupo, herdam as permissões dos mesmos
facili para gerenciar

grupos não podem ter grupos dentro deles

RBAC - permissão temporaria baseada em roles, usuário assume um papel com permissões
ABAC - permissão baseada em uma permissão

# AULA 02/06 #

monitoramenteo de aplicação
- entender saúde operacional da aplicação
- utilização/otimização de recursos
- performace da aplicação
- segurança

logs complementam as métricas

maneiras de coletar logs e métricas
sdk
cli
api rest
cloudwatch

período padrão para expirar os logs --> nunca expira
é possível contabilizar quantas vezes gerou um erro através dos logs, tendo métrica para gerar alarmes e dashboard

# AULA 09/06 #

Realizados os Laboratórios Canvas AWS

# AULA 12/06 #

Realizados os Laboratórios Canvas AWS

# AULA 16/06 # 

load balance - elastic load balancer ELB

gerencia tráfego de aplicações, sem afetar a experiêncai do usuário final
distribui automaticamente o tráfego de entrada em diferente alvos (instâncias EC2, containers, endereços de IP ou zonas do aws)

application load balancer 
- ideal para microserviços com tráfeo via HTTP e HTTPS, por analisar o conteúdo da requisição

network load balancer
- preparado para aplicações com desempenho alto e pouca latência, ideal para tráfego TCP e TLS

classic load balancer
- primeiro load balancer da AWS, ainda está disponível mas a própria empresa recomenda outros


route 53 - responsável pelo serviço de dns da aws
roteamento de diversas maneira (simples, ponderado, baseado em latência, failover e geolocalização)

# AULA 23/06 #

IAC - infraestrutura como código

ao invés de configurar ambientes de nuvem manualmente, a aws permite que seja setado essa variáveis via linha de código

velocidade e eficiência - cria ambientes complexos de desenvolvimento a produção em minutos
consitência - template de IAC garante que todas as diferenças que surgem quandos ambientes estão sendo configurados, sejam eliminadas com a criação pelo template

# AULA 26/06 #

padrões de comunicação assíncrona = aplicações mais resilientes e escaláveis

Amazon SQS - serviço de fila, funciona como um broker de mensageria, muito semelhante ao Kafka pelo que entendi
Amazon SNS - seviço de tópicos, uma mensagem é criada pelo publisher e distribuida para todos os assinantes (na verdade esse é mais parecido com Kafka)
Amazon EventBridge - recebe eventos de diversas origens e utiliza regras para filtrar e rotear esses eventos para os destinos específicos



# AGRADECIMENTO #

Valeu sor, obrigado pela matéria e apoio durante todo o curso, você fez a diferença. 
Me sinto seguro em dizer que você foi o melhor professor que tive ao longo dessa jornada!!!

Obs: Obrigado por ter apresentado o bloquinho para nós, uso todos os dias sem falta.

