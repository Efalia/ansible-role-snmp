SNMP
=========

Rôle mutualisant la configuration de snmp. 

Role Variables
--------------

rocommunity : communauté à utiliser dans le fichier de configuration.
use_snmp : détermine si le service doit être lancé.

Exemple
-------

```
  vars:
    rocommunity: "Efalia-DOC"
  pre_tasks:
    - name: Récupération du manifeste depuis son cache
      set_fact: manifest="{{ lookup('file', manifest_cache_file) }}"
    - name: Redémarrage du service snmpd si l'option est présente
      set_fact:
        use_snmp: "{{ (manifest.infra['snmp'] is defined and manifest.infra['snmp']) | bool }}"
  roles:
    - ../roles/snmp
```

License
-------

MIT
