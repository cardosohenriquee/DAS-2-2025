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

least privilege - dba mexe no banco e apenas







