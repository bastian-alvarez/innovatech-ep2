# ETAPA 1: Compilación (Build)
FROM node:18-alpine AS builder
WORKDIR /app
# RÚBRICA: Copiar package.json primero para aprovechar el caché
COPY package*.json ./
RUN npm install
# Copiamos el resto del código y compilamos
COPY . .
RUN npm run build && npm cache clean --force

# ETAPA 2: Ejecución (Run) con Nginx web server
FROM nginx:alpine

# RÚBRICA: Configurar usuario sin privilegios para Nginx
RUN addgroup -g 1001 -S appuser && adduser -u 1001 -S appuser -G appuser \
    && chown -R appuser:appuser /usr/share/nginx/html \
    && chown -R appuser:appuser /var/cache/nginx \
    && chown -R appuser:appuser /var/log/nginx \
    && chown -R appuser:appuser /etc/nginx/conf.d \
    && touch /var/run/nginx.pid \
    && chown -R appuser:appuser /var/run/nginx.pid

USER appuser

# Copiar los archivos estáticos compilados desde la Etapa 1
# NOTA: Cambia "dist" por "build" si usas Create React App en vez de Vite
COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]