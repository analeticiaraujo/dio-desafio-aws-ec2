Desafio de Projeto DIO: Gerenciamento de Instância EC2 na AWS

📝 Visão Geral do Projeto
Este repositório documenta a execução do desafio de projeto da Digital Innovation One (DIO) sobre o gerenciamento prático de uma instância EC2 na Amazon Web Services (AWS). O objetivo foi aplicar os conceitos de criação, configuração, acesso e gerenciamento do ciclo de vida de um servidor virtual na nuvem, registrando todo o processo como um guia e portfólio técnico.   

📖 Índice
Arquitetura da Solução

Procedimento Passo a Passo

Principais Aprendizados

Autor

🏗️ Arquitetura da Solução
A arquitetura implementada neste laboratório é fundamental para a computação em nuvem. Consiste em uma única instância EC2 (servidor virtual) implantada em uma sub-rede pública dentro da Virtual Private Cloud (VPC) padrão da AWS. O acesso à instância é protegido por um Security Group que atua como um firewall, permitindo tráfego SSH (porta 22) apenas de fontes autorizadas, garantindo uma conexão segura.

🚀 Procedimento Passo a Passo
Esta seção detalha as etapas executadas para completar o desafio, desde a criação dos recursos na AWS até a configuração final do servidor.

1. Criação da Instância EC2
A instância foi provisionada através do console da AWS com as seguintes configurações para se manter no Nível Gratuito (Free Tier):

AMI (Amazon Machine Image): Ubuntu Server, elegível para o Nível Gratuito.

Tipo de Instância: t3.micro, oferecendo recursos suficientes para o laboratório sem gerar custos.   

Par de Chaves (Key Pair): Um novo par de chaves foi criado e o arquivo .pem foi baixado para permitir o acesso seguro via SSH.

Configuração do Security Group: Foi criado um novo Security Group com uma regra de entrada (inbound rule) para permitir tráfego na porta 22 (SSH) a partir do meu IP, restringindo o acesso ao meu ambiente de desenvolvimento.

2. Conexão com a Instância via SSH
A conexão foi estabelecida utilizando o cliente SSH nativo do Windows (CMD). O endereço IPv4 Público da instância foi obtido no painel do EC2 e, no terminal, executei o seguinte comando para conectar:bash
ssh -i ".pem" ubuntu@


A conexão foi estabelecida com sucesso, validando que a configuração da instância e do *Security Group* estavam corretas, como mostra a imagem abaixo.

![Captura conexão](https://github.com/user-attachments/assets/6e2c26c0-bcfb-4743-b7b9-01971c2bd66b)

### 3. Atualização e Gerenciamento do Servidor

Após o primeiro acesso, realizei a atualização dos pacotes do sistema operacional para garantir que todos os softwares estivessem com as últimas correções de segurança.

# Atualiza a lista de pacotes disponíveis
sudo apt update

# Instala as atualizações dos pacotes
sudo apt upgrade -y

Durante o processo de upgrade, o sistema informou que uma nova versão do Kernel estava disponível e que uma reinicialização era recomendada para ativá-la. Para aplicar a atualização do Kernel e garantir que o sistema operacional utilize a versão mais recente e segura, executei o comando de reinicialização:

# Reinicializa o Kernel
sudo reboot

Após a reinicialização, conectei-me novamente à instância para confirmar que o sistema estava operando normalmente.


💡 Principais Aprendizados
Este desafio prático solidificou conceitos essenciais sobre a operação na nuvem AWS:

A Importância dos Security Groups: A configuração correta dos Security Groups é a primeira linha de defesa e a chave para uma conectividade bem-sucedida. Um erro de configuração aqui é a causa mais provável de problemas de acesso, como timeouts de conexão.   

Gerenciamento do Ciclo de Vida: Compreendi a diferença crítica entre as ações de Parar (Stop) e Terminar (Terminate) uma instância.   

Ação	Impacto na Cobrança	Impacto nos Dados (Volume EBS)	Reversibilidade
Parar (Stop)	Cessa a cobrança por computação, mas mantém a cobrança pelo armazenamento EBS.	Os dados no volume raiz são preservados.	Ação reversível. A instância pode ser iniciada novamente.
Terminar (Terminate)	Cessa todas as cobranças associadas à instância.	O volume raiz é excluído por padrão. Os dados são perdidos.	Ação irreversível. A instância é permanentemente removida.

Exportar para as Planilhas
Necessidade de Reinicialização Pós-Atualização do Kernel: Aprendi que, embora muitas atualizações no Linux não exijam reinicialização, atualizações de componentes críticos como o Kernel só entram em vigor após um reboot do sistema.

👨‍💻 Autor
Feito por Ana Leticia de Araújo.

LinkedIn: https://www.linkedin.com/in/ana-leticia-de-araujo

GitHub: https://github.com/analeticiaraujo

