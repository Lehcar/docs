---
title: Configurar servidores de nomes DNS
intro: 'O {% data variables.product.prodname_ghe_server %} usa o protocolo de configuração dinâmica de host (DHCP) para configurações de DNS quando as concessões de DHCP fornecem servidores de nomes. Se os servidores de nomes não forem fornecidos por uma concessão do protocolo DHCP, ou caso você precise usar configurações DNS específicas, será possível especificá-los manualmente.'
redirect_from:
  - /enterprise/admin/guides/installation/about-dns-nameservers
  - /enterprise/admin/installation/configuring-dns-nameservers
  - /enterprise/admin/configuration/configuring-dns-nameservers
  - /admin/configuration/configuring-dns-nameservers
versions:
  ghes: '*'
type: how_to
topics:
  - Enterprise
  - Fundamentals
  - Infrastructure
  - Networking
shortTitle: Configurar servidores DNS
---

Os servidores de nomes que você especificar devem resolver o nome de host da {% data variables.product.product_location %}.

{% data reusables.enterprise_installation.changing-hostname-not-supported %}

## Configurar servidores de nomes usando o console de máquina virtual

{% data reusables.enterprise_installation.open-vm-console-start %}
2. Configure os servidores de nomes da sua instância.
{% data reusables.enterprise_installation.vm-console-done %}

## Configurar servidores de nomes usando o shell administrativo

{% data reusables.enterprise_installation.ssh-into-instance %}

2. To edit your nameservers, use the `ghe-setup-network` command in visual mode. Para obter mais informações, consulte "[Utilitários de linha de comando](/admin/configuration/configuring-your-enterprise/command-line-utilities#ghe-setup-network)".

  ```shell
  ghe-setup-network -v
  ```

5. Para adicionar as suas novas entradas de nameserver para {% data variables.product.product_location %}, execute o seguinte:

  ```shell
  sudo service resolvconf restart
  sudo service dnsmasq restart
  ```
