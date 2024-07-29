This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Create project with Docker

```bash
docker pull node:20-alpine

docker run -it --rm -v $(pwd)/my-next-app:/app -w /app node:20-alpine npx create-next-app@latest
```

## Getting started with Docker

### Development mode

```bash
docker-compose up app
```

### Production mode

```bash
docker-compose up app-production
```

## Access the Running Container

```bash
docker-compose exec app sh
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.
