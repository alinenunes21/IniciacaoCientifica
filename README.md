# Sistema de Simulação de Carga de Trabalho

## 📋 Descrição

Este projeto implementa um sistema distribuído cliente-servidor para simulação e análise de cargas de trabalho computacionais. Desenvolvido como parte de um projeto de iniciação científica, o sistema permite testar o comportamento de aplicações sob diferentes condições de stress de CPU, memória e rede.

## 🎯 Objetivos

- Simular cargas de trabalho realistas em ambientes distribuídos
- Analisar o impacto de diferentes configurações de CPU e memória
- Medir performance de transferência de dados
- Testar comportamento do sistema sob múltiplas conexões simultâneas

## 🏗️ Arquitetura

### Servidor (`server.py`)
- **Porta:** 50002 (localhost)
- **Gerenciamento de Memória:** Aloca até 16GB (1.3GB inicial + 2.4GB por cliente)
- **Processamento Multi-core:** Controla afinidade de CPU por núcleo específico
- **Conexões Simultâneas:** Suporte a múltiplos clientes via threading

### Cliente (`client.py`)
- **Configuração Flexível:** Permite configurar múltiplos clientes
- **Métricas de Performance:** Mede tempo de transferência em milissegundos
- **Controle de Fluxo:** Implementa delay de 33ms entre pacotes

## ⚙️ Funcionalidades

### 🖥️ Simulação de CPU
- Geração de carga em núcleos específicos
- Controle de intensidade (0-100%)
- Duração configurável

### 💾 Gerenciamento de Memória
- Alocação dinâmica por cliente
- Controle de limite máximo
- Liberação automática após desconexão

### 🌐 Transferência de Arquivos
- Envio bidirecional entre cliente e servidor
- Verificação de integridade
- Tratamento de erros de conexão

## 🛠️ Requisitos

```bash
# Dependências principais
pip install psutil

# Biblioteca adicional (inclua no mesmo diretório)
# cpu_load_generator.py
```

### Ambiente Testado
- **SO:** Ubuntu Linux
- **Python:** 3.x
- **Memória:** Mínimo 4GB recomendado
- **CPU:** Multi-core para melhor aproveitamento

## 🚀 Como Executar

### 1. Iniciar o Servidor
```bash
python server.py
```

### 2. Executar Cliente(s)
```bash
python client.py
```

### 3. Configurar Parâmetros
Para cada cliente, configure:
- **Nome do arquivo:** Arquivo a ser transferido
- **Duração:** Tempo de carga em segundos
- **Carga CPU:** Intensidade entre 0 e 1
- **Núcleo:** Número do núcleo específico

## 📊 Exemplo de Uso

```
Quantos clientes deseja simular? 2

--- Configurações para Cliente 1 ---
Nome do arquivo a ser enviado: teste1.txt
Duração da carga em segundos: 10.0
Carga desejada (entre 0 e 1): 0.8
Núcleo da CPU (número inteiro): 0

--- Configurações para Cliente 2 ---
Nome do arquivo a ser enviado: teste2.txt
Duração da carga em segundos: 15.5
Carga desejada (entre 0 e 1): 0.6
Núcleo da CPU (número inteiro): 1
```

## 📈 Métricas Coletadas

- **Tempo de transferência** (milissegundos)
- **Uso de memória por cliente** (2.4GB)
- **Carga de CPU por núcleo** (configurável)
- **Status de conexão** e tratamento de erros

## 🔧 Configurações Avançadas

### Limites do Sistema
- **Memória máxima:** 16GB
- **Porta padrão:** 50002
- **Delay entre pacotes:** 33ms
- **Tamanho do buffer:** 1024 bytes

### Personalização
- Modificar `max_memory_mb` para ajustar limite de memória
- Alterar `time.sleep(0.033)` para diferentes delays
- Configurar porta em `server.bind()`

## 🎓 Aplicações Acadêmicas

Este projeto foi desenvolvido para:
- Estudos de **sistemas distribuídos**
- Análise de **performance computacional**
- Pesquisa em **otimização de recursos**
- Experimentos em **computação paralela**

## 📋 Apresentação

Projeto apresentado no **COMPEEX** (Congresso de Pesquisa, Ensino e Extensão), demonstrando aplicações práticas em simulação de cargas de trabalho distribuídas.

## 🔍 Estrutura do Projeto

```
📁 workload-simulation/
├── 📄 server.py              # Servidor principal
├── 📄 client.py              # Cliente simulador
├── 📄 cpu_load_generator.py  # Gerador de carga CPU
├── 📄 README.md              # Este arquivo
└── 📁 test_files/            # Arquivos para teste
    ├── teste1.txt
    └── teste2.txt
```

## 🤝 Contribuições

Este é um projeto acadêmico desenvolvido como parte de iniciação científica. Sugestões e melhorias são bem-vindas!

## 📄 Licença

Projeto desenvolvido para fins educacionais e de pesquisa.
