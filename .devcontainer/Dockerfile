FROM n8nio/base:20

# Instalar dependências do sistema
RUN apk add --no-cache --update openssh sudo shadow bash

# Configurar permissões de sudo para o usuário node
RUN echo node ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/node && chmod 0440 /etc/sudoers.d/node

# Criar diretório de workspaces e configurar permissões
RUN mkdir /workspaces && chown node:node /workspaces

# Mudar para o usuário node
USER node

# Configurar o pnpm
RUN mkdir -p ~/.pnpm-store && pnpm config set store-dir ~/.pnpm-store --global

# Instalar o n8n globalmente
RUN pnpm install -g n8n

# Definir o comando padrão
CMD ["n8n", "start"]
