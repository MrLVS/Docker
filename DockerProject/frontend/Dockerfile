FROM node:14-alpine AS build
# Собираем приложение на основе образа node:14-alpine
WORKDIR /app
# Задаем рабочий каталог для приложения
COPY package*.json ./
#Копируем зависимости в папку app
RUN npm install
#ЗАпускаем node pakage manager и устанавливаем зависимости
COPY ./ ./
# Копируем оставшиеся файлы в папку приложения
RUN npm install -g @angular/cli
#Устанавливаем angular/cli

RUN ng build --prod
# Устанавливаем сборку "--prod" сокращение от configuration=production
# Дефолтный пусть распаковки прописан в angular.json - ""outputPath": "dist/frontend"
# Можно задать свой через --output-path=/dist, -op
# Ошибка данной сборки TS7015: Element implicitly has an 'any' type because index expression is not of type 'number'.
# apiPort: window["env"]["apiPort"] || "default"
#                 ~~~~~
# Решается изменением tsconfig.json
#"compilerOptions": {
#   "suppressImplicitAnyIndexErrors": true,
#   "strictNullChecks":false,
#   "strictPropertyInitialization": false,}

FROM nginx:1.19-alpine
# распаковываем образ nginx
COPY --from=build app/dist/frontend /usr/share/nginx/html
# копируем необходимые файлы из папки установленого build приложения в папку nginx
COPY nginx.sh /docker-entrypoint.d/
#Копируем скрипт, который будет передавать переменные окружения в рантайме
