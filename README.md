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




