## Alerte inondation

Pour informer rapidement en cas d’inondation, j’ai installé trois capteurs émettant des signaux d’alerte LoRa. Ces signaux sont « entendus » par une ou plusieurs passerelles, puis transmis au serveur de réseau LoRaWAN The Things Stack Community Edition (TTN CE).

Le broker MQTT de TTN CE publie alors toutes les alertes, instantanément récupérées dans un flow NodeRED. Après avoir traité les données reçues, des messages d’alerte sont envoyés par e-mail et/ou SMS. En même temps les données reçues sont stockées dans InfluxDB, pour une utilisation ultérieure depuis Grafana.

Afin d’identifier une éventuelles panne de capteur, les « preuves de vie » émises par les capteurs sont analysées régulièrement. Dès qu’une « preuve de vie » manque, un message de panne est envoyé par e-mail.

- NodeRED, InfluxDB et Grafana tournent dans une version supervised de « Home Assistant ».
- Passerelle utilisée: LPS8 Indoor LoRaWAN Gateway.
- Capteurs utilisés: Dragino LWL02. 
