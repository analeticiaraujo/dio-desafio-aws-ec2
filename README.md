# Desafio de Projeto: Gerenciamento de Instâncias EC2 na AWS

<p align="center">
  <img src="https://img.shields.io/badge/STATUS-CONCLUÍDO-green?style=for-the-badge" alt="Status Concluído"/>
  <img src="https://img.shields.io/badge/Tecnologia-AWS-orange?style=for-the-badge" alt="Tecnologia AWS"/>
  <img src="https://img.shields.io/badge/Serviço-EC2-yellow?style=for-the-badge" alt="Serviço EC2"/>
</p>

Repositório criado para documentar a execução do **Desafio de Projeto da [DIO](https://www.dio.me/)** sobre o gerenciamento de instâncias **EC2** na **Amazon Web Services (AWS)**. O objetivo deste laboratório foi aplicar os conhecimentos adquiridos para criar, conectar e gerenciar uma máquina virtual na nuvem, documentando cada passo do processo.

---

### 👩‍💻 Autora

| Nome                | GitHub                                       | LinkedIn                                                       |
| ------------------- | -------------------------------------------- | -------------------------------------------------------------- |
| Ana Leticia de Araujo | [@analeticiaraujo](https://github.com/analeticiaraujo) | [Ana Leticia de Araujo](https://www.linkedin.com/in/ana-leticia-de-araujo) |

---

## 📜 Índice

* [Visão Geral do Desafio](#-visão-geral-do-desafio)
* [Passo 1: Criação da Instância EC2](#-passo-1-criação-da-instância-ec2)
* [Passo 2: Conexão com a Instância via SSH](#-passo-2-conexão-com-a-instância-via-ssh)
* [Passo 3: Atualização e Gerenciamento do Servidor](#-passo-3-atualização-e-gerenciamento-do-servidor)
* [Conclusão e Aprendizados](#-conclusão-e-aprendizados)

---

## 🎯 Visão Geral do Desafio

Este projeto prático teve como objetivo consolidar os conhecimentos sobre o serviço **Elastic Compute Cloud (EC2)** da AWS. O desafio consistiu em provisionar uma instância Linux, conectar-se a ela de forma remota e realizar as primeiras configurações, documentando todo o processo para servir como material de consulta e portfólio.

---

## 🚀 Passo 1: Criação da Instância EC2

A primeira etapa foi a criação da máquina virtual no painel da AWS. A tabela abaixo detalha as configurações utilizadas:

| Configuração              | Escolha                                                                                                      | Descrição                                                                                             |
| ------------------------- | ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------- |
| **AMI** | `Amazon Linux`                                                                                               | Imagem de máquina padrão da AWS, otimizada para o ambiente e elegível no *Free Tier*.                 |
| **Tipo de Instância** | `t3.micro`                                                                                                   | Instância com bom equilíbrio de recursos para aprendizado e testes, também coberta pelo *Free Tier*. |
| **Par de Chaves** | Novo par de chaves `.pem`                                                                                    | Arquivo de chave privada essencial para a autenticação segura via SSH.                                |
| **Security Group** | Personalizado                                                                                                | Regra de firewall configurada para permitir tráfego de entrada na **porta 22 (SSH)** apenas do meu IP. |

---

## 💻 Passo 2: Conexão com a Instância via SSH

Com a instância em estado de *Running*, o próximo passo foi a conexão remota. Como utilizei o sistema operacional **Windows**, a conexão foi realizada através do **Prompt de Comando (CMD)**.

1.  **Obtenção do IP Público:** No painel do EC2, identifiquei o endereço de **IPv4 público** da instância.
2.  **Comando de Conexão:** Utilizei o seguinte comando `ssh` para estabelecer a conexão:

    ```bash
    ssh -i "caminho/para/sua-chave.pem" ec2-user@SEU_IP_PUBLICO
    ```
    * `ssh`: Ferramenta para acesso remoto seguro.
    * `-i`: Flag que especifica o arquivo de identidade (chave privada).
    * `ec2-user`: Usuário padrão para a AMI Amazon Linux.

Após a execução do comando e a confirmação da autenticidade do host, a conexão foi estabelecida com sucesso.

#### Evidência da Conexão

A captura de tela abaixo comprova o acesso bem-sucedido à instância EC2.

![Captura conexão](https://github.com/user-attachments/assets/b2c443f2-6498-4b45-b898-7f08b9ff0ed3)

---

## 🛠️ Passo 3: Atualização e Gerenciamento do Servidor

Uma vez conectado, a primeira boa prática de gerenciamento foi garantir que todos os pacotes do sistema operacional estivessem atualizados.

1.  **Comando de Atualização:** Executei o comando abaixo para atualizar os pacotes.

    ```bash
    sudo yum update -y
    ```

2.  **Aviso de Atualização do Kernel:** Após a atualização, o sistema exibiu uma mensagem importante:

    > *"Newer kernel available... Restarting the system to load the new kernel will not be handled automatically, so you should consider rebooting."*

    Isso indica que o *coração* do sistema operacional (Kernel) foi atualizado, mas a nova versão só será carregada após uma reinicialização.

3.  **Reinicialização do Servidor:** Para aplicar o novo kernel e concluir o processo, executei o comando de reinicialização.

    ```bash
    sudo reboot
    ```
    A conexão SSH foi encerrada. Após alguns instantes, reconectei-me para confirmar que a instância estava novamente online e com o sistema atualizado.

---

## ✨ Conclusão e Aprendizados

Este desafio foi uma excelente oportunidade para aplicar de forma prática os conceitos teóricos sobre a **AWS** e o serviço **EC2**. Ao final, fui capaz de entender o ciclo de vida completo de uma instância, desde sua criação, passando pela configuração de segurança, conexão remota e gerenciamento básico do sistema operacional. A documentação do processo no GitHub também reforçou a importância de manter um registro claro e estruturado de projetos de infraestrutura.
