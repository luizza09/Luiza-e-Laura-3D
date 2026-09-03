# Luiza-e-Laura-3D
# Criptografia RSA e Teoria dos Números em Python 🔒

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Tema](https://img.shields.io/badge/Op%C3%A7%C3%A3o_C-Criptografia_%26_Seguran%C3%A7a-green.svg)](#)
[![Finalidade](https://img.shields.io/badge/Finalidade-Did%C3%A1tica-orange.svg)](#)

Este repositório apresenta uma demonstração prática e conceitual da aplicação da **Teoria dos Números** na segurança de dados, focando na implementação do algoritmo de criptografia assimétrica **RSA** (*Rivest-Shamir-Adleman*) em Python.

---

## 📋 Sumário
- [1. Contextualização](#1-contextualização)
- [2. Objetivos](#2-objetivos)
- [3. Fundamentação Teórica](#3-fundamentação-teórica)
- [4. Aplicação Prática no Mundo Real](#4-aplicação-prática-no-mundo-real)
- [5. Demonstração Matemática Passo a Passo](#5-demonstração-matemática-passo-a-passo)
- [6. Implementação em Python](#6-implementação-em-python)
- [7. Como Executar](#7-como-executar)
- [8. Considerações Finais e Segurança](#8-considerações-finais-e-segurança)

---

## 1. Contextualização

A criptografia é a espinha dorsal da privacidade na era digital. Ela é utilizada diariamente na proteção de smartphones, computadores, transações bancárias, compras online e na garantia da confidencialidade de e-mails e mensagens instantâneas.

Trata-se do processo de codificar **"texto simples"** em **"texto criptografado"** utilizando modelos matemáticos e algoritmos. Para reverter o processo e acessar o conteúdo original, faz-se necessário o uso de uma **chave de descriptografia** compatível.

---

## 2. Objetivos

- **Analisar** a aplicação dos conceitos da Teoria dos Números na criptografia moderna.
- **Demonstrar** o funcionamento prático do algoritmo **RSA** através da resolução de um problema de segurança de dados.
- **Implementar** um script didático em **Python** que ilustre os processos de criação de chaves, cifragem e decifragem de mensagens.

---

## 3. Fundamentação Teórica

O algoritmo **RSA** foi desenvolvido em 1977 por Ron Rivest, Adi Shamir e Leonard Adleman no MIT. É uma das principais formas de **criptografia assimétrica**, ou seja, utiliza um par de chaves distintas:

- **Chave Pública**: Criada a partir da multiplicação de dois números primos e um valor auxiliar. Pode ser distribuída abertamente para que qualquer pessoa criptografe mensagens.
- **Chave Privada**: Mantida em segredo pelo proprietário, permitindo descriptografar as mensagens criptografadas com a chave pública correspondente. Depende diretamente do conhecimento dos dois números primos originais.

> 💡 **Nota:** Devido ao custo computacional de chaves grandes (geralmente de 2048 a 4096 bits), o RSA é amplamente empregado na troca segura de chaves de criptografia simétrica.

---

## 4. Aplicação Prática no Mundo Real

A criptografia estudada neste projeto reflete-se em tecnologias amplamente utilizadas:

1. **WhatsApp Messenger**: Utiliza o protocolo *Signal* para implementar **criptografia de ponta a ponta**. Garante que apenas os interlocutores tenham acesso ao conteúdo das conversas.
2. **Mensagens RCS (Android e iOS)**: Implementação de proteção para mensagens interdigitais (RCS), garantindo cifragem semelhante à do iMessage e WhatsApp durante o envio de textos e mídias de alta qualidade.

---

## 5. Demonstração Matemática Passo a Passo

Abaixo está o detalhamento dos cálculos realizados para o exemplo didático:

### Step 1: Seleção dos Números Primos e Cálculo de $n$
$$p = 5, \quad q = 11$$
$$n = p 	imes q = 5 	imes 11 = 55$$

### Step 2: Cálculo da Função Totiente de Euler $\phi(n)$
$$\phi(n) = (p - 1)(q - 1)$$
$$\phi(55) = (5 - 1)(11 - 1) = 4 	imes 10 = 40$$

### Step 3: Definição da Chave Pública ($e$)
Escolhe-se $e = 3$, pois é **relativamente primo** (coprimo) em relação a $40$ ($\gcd(3, 40) = 1$).

### Step 4: Definição da Chave Privada ($d$)
O valor $d = 27$ é obtido pois satisfaz a condição de **inverso modular**:
$$e 	imes d \equiv 1 \pmod{\phi(n)}$$
$$(3 	imes 27) = 81 \implies 81 \pmod{40} = 1$$

### Step 5: Processo de Cifragem (Criptografia)
Dado o valor numérico da mensagem $M = 7$:
$$C = M^e \pmod n$$
$$C = 7^3 \pmod{55} = 343 \pmod{55} = 13$$

### Step 6: Processo de Decifragem (Descriptografia)
Utilizando a chave privada $d = 27$:
$$M = C^d \pmod n$$
$$M = 13^{27} \pmod{55} = 7$$

---

## 6. Implementação em Python

```python
# Definição dos números primos
p = 5
q = 11

# Cálculo de n
n = p * q

# Cálculo da função totiente de Euler
phi = (p - 1) * (q - 1)

# Definição da chave pública (e) e chave privada (d)
e = 3
d = 27

# Representação numérica da mensagem original
mensagem = 7

# Criptografia da mensagem: C = (mensagem ^ e) mod n
criptografada = (mensagem ** e) % n

# Descriptografia da mensagem: M = (criptografada ^ d) mod n
descriptografada = (criptografada ** d) % n

# Exibição dos resultados
print("Mensagem original:", mensagem)
print("Mensagem criptografada:", criptografada)
print("Mensagem descriptografada:", descriptografada)
```

### Saída do Console:
```text
Mensagem original: 7
Mensagem criptografada: 13
Mensagem descriptografada: 7
```

---

## 7. Como Executar

1. Certifique-se de ter o [Python 3](https://www.python.org/) instalado em seu sistema.
2. Baixe ou clone este repositório.
3. Abra o terminal no diretório do projeto e execute:
   ```bash
   python main.py
   ```

---

## 8. Considerações Finais e Segurança

- **Propósito Didático**: O código e a demonstração utilizam números primos pequenos para facilitar a compreensão do fluxo matemático básico.
- **Aplicações Reais**: Em ambientes reais de produção, são empregados números primos de centenas de dígitos e algoritmos adicionais de *padding* (como OAEP) para evitar ataques matemáticos.
- **Conclusão**: O projeto demonstra de forma prática como a abstração matemática (teoria dos números e aritmética modular) serve como fundamento para a construção de sistemas modernos e seguros de transmissão de dados.