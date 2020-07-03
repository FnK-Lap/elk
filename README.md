# elk

## Docker logs stdout

Ajouter la partie `logging` sur les contaier dans le `docker-compose.yml`

```
  php:
    image:  # ...
    # ...
    logging:
      driver: gelf
      options:
        gelf-address: "udp://localhost:12201"
        tag: "{{ value }}" # Un champs `tag` sera ajoute au log avec la valeur `{{ value }}`
```	

`./data` : Données d'elasticsearch
`./savedObjects` : Visualisations / Dashboards / ... par defaut a importer dans Kibana si besoin
`./elasticsearch.yml` : Fichier de config d'elasticsearch
`./logstash.conf` : Fichier de config dde Logstash

### Saved Objects

1. Types :
	- `query_*` : Type Query

2. Saved Objects :

- `query_grok_parse_failure.ndjson` : Liste de toutes less erreurs de parsing Grok. Ajouter des filtres correspondant dans le fichier `./logstash.conf`
