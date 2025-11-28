## 1 - Rodando testes

```sh
cargo test
```

## 2 - Buildando o contrato

```sh
# Após rodar o comando, escolha a opção non-reproducible-wasm
cargo near build
```

## 3 - Criar conta [pessoal ou para contrato]

```sh
# Troque <your-account-id.testnet> pelo nome da conta que você deseja
# o --useFaucet é usado para fornecer tokens iniciais para nossa conta de testes
near create-account <your-account-id.testnet> --useFaucet

# Exemplo: near create-account my-app-greeting-1234.testnet --useFaucet
```

## 4 - Comando extra - Checar o estado da conta (balanço, storage, contrato)

```sh
near state <your-account-id.testnet>

# Exemplo: near state my-app-greeting-1234.testnet
```

## 4 - Deploy (ou re-deploy) do contrato

```sh
near deploy <created-account> ./target/near/greeting_app.wasm
```

Para ver os logs das interações no seu contrato, acesse o link:
https://testnet.nearblocks.io/address/<created-account>

Exemplo: https://testnet.nearblocks.io/address/my-app-greeting-1234.testnet

# 5 - Crie uma conta pessoal ou faça login com a conta já criada

```sh
# Caso queira fazer login com a conta pessoal já criada. Isso vai abrir seu browser para obter os dados da conta.
near login

# Caso queira criar uma nova conta pessoal usando o CLI, repita o passo 3.
```

# 6 - Interagindo com o contrato

## 6.1 Lendo dados

```sh
# Para ler dados usando os métodos púplicos do contrato
near view <created-account> get_greeting

# Exemplo de retorno: "Hello"
```

## 6.2 Escrevendo dados

```sh
# Para ler dados usando os métodos púplicos do contrato
near call <created-account> set_greeting '{"greeting": "Olá meus nobres"}' --accountId <created-account>

# Exemplo:
# near call my-app-greeting-1234.testnet set_greeting '{"greeting": "Olá meus nobres"}' --accountId wendersonpires.testnet
```

## 6.3 Revendo o estado do contrato

Repita o comando do tópico 6.1 para ver o valor atualizado do contrato.
