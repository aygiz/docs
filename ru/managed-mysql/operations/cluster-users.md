# Управление пользователями БД

Вы можете добавлять и удалять пользователей, а также управлять их индивидуальными настройками.


## Получить список пользователей {#list-users}

{% list tabs %}

- Консоль управления
  
  1. Перейдите на страницу каталога и выберите сервис **{{ mmy-name }}**.
  1. Нажмите на имя нужного кластера, затем выберите вкладку **Пользователи**.

- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы получить список пользователей кластера, выполните команду:
  
  ```
  $ yc managed-mysql user list
       --cluster-name <имя кластера>
  ```
  
  Имя кластера можно запросить со [списком кластеров в каталоге](cluster-list.md).

{% endlist %}

## Добавить пользователя {#adduser}

{% note info %}

Назначать роли пользователям следует через консоль управления или API. Роли, назначенные командой `GRANT` в базе данных, сбросятся при внесении изменений через консоль управления или API.

{% endnote %}

{% list tabs %}

- Консоль управления
  
  1. Перейдите на страницу каталога и выберите сервис **{{ mmy-name }}**.
  1. Нажмите на имя нужного кластера и выберите вкладку **Пользователи**.
  1. Нажмите кнопку **Добавить**.
  1. Введите имя пользователя БД и пароль (от 8 до 128 символов).
  1. Выберите базу данных, доступ к которой получит пользователь.
  1. Выберите роль пользователя и нажмите кнопку **Добавить** под списком ролей. Повторите действие для всех нужных пользователю ролей.
  1. Нажмите кнопку **Добавить** в окне создания пользователя.

- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы создать пользователя в кластере, выполните команду:
  
  ```
  $ yc managed-mysql user create <имя пользователя>
       --cluster-name <имя кластера>
       --password=<пароль для пользователя>
       --permissions=<список баз, к которым пользователь получит доступ>
  ```
  
  Имя кластера можно запросить со [списком кластеров в каталоге](cluster-list.md).  

{% endlist %}

## Изменить пользователя {#updateuser}

Для пользователя можно изменить:

- имя и пароль;
- список баз, к которым у него есть доступ;
- ограничение на количество подключений к базам.

{% list tabs %}

- Консоль управления
  
  В консоли управления пока можно изменить только пароль пользователя БД:
  
  1. Перейдите на страницу каталога и выберите сервис **{{ mmy-name }}**.
  1. Нажмите на имя нужного кластера и выберите вкладку **Пользователи**.
  1. Нажмите значок ![image](../../_assets/vertical-ellipsis.svg) и выберите пункт **Изменить пароль**.

- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы изменить пароль пользователя или список доступных ему баз данных, выполните команду:
  
  ```
  $ yc managed-mysql user update <имя пользователя>
       --cluster-name <имя кластера>
       --password=<пароль для пользователя>
       --permissions=<список баз, к которым пользователь должен иметь доступ>
  ```
  
  Имя кластера можно запросить со [списком кластеров в каталоге](cluster-list.md).
  
{% endlist %}

## Удалить пользователя {#removeuser}

{% list tabs %}

- Консоль управления
  
  1. Перейдите на страницу каталога и выберите сервис **{{ mmy-name }}**.
  1. Нажмите на имя нужного кластера и выберите вкладку **Пользователи**.
  1. Нажмите значок ![image](../../_assets/vertical-ellipsis.svg) и выберите пункт **Удалить**.

- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы удалить пользователя, выполните команду:
  
  ```
  $ yc managed-mysql user delete <имя пользователя>
       --cluster-name <имя кластера>
  ```
  
  Имя кластера можно запросить со [списком кластеров в каталоге](cluster-list.md).
  
{% endlist %}
