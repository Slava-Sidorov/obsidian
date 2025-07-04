
1. **Что такое Prometheus и для чего он используется?**
   - Prometheus — это система мониторинга и сбора метрик с открытым исходным кодом, разработанная для высоконагруженных систем. Она собирает и хранит метрики из различных источников, используя pull-модель (запросы к сервисам). Prometheus популярен благодаря удобству настройки, гибкости и возможностям алертинга.

2. **Какие основные компоненты есть у Prometheus?**
   - Основные компоненты Prometheus включают:
      - *Prometheus Server*, который собирает и хранит метрики.
      - *Exporter*, предоставляющий метрики для Prometheus.
      - *Alertmanager*, обрабатывающий алерты и уведомления.
      - *Pushgateway*, позволяющий отправлять метрики от краткоживущих приложений.

3. **Что такое Exporter в Prometheus и для чего он нужен?**
   - Exporter — это приложение, которое преобразует данные из сервисов в метрики, понятные Prometheus. Например, `node_exporter` собирает метрики операционной системы, а `blackbox_exporter` позволяет отслеживать доступность ресурсов.

4. **Как Prometheus собирает метрики?**
   - Prometheus использует pull-модель для сбора метрик, запрашивая данные по HTTP на определённом endpoint, обычно `/metrics`. Также возможно использовать push-модель через Pushgateway для сборки метрик от краткоживущих процессов.

5. **Что такое Grafana и как она используется вместе с Prometheus?**
   - Grafana — это платформа для визуализации данных, которая интегрируется с Prometheus для создания наглядных панелей мониторинга. Grafana использует метрики из Prometheus для построения графиков и дашбордов, позволяя отслеживать состояние системы в реальном времени.

6. **Как создать алерт в Prometheus и отправить уведомление?**
   - В Prometheus алерты задаются в файле конфигурации с помощью Alertmanager. Можно создать правило, которое отслеживает определенные условия и отправляет уведомления, когда условия выполняются. Alertmanager управляет маршрутизацией и отправкой уведомлений через такие каналы, как email, Slack или другие мессенджеры.

7. **Как Prometheus хранит данные?**
   - Prometheus хранит временные ряды метрик на локальном диске в виде базы данных на основе *time-series*. Данные сохраняются в виде блоков с временными метками, метками и значениями. Хранилище Prometheus оптимизировано для хранения большого количества временных рядов.

8. **Что такое Labels в Prometheus, и как их использовать?**
   - Labels — это ключи и значения, которые добавляются к метрикам, чтобы различать и фильтровать их. Например, для метрики `http_requests_total` можно добавить метку `status="200"`, что позволит отдельно отслеживать успешные запросы.

9. **Как настроить Grafana для визуализации метрик Prometheus?**
   - В Grafana необходимо добавить источник данных Prometheus, указав его URL. После этого можно создавать панели и дашборды, используя Prometheus Query Language (PromQL) для выборки метрик, и настраивать графики под конкретные нужды.

10. **Что такое PromQL и как его использовать?**
    - PromQL (Prometheus Query Language) — это язык запросов Prometheus для получения и обработки метрик. Он позволяет выполнять выборку данных, задавать условия фильтрации по меткам, а также агрегировать и трансформировать метрики для построения графиков и создания алертов.
