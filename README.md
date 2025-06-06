# Отключить обновления Windows

![](https://i.imgur.com/pGsWaOt.png 'Что-то пошло не так')

⚡ Отключение автоматических обновлений в один клик, без фоновых процессов.

> [!WARNING]
> Перед запуском этого скрипта убедитесь, что Windows полностью обновлена и в данный момент не устанавливает или не загружает обновления! Прерывание обновления может привести к поломке вашей установки Windows!

---

## Как использовать

### Просто!

1.  **Клонируйте или скачайте:**

    * Клонируйте этот репозиторий с помощью `git clone https://github.com/tsgrgo/windows-update-disabler.git` или скачайте его как ZIP-файл и распакуйте.

2.  **Проверьте наличие активных обновлений:**

    * Убедитесь, что в данный момент не устанавливаются обновления. Перейдите в **Настройки > Обновление и безопасность > Центр обновления Windows** и проверьте.

3.  **Запустите скрипт:**

    * Запустите `disable updates.bat`. Это отключит автоматические обновления Windows.

4.  **Повторное включение обновлений (необязательно):**

    * Если вам нужно снова разрешить автоматические обновления, запустите `enable updates.bat`. Это полностью обратная функция `disable updates.bat` и отменит все внесенные изменения.

---

## Как обновлять вручную

Регулярные обновления рекомендуются для безопасности. Для обновления вручную:

1.  **Включите обновления:**

    * Запустите `enable updates.bat`, чтобы повторно включить Центр обновления Windows.

2.  **Выполните обновления:**

    * Перейдите в **Настройки > Обновление и безопасность > Центр обновления Windows** и установите доступные обновления.

3.  **Снова отключите обновления:**

    * После обновления снова запустите `disable updates.bat`, чтобы отключить автоматические обновления.

---

## Использование службы обновлений временно

Некоторые приложения, такие как Microsoft Store, зависят от службы Центра обновления Windows. Чтобы временно включить службу:

1.  **Включите службу обновлений:**

    * Запустите `use update service.bat`, чтобы повторно включить службу Центра обновления Windows.

2.  **Используйте зависимые приложения:**

    * Теперь вы можете использовать приложения, которым требуется служба обновлений.

3.  **Снова отключите службу обновлений:**

    * После завершения работы снова запустите `disable updates.bat`, чтобы отключить службу обновлений.

---

## Что делает скрипт

Скрипт выполняет следующие действия для отключения автоматических обновлений:

* Отключает **службу Центра обновления Windows (wuauserv)**.
* Отключает **службу оркестрации обновлений (UsoSvc)**.
* Отключает **службу восстановления Центра обновления Windows (WaaSMedicSvc)**.
* Отключает все запланированные задачи, связанные с обновлениями.
* Применяет изменения в реестре для предотвращения автоматических обновлений.

---

## Зачем нужен PsExec?

Некоторые из задействованных служб и задач защищены от учетных записей пользователей и требуют повышенных системных привилегий для изменения. PsExec позволяет скрипту выполнять команды с необходимыми разрешениями для обхода этих ограничений.

PsExec является частью официального пакета Sysinternals от Microsoft. Дополнительная информация: https://docs.microsoft.com/en-us/sysinternals/downloads/psexec
