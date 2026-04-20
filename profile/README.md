# ⚡ RISC-V-Azedinha

## Plataforma Didática Baseada em SoC RISC-V com Aceleração Neural em FPGA 

Bem-vindo à organização oficial do nosso Trabalho de Conclusão de Curso (TCC) em Engenharia de Computação pelo Centro Universitário do Instituto Mauá de Tecnologia.

Este espaço centraliza todos os repositórios que compõem o nosso ecossistema de hardware e software, focado no ensino prático de Arquitetura de Computadores e aceleração de Inteligência Artificial na Borda (Edge AI).

## 📌 Sobre o Projeto

O projeto consiste no co-projeto (hardware/software co-design) de um Sistema-em-Chip (SoC) de código aberto baseado na arquitetura RISC-V. A plataforma busca mitigar a lacuna didática entre os processadores escalares clássicos ensinados na academia e os modernos sistemas heterogêneos exigidos pela indústria.

Para isso, o SoC não atua apenas como um processador genérico, mas integra uma Unidade de Processamento Neural (NPU) sistólica, permitindo a análise explícita e mensurável de gargalos de memória e o ganho de desempenho obtido por Arquiteturas de Domínio Específico (DSAs).

## 🚀 Principais Recursos

- Núcleo RISC-V (RV32I_Zicsr): Processador multiciclo que suporta o conjunto base de inteiros e a extensão privilegiada de Control and Status Registers (CSRs).
- Aceleração Neural (NPU): Arranjo sistólico operando em fluxo de dados Saída Estacionária (Output Stationary), para aceleração de inferências neurais.
- Infraestrutura de SoC e Barramento: Sistema completo com barramento customizado, árbitro de barramento e integração via MMIO (Memory Mapped I/O).
- Sistema Operacional Customizado (AXON-OS): Um RTOS monolítico e embarcado, desenvolvido sob medida para o SoC, com suporte a escalonamento preemptivo de tarefas.
- Ecossistema Educacional: Interface gráfica desenvolvida em Python que permite inspeção de registradores e monitoramento de inferências neurais via UART, convertendo o hardware em uma bancada interativa de aprendizado.

👥 Equipe de Desenvolvimento

- André Solano Ferreira Rodrigues Maiolini
- Durval Consorti Soranz de Barros Santos
- Estevan Delazari Feher
- Leonardo Roberto Amadio
- Lucas Castanho Paganotto Carvalho 

Orientação: Prof. Ms. Nuncio Perrella e Prof. Dr. Angelo Sebastião Zanini.
