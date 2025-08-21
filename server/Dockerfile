FROM node:16-alpine

WORKDIR /app

ARG ATLAS_URI

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 5050

ENV NODE_ENV=production
ENV PORT=5050
ENV ATLAS_URI=${ATLAS_URI}

RUN addgroup -g 1001 -S nodejs && \
    adduser -S nodejs -u 1001

RUN chown -R nodejs:nodejs /app

USER nodejs

HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD node -e "require('http').get('http://localhost:5050/posts', (res) => { process.exit(res.statusCode === 200 ? 0 : 1) })" || exit 1

CMD ["npm","start"]