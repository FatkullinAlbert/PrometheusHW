# PrometheusHW
Домашнее задание на тему "Работа с Prometheus"
Задание:
Настроить дашборд с 4-мя графиками
память;
процессор;
диск;
сеть.
Настроить на одной из систем:
zabbix (использовать screen (комплексный экран);
prometheus - grafana.
У задания есть выбор, на чём его выполнять.
Буду использовать комбинацию Prometheus + Grafana, т.к. я уже пользвался ей.
Для начала нам надо скачать Prometheus, Node-Expoerter и Grafana.
Устанавливаем Prometheus и Node-Expoerter:
sudo apt install prometheus prometheus-node-exporter -y
sudo apt install prometheus
Устанавливаем Grafana:
sudo apt install -y software-properties-common wget
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
sudo apt install Grafana
echo "deb https://packages.grafana.com/oss/deb stable main" | sudo tee /etc/apt/sources.list.d/grafana.list
sudo apt install -y grafana
Проверяем работаспособность каждого из них:
sudo systemctl status prometheus
sudo systemctl status prometheus-node-exporter
sudo systemctl status grafana-server
После того как мы проверили их работу, мы можем настроить конфиг Prometheus предварительно проверив скрипт на работу:
promtool check config /etc/prometheus/prometheus.yml
После перезагрузки мы можем зайти на Prometheus (192.168.1.20:9090 у моей машины)и проверить его работаспособность
После этого мы заходим на Grafana (192.168.1.20:3000) и заходим. Во время первого захода там будет логин и пароль admin и admin, потом вы меняете пароль.
У нас перед нами пустая Grafana.
Для начала нам надо спуститься вниз и выбрать источник данных - кнопка "Add data source".
Там указываем, что нашим источником данных будет Prometheus, с последующим адресом (я указал localhost:9090)
После сохранения мы можем создавать dashboard'ы - доску изображёнными в графиках параметрами наших ВМ, т.е. визуализациями (vizualizations)
Заходим в Dashboard и нажимаем кнопку "New Dashboard", а в окне "Add Vizualization"
Настраиваем первую визуализацию - пусть это будет процессор. Мы внизу можем выбрать источник данных, формулу, с которой будут работать наши данные, а справа - представление наших данных и в какой величине.
После настройки нажимаем кнопку возвращения на окно dashboard и добавляем ещё визуализацию: по итогу добавив и сделав ещё 3 визуализации на память, диск и сеть мы выполняем наше задание.
Задание выполнено!
