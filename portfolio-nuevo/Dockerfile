# ═══════════════════════════════════════════════
# Dockerfile — Portfolio Antony Vera Sánchez
# Imagen: nginx:alpine (ultra ligera ~23MB)
# ═══════════════════════════════════════════════

FROM nginx:alpine

# Metadata
LABEL maintainer="Antony Vera Sánchez <antonyverasanchez2706@gmail.com>"
LABEL description="Portfolio personal — Ciberseguridad & Desarrollo de Software"

# Copiar config nginx personalizada
COPY nginx.conf /etc/nginx/nginx.conf

# Copiar archivos del portfolio
COPY index.html   /usr/share/nginx/html/
COPY css/         /usr/share/nginx/html/css/
COPY js/          /usr/share/nginx/html/js/
COPY assets/      /usr/share/nginx/html/assets/

# Permisos correctos (seguridad)
RUN chown -R nginx:nginx /usr/share/nginx/html && \
    chmod -R 755 /usr/share/nginx/html

# Puerto
EXPOSE 80

# Health check
HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
  CMD wget -qO- http://localhost/ || exit 1

CMD ["nginx", "-g", "daemon off;"]
