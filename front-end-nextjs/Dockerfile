FROM node:18-alpine as base

WORKDIR /app

COPY package*.json yarn.lock* package-lock.json* pnpm-lock.yaml* ./

RUN \
  if [ -f yarn.lock ]; then yarn --frozen-lockfile; \
  elif [ -f package-lock.json ]; then npm ci; \
  elif [ -f pnpm-lock.yaml ]; then corepack enable pnpm && pnpm install --frozen-lockfile; \
  else echo "No lock file found, skipping dependency installation" && exit 1; \
  fi

COPY . .

RUN npm run build

EXPOSE 3000

CMD ["npm", "start"]
