pipeline {
  agent any
  tools {
    nodejs 'nodejs'
  }
  stages {
    stage("build") {
      steps {
        echo "🚀 Building the application"
        sh 'docker build -t nextjs_jenkins .'
      }
    }

    stage("deploy") {
      steps { 
        echo '🚀 Deploying the application'
        sh 'docker start nextjs_jenkins || docker run --name nextjs_jenkins -d -p 3001:3000 nextjs_jenkins'
        sh 'docker ps'
        echo "🚀🚀🚀"
      }
    }
  }
}


COPY --from=builder --chown=nextjs:nodejs /app/.next ./.next
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/package.json ./package.json
COPY --from=builder /app/public ./public

CMD npm start

FROM base as dev
ENV NODE_ENV=development
RUN npm install
COPY . .
CMD npm run dev

