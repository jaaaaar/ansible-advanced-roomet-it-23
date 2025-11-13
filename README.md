# Ansible Edasijõudnud Labor: Templates ja Vault

**Autor:** Roomet  
**Kursus:** it-23

See pakett sisaldab täielikku Ansible projekti struktuuri vastavalt antud juhendile:
- templates (Jinja2 mallid: Apache, MySQL, PHP-FPM)
- inventory (hosts.yml)
- group_vars, host_vars (näidismuutujad)
- playbooks (site.yml)
- ansible.cfg
- .gitignore

**Kasutus:**
1. Vaata läbi `group_vars/all/vault.yml` ja krüpteeri see Ansible Vault'iga:
   ```bash
   ansible-vault encrypt group_vars/all/vault.yml
   ```
   või loo uus:
   ```bash
   ansible-vault create group_vars/all/vault.yml
   ```

2. Käivita süntaksikontroll:
   ```bash
   ansible-playbook --syntax-check playbooks/site.yml
   ```

3. Kuiv jooks (`--check`) ja/või päris jooks:
   ```bash
   ansible-playbook -i inventory/hosts.yml playbooks/site.yml --check
   ansible-playbook -i inventory/hosts.yml playbooks/site.yml --ask-vault-pass
   ```

**Märkused:**
- Paroolid/võtmed on näidatud näitena – krüpteeri `group_vars/all/vault.yml` enne kasutamist produktiivkeskkonnas.
- `.vault_pass` EI OLE lisatud repositooriumi. Lisa see oma CI/CD jaoks turvaliselt ja lisa `.gitignore`-i.

