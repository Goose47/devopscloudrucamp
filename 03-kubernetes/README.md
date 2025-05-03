### Алгоритм развертывания кластера через манифесты
- Указать логин и пароль от Docker HUB'а в ``.env`` по примеру из ``.env.example``
- Сгенерировать секрет ``make gen``
- Применить манифесты ``make deploy``

### Алгоритм развертывания кластера через helm
- Билд зависимостей: ``helm dependency build ./helm/echo-server/``
- Установка чарта:
```
helm install echo-server ./helm/echo-server \
  --set dockerRegistry.username=<docker-registry-username> \
  --set dockerRegistry.password=<docker-registry-password>
```

В кластере будут задеплоены три реплики echo-server'а, и nginx-ingress контроллер.
