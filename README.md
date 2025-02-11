**Zabbix Template** 

System Resources Monitoring 
Описание 

Шаблон для мониторинга основных ресурсов системы с помощью Zabbix. Включает метрики CPU, памяти, сетевого трафика и дискового пространства. 
Содержание шаблона 
Элементы данных: 

    CPU  
        Load Average
        CPU Usage (%)
         

    Память  
        Memory Total (B)
        Memory Usage (B)
         

    Сетевой трафик  (через правило обнаружения) 
        Incoming traffic (bps)
        Outgoing traffic (bps)
         

    Дисковое пространство  (через правило обнаружения) 
        Free Disk Space (B)
        Total Disk Space (B)
        Used Disk Space (B)
         
     

Правила обнаружения: 

    Network Interface Discovery  
        Условие: eth[0-9]+ | enp[0-9]+s[0-9]+ | wlan[0-9]+
         

    Disk Discovery (Universal)  
        Условие: Корневой раздел и стандартные директории (/bin, /boot, /dev, /etc, ...) + Windows диски (A-Z:)
         
     

Требования 

    Zabbix версии 6.0 или выше
     

Установка 

    Импортируйте шаблон через веб-интерфейс Zabbix
    Примените шаблон к нужным хостам
     

Примечания 

Шаблон не содержит конфиденциальной информации и может быть использован в любых целях. 
