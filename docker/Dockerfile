# Use a imagem oficial do Node.js como base
FROM node:20-alpine AS base

# Defina o diretório de trabalho
WORKDIR /app

# Copie os arquivos de configuração essenciais
COPY package.json package-lock.json ./

# Instale as dependências
RUN npm install

# Copie o restante dos arquivos da aplicação
COPY . .

# Construir a aplicação para produção
FROM base AS build
RUN npm run build

# Imagem final para produção
FROM node:20-alpine AS production

# Defina o diretório de trabalho
WORKDIR /app

# Copie os arquivos necessários para o ambiente de produção
COPY --from=build /app/.next ./.next
COPY --from=build /app/node_modules ./node_modules
COPY --from=build /app/package.json ./package.json
COPY --from=build /app/public ./public

# Defina a variável de ambiente para produção
ENV NODE_ENV=production

# Exponha a porta da aplicação
EXPOSE 3000

# Comando para iniciar a aplicação
CMD ["npm", "start"]
