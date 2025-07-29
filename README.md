# 🚀 DevOps Диплом — Автоматизация от идеи до мониторинга

Добро пожаловать в дипломный проект, созданный в рамках обучения в TMS School. Здесь DevOps-подход обретает реальную форму — от инфраструктуры до готового приложения под контролем мониторинга и CI/CD.

---

## 🎓 Что вы найдёте в этом проекте
Проект охватывает весь цикл внедрения DevOps-практик:

✅ Автоматизация серверной части через Ansible

🔄 Полноценный CI/CD Pipeline в Jenkins

🐳 Контейнеризация с помощью Docker

📈 Сбор и визуализация метрик через Prometheus + Grafana

🚨 Система алертов с Alertmanager, интеграция с Telegram

🧮 Веб-приложение — вычеслы4ение Дискриминанта на Flask

---

## 📦 Структура проекта

Репозитории проекта:

| Назначение | Репозиторий |
|------------|-------------|
| Ansible-автоматизация и конфигурация Jenkins | [tmsprojectdiplom](https://github.com/Vlados752/tmsprojectdiplom/tree/main/roles) |
| Исходный код приложения и Jenkins pipeline | [app_tmsm](https://github.com/Vlados752/app_tms/tree/main) |

---

## ⚙️ Что под капотом

- **2 Linux-хоста (Ubuntu 24.04.01)**:
  - **Хост 1**: Ansible, Docker
  - **Хост 2**: Docker, Jenkins
  - **Хост 3**: Alermanager,Prometheus, Grafana
- Связь по SSH между хостами (из первого ко второму и к третьему)
- Минимальные системные требования: 2 vCPU, 2 ГБ RAM на каждом хосте

---

## 🚀 Как развернуть проект

1. Клонируйте репозиторий с Ansible-ролями:

   ```bash
   git clone https://github.com/Vlados752/tmsprojectdiplom.git
   ```

2. Задайте настройки:

    - IP-серверов — в hosts.ini

    - Секреты и параметры — в group_vars/all.yml
  

3. Запустите развёртывание:

   ```bash
   ansible-playbook -i hosts.ini deploy.yml --ask-vault-pass
   ```

**Проверка создания контейнеров на исполняемом хосте:**

![Проверка создания контейнеров](1.png)

---

## 🛠 CI/CD Pipeline (Jenkins)

1. Откройте браузер по адресу `http://<IP>:8080` и авторизуйтесь в Jenkins
2. Запустите Jenkins pipeline:
   - Пайплайн скачивает [исходный код приложения (Flask-Дискриминант)](https://github.com/Vlados752/app_tms)
   - Проверяет код flake8-линтером
   - Собирает образ Docker
   - Запускает тесты
   - ПОтправляет уведомление в Telegram
3. После успешного запуска, приложение будет доступно по адресу `http://<IP>:5000`

**Успешно завершённый пайплайн:**

![Pipeline](2.png)

**Доступное приложение "Диксриминант":**

![Calculator](3.png)

---

##  📊 Мониторинг без лишнего шума
   
- **Prometheus** собирает метрики с Jenkins и Flask-приложения
- **Grafana** отображает метрики на дашбордах
- **Alertmanager** отправляет алерты в Telegram при сбоях или отклонениях

**Grafana Dashboard:**

![Grafana](4.png)

** 🚨 Полученные алерты в Telegram:**

![Алерты](5.png)

---

## 📌 Полезные команды

```bash
# Проверить статус всех сервисов Docker
docker ps -a

# Перезапустить Jenkins
sudo systemctl restart jenkins

# Посмотреть логи Prometheus
docker logs prometheus

# Проверка SSH-доступа
ssh user@host2
```

---

## 🧯 Частые проблемы — быстрые решения

- Jenkins не стартует? Проверьте Java и логи /var/log/jenkins/jenkins.log
- Ошибка линтинга? Установите flake8
- Нет алертов? Проверьте настройки Telegram-бота

---

## 📮 Автор проекта

Разработчик: **Маслов Владислав**
📧 Email: [vladi4ej@gmail.com](mailto:vladi4ej@gmail.com)

---
