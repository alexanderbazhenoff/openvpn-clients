## openvpn-clients ansible role
Stop your hand work with OpenVPN client sertificates.

### Required:

1. ansible>=2.2.
2. zip and python packages installed on OpenVPN server.
3. Specify path for the all ansible roles in ansible.cfg: `roles_path = /path/to/directory/with/roles/`.
   E.g: `roles_path = ~/ansible/roles/`

### Usage:

Use global hosts settings (readme will be updated) or run *.yml files with `-i inventory` to override them:

1. Specify OpenVPN server IP/FQDN and credentials in **openvpn-users/inventory** file.
2. Run: `ansible-playbook <playbook-name>.yml -i inventory`, which is:

- **tests/openvpn_make_user.yml** - Create OpenVPN client sertificate for input username and send them (with instructions) via email. Please check `var/main.yml` for additional settings.
- **tests/openvpn_make_mobile.yml** - Create .ovpn file for clients (mostly mobile devices) and send them (with other keys and instructions) via email.
- **tests/openvpn_resend.yml** - Just resend all existing keys, .ovpn file (if exists) and instructions via email. No changes on OpenVPN server.
- **tests/openvpn_revoke_user.yml** - Revoke OpenVPN client certificate for input username. All pem-certificate-releated errors will be ignored and certs will be removed from the server.
- **tests/openvpn_show_stat.yml** - Show list of client certificates on OpenVPN server.

**Please note:** you should enter username ***without*** email domain, e.g: **j.doe** instead of **j.doe@domain.com**. Follow the credentials standart of naming: jdoe - wrong name, j.doe - right.
