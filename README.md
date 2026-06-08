# 📦 Delainventory - GLPI

Plugin desenvolvido para o GLPI com foco em rastreabilidade de inventário, histórico de conferências e impressão de etiquetas patrimoniais via impressoras Zebra.

O plugin adiciona uma nova aba aos ativos do GLPI, permitindo registrar inventários realizados pelos usuários, manter um histórico de auditoria e gerar etiquetas com QR Code para identificação rápida dos equipamentos.

<br>

> O projeto foi desenvolvido utilizando a arquitetura de plugins do GLPI, integrando-se diretamente aos ativos da plataforma e utilizando impressão ZPL para etiquetas patrimoniais.

<br>

<img src="https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white"/> <img src="https://img.shields.io/badge/GLPI-2C6BED?style=for-the-badge"/> <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white"/> <img src="https://img.shields.io/badge/Zebra_ZPL-000000?style=for-the-badge"/>

## ✨ Funcionalidades

- Registro manual de inventários realizados pelos usuários;
- Compatível com múltiplos tipos de ativos;
- Geração automática de etiquetas patrimoniais;
- QR Code apontando diretamente para o ativo no GLPI;
- Envio de comandos ZPL diretamente para impressoras Zebra via rede;

## 🖥️ Ativos Suportados

Atualmente o plugin suporta:

- Computadores;
- Monitores;
- Impressoras;
- Telefones.

A arquitetura permite expansão futura para outros tipos de ativos do GLPI.

## 🏷️ Etiqueta Gerada

Cada etiqueta contém:

- Código patrimonial do ativo;
- Descrição do equipamento;
- Número de série;
- Responsável;
- QR Code para acesso rápido ao cadastro no GLPI.

Exemplo:

```text
ID DO EQUIPAMENTO
00001

DESCRIÇÃO
Notebook Dell Latitude 5440

SERIAL
ABC123XYZ

RESPONSÁVEL
Simpress

[ QR CODE ]
```

## 📂 Estrutura do Projeto

```bash
delainventory/
├── front/
│   ├── action.php
│   ├── config.php
│   ├── log.php
│   └── print.php
│
├── src/
│   ├── Config.php
│   └── Log.php
│
├── templates/
│   ├── config.html.twig
│   └── log.html.twig
│
├── hook.php
└── setup.php
```

## ⚙️ Funcionamento

### Registro de Inventário

1. Usuário acessa um ativo no GLPI;
2. Seleciona a aba **Delainventory**;
3. Clica em **Registrar inventário**;
4. Informa uma observação;
5. O registro é armazenado em banco de dados;
6. O histórico fica disponível para consulta futura.

### Impressão de Etiquetas

1. Usuário acessa um ativo;
2. Clica em **Imprimir etiqueta**;
3. O plugin coleta os dados do ativo;
4. Gera o ZPL dinamicamente;
5. Envia o conteúdo diretamente para a impressora Zebra via TCP/IP (porta 9100);
6. A etiqueta é impressa automaticamente.

## 🔧 Requisitos

- GLPI;
- PHP 8+;
- MySQL ou MariaDB;
- Impressora Zebra compatível com ZPL;
- Conectividade de rede entre servidor e impressora.

## 🚀 Instalação

Clone o repositório:

```bash
git clone https://github.com/VitorPaloco/Delainventory-GLPI.git
```

Copie o plugin para o diretório de plugins do GLPI:

```bash
glpi/plugins/delainventory
```

Ative o plugin pelo painel administrativo do GLPI:

```text
Configurar → Plugins → Delainventory → Instalar → Ativar
```

## 📸 Screenshots

### Aba de Inventário

![Tela do Plugin](docs/images/inventory-tab.png)

### Etiqueta Impressa

![Etiqueta Zebra](docs/images/label-example.png)

## 📈 Próximas Evoluções

- Inserção do IP e porta da impressora diretamente no GLPI
- Inserção do template ZPL diretamente no GLPI
- Permitir demais formatos de etiqueta (EPL, CPCL...) e tamanhos
- Exportação de histórico para Excel/PDF

## 👨‍💻 Autor

Desenvolvido por **Vitor Paloco** para automação e rastreabilidade de inventário patrimonial utilizando GLPI.
