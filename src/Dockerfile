FROM oven/bun

EXPOSE 3000

WORKDIR /usr/src/app

ENV NODE_ENV production

COPY package.json .
COPY bun.lockb .

RUN bun install

COPY src src
COPY www www
COPY prisma prisma

COPY tsconfig.json .
COPY tailwind.config.js .
COPY postcss.config.cjs .
COPY vite.config.js .

RUN bunx prisma generate
RUN bun run build

COPY public public

CMD ["bun", "www/bin.ts"]
