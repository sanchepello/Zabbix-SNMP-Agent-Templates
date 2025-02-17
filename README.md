**System Performance Monitoring Template for Zabbix**

**Описание**

Этот репозиторий содержит шаблон для мониторинга производительности системы с помощью Zabbix версии 6.0. Шаблон включает набор элементов (items), триггеров и меток для детального анализа загрузки процессора, использования оперативной памяти (RAM) и других ключевых метрик производительности.

Шаблон разработан для упрощения настройки мониторинга систем и предоставления четких предупреждений о проблемах производительности.

**Содержание**

1. [Описание]
1. [Структура шаблона]
1. [Основные компоненты]
1. [Использование]
1. [Теги]
1. [Примеры триггеров]

**Структура шаблона**

Шаблон организован следующим образом:

- **Группы** : Все шаблоны относятся к группе MFCTemplates.
- **Items** : Включают метрики для CPU, RAM и других компонентов системы.
- **Triggers** : Предопределенные условия для оповещения о проблемах производительности.

**Основные компоненты**

**Items**

|CPU Core Load|system.cpu.load[percpu,avg1]|Средняя нагрузка на процессор за последнюю минуту.|
| - | - | - |
|CPU Utilization (%)|system.cpu.util[,,]|Использование процессора в процентах.|
|Free RAM|vm.memory.size[free]|Доступное количество оперативной памяти.|

**Triggers**

|High CPU Load|last(/System Performance/system.cpu.load[percpu,avg1]) > 5|AVERAGE|Высокая нагрузка на процессор.|
| - | - | - | - |
|High CPU Usage|avg(/System Performance/system.cpu.util[,,],5m) > 80|HIGH|Высокое использование процессора более 80%.|
|Low Free RAM|last(/System Performance/vm.memory.size[free]) < [критическое значение]|CRITICAL|Недостаточно свободной оперативной памяти.|

**Установка**

1. Скачайте файл экспорта шаблона (zabbix\_export.yaml или аналогичный).
1. Импортируйте шаблон в Zabbix через интерфейс:
   1. Перейдите в раздел **Configuration -> Templates** .
   1. Нажмите кнопку **Import** .
   1. Выберите скачанный файл шаблона.
1. Примените шаблон к нужным хостам.

**Использование**

1. После импорта шаблона все настроенные метрики автоматически начинают собираться.
1. Проверьте графики производительности в разделе **Monitoring -> Graphs** .
1. Настройте оповещения для активации при срабатывании триггеров.

**Теги**

Каждый элемент и триггер помечен тегами для удобства фильтрации и управления:

- **component** : cpu, memory
- **metric** : load, usage, free
- **purpose** : status, performance

Пример:

>tags:
>
>\- tag: component
>
>value: cpu
>
>\- tag: metric
>
>value: load
>
>\- tag: purpose
>
>value: status

**Примеры триггеров**

**Пример 1: Высокая нагрузка на CPU**

>expression: 'last(/System Performance/system.cpu.load[percpu,avg1]) > 5'
>
>name: 'High CPU Load'
>
>priority: AVERAGE
>
>description: 'Высокая нагрузка на CPU'

**Пример 2: Высокое использование CPU**

>expression: 'avg(/System Performance/system.cpu.util[,,],5m) > 80'
>
>name: 'High CPU Usage'
>
>priority: HIGH
>
>description: 'Высокое использование CPU'

**Пример 3: Низкий уровень свободной RAM**

>expression: 'last(/System Performance/vm.memory.size[free]) < [критическое значение]'
>
>name: 'Low Free RAM'
>
>priority: CRITICAL
>
>description: 'Недостаточно свободной оперативной памяти'

**Лицензия**

Этот проект распространяется под лицензией MIT. Подробности см. в файле [LICENSE](https://chat.qwenlm.ai/c/LICENSE) .

**Авторы**

- **sanchepello**
  - Email: sancheuz401@gmail.com
  - GitHub: https://github.com/sanchepello
