---
theme: "serif"
transition: "slide"
title: "Técnicas de hash"
enableMenu: true
enableSearch: false
enableChalkboard: true
slideNumber: true
---

##### Técnicas de Hash

![-](https://academy.bit2me.com/wp-content/uploads/2018/07/18_Sha256-1.webp)

---

###### O que é uma função hash?

Uma função hash, em termos simples, é um algoritmo que transforma um conjunto de dados (geralmente uma sequência de caracteres ou um arquivo) em uma sequência de caracteres alfanuméricos de comprimento fixo, chamada de "hash". Essa representação de hash é única para um conjunto específico de dados de entrada. As funções hash são projetadas para serem rápidas de calcular e irreversíveis, o que significa que é quase impossível reverter o hash para obter os dados originais.

---

###### Para que serve uma função hash?
As funções hash têm uma ampla variedade de aplicações em ciência da computação e segurança da informação. Alguns dos usos mais comuns incluem:

---

1 - Verificação de integridade: As funções hash são frequentemente usadas para verificar se os dados não foram corrompidos durante a transmissão ou armazenamento. O hash do arquivo original é comparado ao hash do arquivo recebido para garantir que eles sejam idênticos.

2 - Armazenamento seguro de senhas: As senhas dos usuários não são armazenadas diretamente em bancos de dados. Em vez disso, seus hashes são armazenados. Quando um usuário faz login, o sistema calcula o hash da senha inserida e compara-o com o hash armazenado.

---

3 - Criptografia: As funções hash desempenham um papel fundamental em algoritmos de criptografia, como HMAC (Hash-based Message Authentication Code), que garantem a autenticidade e integridade dos dados.

4 - Indexação rápida de dados: As funções hash são usadas em estruturas de dados, como tabelas hash, para acesso eficiente a dados com base em uma chave.

5 - Verificação de duplicatas: Em bancos de dados, hashes podem ser usados para verificar se um registro já existe, evitando a inserção de duplicatas.

---

##### Técnicas de hashcomuns

MD5 (Message Digest 5): Esta foi uma das funções hash mais populares, mas é considerada fraca em termos de segurança atualmente devido à sua vulnerabilidade a colisões (quando dois conjuntos diferentes de dados produzem o mesmo hash).

SHA-1 (Secure Hash Algorithm 1): Também uma vez amplamente utilizado, o SHA-1 também é considerado fraco atualmente, devido às colisões sendo encontradas.

SHA-256 (Secure Hash Algorithm 256): Parte da família SHA-2, o SHA-256 é amplamente utilizado em aplicações de segurança e é considerado muito mais seguro do que o MD5 e o SHA-1.

---

bcrypt: É uma função hash projetada especificamente para armazenar senhas com segurança, com um alto custo computacional para desacelerar ataques de força bruta.

Argon2: Uma função hash e algoritmo de derivação de chave que é altamente recomendado para armazenamento seguro de senhas devido à sua resistência a ataques de força bruta e paralelos.

SHA-3 (Secure Hash Algorithm 3): É a terceira geração da família de funções hash SHA e oferece segurança sólida contra colisões.

---


```javascript
const crypto = require('crypto');

// Chave secreta (deve ser mantida em segredo)
const secretKey = crypto.randomBytes(32); // Usando uma chave de 256 bits

const iv = crypto.randomBytes(16);

// Dados a serem criptografados
const plaintext = 'Mensagem secreta';

// Criptografar
const cipher = crypto.createCipheriv('aes-256-cbc', secretKey, iv);
let encrypted = cipher.update(plaintext, 'utf-8', 'hex');
encrypted += cipher.final('hex');

console.log('Texto criptografado:', encrypted);

// Gerar um HMAC para os dados criptografados
const hmac = crypto.createHmac('sha256', secretKey);
hmac.update(encrypted);
const hash = hmac.digest('hex');

console.log('HMAC:', hash);

// Simulação de transmissão e recebimento

// Verificação do HMAC
const receivedHmac = hash; // Aqui você receberia o HMAC enviado junto com os dados criptografados
const receivedEncrypted = encrypted; // Aqui você receberia os dados criptografados

const hmacToVerify = crypto.createHmac('sha256', secretKey);
hmacToVerify.update(receivedEncrypted);
const calculatedHmac = hmacToVerify.digest('hex');

if (calculatedHmac === receivedHmac) {
  console.log('HMAC verificado com sucesso. Dados íntegros.');
  // Descriptografar
  const decipher = crypto.createDecipheriv('aes-256-cbc', secretKey, iv);
  let decrypted = decipher.update(receivedEncrypted, 'hex', 'utf-8');
  decrypted += decipher.final('utf-8');
  console.log('Texto descriptografado:', decrypted);
} else {
  console.log('HMAC não corresponde. Os dados podem ter sido alterados.');
}
```

---