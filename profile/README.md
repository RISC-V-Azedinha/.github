# ⚡ RISC-V-Azedinha

**Plataforma didática baseada em SoC RISC-V com aceleração neural em FPGA**

Trabalho de Conclusão de Curso em Engenharia de Computação, Centro Universitário do Instituto Mauá de Tecnologia (CEUN-IMT).

Esta organização reúne os repositórios de *hardware* e *software* do projeto: o sistema-em-chip, o acelerador neural, o sistema operacional de tempo real e as ferramentas didáticas que os acompanham.

---

## Motivação

O ensino de Arquitetura de Computadores costuma se apoiar em processadores escalares clássicos, enquanto os sistemas atuais são heterogêneos e combinam núcleos de uso geral com aceleradores de domínio específico (DSAs). Simuladores didáticos abstraem o *hardware*, e projetos sintetizáveis de código aberto raramente são pensados para o ensino; nenhum dos ecossistemas didáticos analisados explora a aceleração neural.

Este projeto propõe um SoC de código aberto, desenvolvido por co-projeto *hardware*/*software*, que integra a um núcleo RISC-V uma Unidade de Processamento Neural (NPU) sistólica. A plataforma permite observar e medir, em *hardware* real, o gargalo de Von Neumann, o efeito da movimentação de dados sobre o desempenho e o ganho obtido por uma arquitetura dedicada.

## Arquitetura

- **Núcleo RV32I_Zicsr:** processador multiciclo com o conjunto base de inteiros e a extensão de registradores de controle e estado (CSRs), com tratamento de exceções e interrupções em modo de máquina.
- **NPU:** arranjo sistólico 4×4 de precisão INT8 com fluxo de dados *Output Stationary* e um modo GEMV (produto matriz-vetor) para camadas densas. Inclui im2col em *hardware*, pós-processamento (PPU), pesos residentes, *streaming* de entradas e execução por programas de descritores.
- **Infraestrutura do SoC:** interconexão por *crossbar*, controlador DMA, controladores de interrupção (CLINT e PLIC), UART, GPIO, cartão SD e saída VGA, todos acessados por E/S mapeada em memória (MMIO).
- **AXON:** núcleo de tempo real (RTOS) escrito para a plataforma, com escalonamento preemptivo por prioridades, alocação dinâmica de memória, chamadas de sistema e terminal pela UART.
- **Ferramentas didáticas:** aplicação gráfica em Python com experimentos sobre o *datapath* do processador, E/S mapeada em memória, arbitragem de barramento, multitarefa, *dataflow* sistólico e inferência neural na FPGA, além de um *debugger* com execução passo a passo e pontos de parada.

## Resultados

Implementação em FPGA (Digilent Nexys A7, Xilinx Artix-7) a 100 MHz:

| Métrica | Valor |
|---|---|
| Vazão máxima da NPU (multiplicação de matrizes, *K* = 2.048) | 12,2 MACs úteis/ciclo, de um teto de 16 |
| Aceleração sobre o núcleo RV32I no mesmo cenário | 7.477× |
| CNN para MNIST (6.810 parâmetros, 12.844 MACs) | 1.506 ciclos (≈ 15 µs) por inferência |
| Acurácia da CNN quantizada em INT8 | 97,79% (emulação, 10.000 imagens de teste) |

Todos os resultados da NPU no *benchmark* são recalculados pela CPU e comparados byte a byte, sem divergências.

## Repositórios

| Repositório | Descrição |
|---|---|
| [RISC-V](https://github.com/RISC-V-Azedinha/RISC-V) | SoC completo: RTL em VHDL, *firmware*, *benchmarks* e fluxo de síntese para FPGA |
| [NPU](https://github.com/RISC-V-Azedinha/NPU) | Desenvolvimento e verificação da Unidade de Processamento Neural |
| [AXON-OS](https://github.com/RISC-V-Azedinha/AXON-OS) | RTOS educacional para RV32I, executável no QEMU e no SoC em FPGA |
| [GUI-TCC](https://github.com/RISC-V-Azedinha/GUI-TCC) | Aplicação didática em Python (PyQt5) com os experimentos da plataforma |
| [Digit-Tracker](https://github.com/RISC-V-Azedinha/Digit-Tracker) | Reconhecimento de dígitos desenhados no ar por visão computacional, com inferência na NPU |

## Equipe

- André Solano Ferreira Rodrigues Maiolini
- Durval Consorti Soranz de Barros Santos
- Estevan Delazari Feher
- Leonardo Roberto Amadio
- Lucas Castanho Paganotto Carvalho

**Orientação:** Prof. Me. Nuncio Perrella e Prof. Dr. Angelo Sebastião Zanini.
