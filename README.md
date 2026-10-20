Aqui vai um README completo e pronto para colar no arquivo `README.md`:

```md name=README.md url=https://github.com/m4rcosJr/MikrotikController/blob/main/README.md
# MikroTik Controller

Aplicação web para controle de dispositivos MikroTik via SSH, com autenticação segura, interface amigável e registro de auditoria das ações executadas.

O projeto foi pensado para permitir ações simples e controladas no RouterOS, como habilitar/desabilitar interfaces Ethernet, com validação de comandos e logs para rastreabilidade.

## Funcionalidades

- Login com autenticação JWT
- Execução de comandos no MikroTik por SSH
- Controle de interfaces Ethernet
- Modo mock para testes locais sem dispositivo real
- Visualização de status do sistema
- Tela de logs com auditoria das ações
- Rate limiting para proteger a API
- Frontend estático em HTML, CSS e JavaScript

## Tecnologias

- Node.js
- Express
- SSH2
- JWT (jsonwebtoken)
- CORS
- dotenv
- express-rate-limit
- Frontend em JavaScript puro

## Estrutura do projeto

```
MikrotikController/
├── public/
│   ├── app.js
│   ├── index.html
│   └── style.css
├── logs/
│   └── auditoria.log
├── .gitignore
├── package.json
├── README.md
├── server.js
└── .env
```

## Pré-requisitos

- Node.js v18+
- Acesso SSH habilitado no MikroTik
- Credenciais válidas do equipamento
- Um ambiente com acesso ao roteador na rede

## Instalação

1. Clone o repositório:
```
git clone https://github.com/m4rcosJr/MikrotikController.git
cd MikrotikController
```

2. Instale as dependências:
```
npm install
```


> Se `MOCK_MODE=true`, a aplicação simula execuções sem tentar conectar ao MikroTik.

## Executando

```bash
npm start
```

Ou em modo de desenvolvimento:

```
npm run dev
```

A aplicação fica disponível em:

```
http://localhost:3000
```

## Como usar

### Login
Acesse a interface web e faça login usando as credenciais definidas em:
- `APP_USER`
- `APP_PASS`

### Execução de ações
As ações disponíveis estão mapeadas no backend e incluem, por exemplo:

- Desabilitar ether1
- Desabilitar ether2
- Desabilitar ether3
- Habilitar ether4

Essas ações são executadas via comandos RouterOS por SSH.

### Logs
O sistema registra:
- login sucedido/fracassado
- ações executadas
- erros de execução
- dados do usuário e do IP

Os logs podem ser vistos na aba de "Logs" dentro da interface.

## API

### POST /api/login
Autentica o usuário e retorna um token JWT.

Exemplo de payload:

```json
{
  "username": "admin",
  "password": "123456"
}
```

### POST /api/execute
Executa uma ação permitida no MikroTik.

Exemplo de payload:

```json
{
  "action": "disable_ether1"
}
```

### GET /api/status
Retorna informações do backend e do equipamento alvo.

### GET /api/logs
Retorna as últimas 100 entradas do log de auditoria.

## Segurança

- Tokens JWT para autenticação da API
- Rate limiting para reduzir abuso
- Whitelist de comandos permitidos
- Registro de ações em log
- Validação de ações no backend antes da execução

## Observações

Este projeto foi desenvolvido como uma ferramenta de automação/controlador simples para ambientes locais, com foco em facilidade de uso e monitoramento.

Em produção, recomenda-se:
- usar HTTPS
- manter `JWT_SECRET` em ambiente seguro
- configurar firewall e controle de acesso
- evitar expor a interface diretamente na internet sem proteção

## Licença

Este projeto está disponível para uso acadêmico e pessoal. Caso queira reutilizar em produção, revise os ajustes de segurança e autenticação conforme o ambiente.

## Autor

Desenvolvido por m4rcosJr.
```

Se quiser, posso também criar uma segunda versão mais “bonita/profissional”, com foco em GitHub, ou uma versão mais curta e enxuta.
