Prometheus + Grafana — Ansible-автоматизация
Этот проект разворачивает стек мониторинга Prometheus и Grafana с помощью Ansible и Docker Compose.

Что делает:

Устанавливает docker и docker compose (если их нет)

Копирует docker-compose.yml на целевой сервер

Поднимает стек мониторинга в указанной директории

Использует Ansible Vault для безопасного хранения паролей Grafana

ansible-vault encrypt vault1.yml - шифоуем креды
 
Запуск:
ansible-playbook -i inventory.ini playbook.yml
--ask-vault-pass
--extra-vars "monitoring_stack_dir=/mnt/raid/monitoring" -> обязательно да целевом сервере, должна быть директория monitoring

Структура проекта:
monitoring-ansible-grafana-prometeus/
├── inventory.ini
├── playbook.yml
├── vault.yml ← зашифрованный файл с паролями Grafana
├── README ← этот файл
└── roles/
└── monitoring_stack/

Переменные:
monitoring_stack_dir — директория на целевом сервере, куда будет скопирован docker-compose.yml и развёрнут стек

Сервисы:

Prometheus: порт 9090

Grafana: порт 3000

Все данные сохраняются в Docker volume
