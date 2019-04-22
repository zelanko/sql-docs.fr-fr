---
title: Jointure de SQL Server sur Linux à Active Directory
titleSuffix: SQL Server
description: ''
author: Dylan-MSFT
ms.author: Dylan.Gray
ms.reviewer: rothja
ms.date: 04/01/2019
manager: craigg
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 6ccc94acb42fa7043912099c4888834cf4ff3e71
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59243583"
---
# <a name="join-sql-server-on-a-linux-host-to-an-active-directory-domain"></a>Jointure de SQL Server sur un hôte Linux à un domaine Active Directory

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article fournit des indications générales sur la façon de joindre un ordinateur hôte de SQL Server Linux à un domaine Active Directory (AD). Il existe deux méthodes : utilisez un package SSSD intégré ou utiliser des fournisseurs tiers Active Directory. Exemples de produits de jonction de domaine tiers sont [PowerBroker identité Services (pbi)](https://www.beyondtrust.com/), [une seule identité](https://www.oneidentity.com/products/authentication-services/), et [Centrify](https://www.centrify.com/). Ce guide comprend les étapes permettant de vérifier votre configuration Active Directory. Toutefois, il n’est pas conçu pour fournir des instructions sur la façon de joindre un ordinateur à un domaine lors de l’utilisation des utilitaires tiers.

## <a name="prerequisites"></a>Prérequis

Avant de configurer l’authentification Active Directory, vous devez configurer un Active Directory contrôleur de domaine Windows, sur votre réseau. Ensuite, joindre votre serveur SQL Server sur un hôte Linux à un domaine Active Directory.

> [!IMPORTANT]
> Les étapes de l’exemple décrits dans cet article sont à titre indicatif uniquement. Étapes réelles peuvent différer légèrement dans votre environnement en fonction de la configuration de votre environnement global. Impliquez vos administrateurs système et de domaine pour votre environnement de configuration spécifique, la personnalisation et nécessaire la résolution des problèmes.

## <a name="check-the-connection-to-a-domain-controller"></a>Vérifiez la connexion à un contrôleur de domaine

Vérifiez que vous pouvez contacter le contrôleur de domaine avec les noms courts et qualifiés complet du domaine :

```bash
ping contoso
ping contoso.com
```

> [!TIP]
> Ce didacticiel utilise **contoso.com** et **CONTOSO.COM** comme exemples de noms de domaine et le domaine, respectivement. Il utilise également **DC1. CONTOSO.COM** comme l’exemple de nom de domaine du contrôleur de domaine complet. Vous devez remplacer ces noms par vos propres valeurs.

Si une de ces vérifications de nom échoue, mettez à jour votre liste de recherche du domaine. Les sections suivantes fournissent des instructions pour Ubuntu, Red Hat Enterprise Linux (RHEL) et SUSE Linux Enterprise Server (SLES) respectivement.

### <a name="ubuntu"></a>Ubuntu

1. Modifier le **/etc/network/interfaces** fichiers, afin que votre domaine Active Directory est dans la liste de recherche du domaine :

   ```/etc/network/interfaces
   # The primary network interface
   auto eth0
   iface eth0 inet dhcp
   dns-nameservers **<AD domain controller IP address>**
   dns-search **<AD domain name>**
   ```

   > [!NOTE]
   > L’interface réseau, `eth0`, peuvent différer pour des ordinateurs différents. Pour connaître le celui que vous utilisez, exécutez **ifconfig**. Copiez ensuite l’interface qui a une adresse IP et les octets transmis et reçus.

1. Après avoir modifié ce fichier, redémarrez le service de réseau :

   ```bash
   sudo ifdown eth0 && sudo ifup eth0
   ```

1. Ensuite, vérifiez que votre **/etc/resolv.conf** fichier contient une ligne comme dans l’exemple suivant :

   ```/etc/resolv.conf
   search contoso.com com  
   nameserver **<AD domain controller IP address>**
   ```

### <a name="rhel"></a>RHEL

1. Modifier le **/etc/sysconfig/network-scripts/ifcfg-eth0** fichiers, afin que votre domaine Active Directory est dans la liste de recherche du domaine. Ou modifiez un autre fichier de configuration d’interface comme il convient :

   ```/etc/sysconfig/network-scripts/ifcfg-eth0
   PEERDNS=no
   DNS1=**<AD domain controller IP address>**
   DOMAIN="contoso.com com"
   ```

1. Après avoir modifié ce fichier, redémarrez le service de réseau :

   ```bash
   sudo systemctl restart network
   ```

1. Maintenant vérifier que votre **/etc/resolv.conf** fichier contient une ligne comme dans l’exemple suivant :

   ```/etc/resolv.conf
   search contoso.com com  
   nameserver **<AD domain controller IP address>**
   ```

1. Si vous ne pouvez pas toujours tester le contrôleur de domaine, recherchez le nom de domaine complet et l’adresse IP du contrôleur de domaine. Est un exemple de nom de domaine **DC1. CONTOSO.COM**. Ajoutez l’entrée suivante à **/etc/hosts**:

   ```/etc/hosts
   **<IP address>** DC1.CONTOSO.COM CONTOSO.COM CONTOSO
   ```

### <a name="sles"></a>SLES

1. Modifier le **/etc/sysconfig/network/config** fichiers, afin que votre contrôleur de domaine Active Directory adresse IP est utilisée pour les requêtes DNS et votre domaine Active Directory est dans la liste de recherche du domaine :

   ```/etc/sysconfig/network/config
   NETCONFIG_DNS_STATIC_SEARCHLIST=""
   NETCONFIG_DNS_STATIC_SERVERS="**<AD domain controller IP address>**"
   ```

1. Après avoir modifié ce fichier, redémarrez le service de réseau :

   ```bash
   sudo systemctl restart network
   ```

1. Ensuite, vérifiez que votre **/etc/resolv.conf** fichier contient une ligne comme dans l’exemple suivant :

   ```/etc/resolv.conf
   search contoso.com com
   nameserver **<AD domain controller IP address>**
   ```

## <a name="join-to-the-ad-domain"></a>Joindre au domaine Active Directory.

Après avoir vérifié la configuration de base et la connectivité avec le contrôleur de domaine, il existe deux options pour joindre un ordinateur hôte de SQL Server Linux avec le contrôleur de domaine Active Directory :

- [Option 1 : Utiliser un package SSSD](#option1)
- [Option 2 : Utilisez les utilitaires de fournisseur tiers openldap](#option2)

### <a id="option1"></a> Option 1 : Utiliser le package SSSD pour joindre le domaine Active Directory

Cette méthode joint l’hôte SQL Server à un domaine AD à l’aide **realmd** et **sssd** packages.

> [!NOTE]
> Il s’agit de la méthode préférée de joindre un hôte Linux à un contrôleur de domaine Active Directory.

Utilisez les étapes suivantes pour joindre un ordinateur hôte SQL Server à un domaine Active Directory :

1. Utilisez [realmd](https://www.freedesktop.org/software/realmd/docs/guide-active-directory-join.md) pour joindre votre ordinateur hôte à votre domaine Active Directory. Vous devez d’abord installer les deux le **realmd** et packages de client Kerberos sur l’ordinateur hôte de SQL Server à l’aide du Gestionnaire de package de votre distribution Linux :

   **RHEL:**

   ```base
   sudo yum install realmd krb5-workstation
   ```

   **SUSE :**

   ```bash
   sudo zypper install realmd krb5-client
   ```

   **Ubuntu :**

   ```bash
   sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
   ```

1. Si l’installation du package client Kerberos vous invite à entrer un nom de domaine, entrez votre nom de domaine en majuscules.

1. Après avoir confirmé que votre serveur DNS est correctement configuré, joindre le domaine en exécutant la commande suivante. Vous devez vous authentifier à l’aide d’un compte AD qui dispose de privilèges suffisants dans Active Directory pour joindre un nouvel ordinateur au domaine. Cette commande crée un nouveau compte d’ordinateur dans AD, crée le **/etc/krb5.keytab** héberger le fichier keytab, configure le domaine dans **/etc/sssd/sssd.conf**et les mises à jour **/etc/krb5.conf**.

   ```bash
   sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
   ```

   Vous devez voir le message, `Successfully enrolled machine in realm`.

   Le tableau suivant répertorie certains messages d’erreur que vous pourriez recevoir et des suggestions sur les résoudre :

   | Message d'erreur | Recommandation |
   |---|---|
   | `Necessary packages are not installed` | Installer ces packages à l’aide du Gestionnaire de package de votre distribution Linux avant de réexécuter la commande de jointure de domaine. |
   | `Insufficient permissions to join the domain` | Un administrateur de domaine, vérifiez que vous disposez des autorisations suffisantes pour joindre des ordinateurs Linux à votre domaine. |
   | `KDC reply did not match expectations` | Vous n’avez ne peut-être pas spécifié le nom de domaine correct pour l’utilisateur. Noms de domaine respectent la casse, généralement en majuscules et peuvent être identifiés avec le domaine de la commande découvrir contoso.com. |

   SQL Server utilise SSSD et NSS pour le mappage des comptes d’utilisateurs et groupes pour les identificateurs de sécurité (SID). SSSD doit être configuré et en cours d’exécution pour SQL Server créer les connexions AD avec succès. **realmd** généralement cela automatiquement dans le cadre de joindre le domaine, mais dans certains cas, vous devez le faire séparément.

   Pour plus d’informations, consultez Comment [configurer manuellement les SSSD](https://access.redhat.com/articles/3023951), et [configurer NSS pour travailler avec SSSD](https://access.redhat.com/documentation/red_hat_enterprise_linux/7/html/system-level_authentication_guide/configuring_services#Configuration_Options-NSS_Configuration_Options).

1. Vérifiez que vous pouvez maintenant collecter des informations sur un utilisateur à partir du domaine, et que vous pouvez acquérir un ticket Kerberos en tant que cet utilisateur. L’exemple suivant utilise **id**, [kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html), et [klist](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/klist.html) commandes pour cela.

   ```bash
   id user@contoso.com

   uid=1348601103(user@contoso.com) gid=1348600513(domain group@contoso.com) groups=1348600513(domain group@contoso.com)

   kinit user@CONTOSO.COM

   Password for user@CONTOSO.COM:

   klist
   Ticket cache: FILE:/tmp/krb5cc_1000
   Default principal: user@CONTOSO.COM
   ```

   > [!NOTE]
   > - Si **id user@contoso.com**  retourne, `No such user`, assurez-vous que le service SSSD démarrée avec succès en exécutant la commande `sudo systemctl status sssd`. Si le service est en cours d’exécution et que vous voyez toujours l’erreur, essayez d’activer la journalisation documentée pour SSSD. Pour plus d’informations, consultez la documentation de Red Hat pour [SSSD dépannage](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/System-Level_Authentication_Guide/trouble.html#SSSD-Troubleshooting).
   >
   > - Si **kinit user@CONTOSO.COM**  retourne, `KDC reply did not match expectations while getting initial credentials`, assurez-vous que vous avez spécifié le domaine en majuscules.

Pour plus d’informations, consultez la documentation de Red Hat pour [découverte et jonction à des domaines identité](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/realmd-domain.html).

### <a id="option2"></a> Option 2 : Utilisez les utilitaires de fournisseur tiers openldap

Vous pouvez utiliser les utilitaires tiers tels que [pbi](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/), ou [Centrify](https://www.centrify.com/). Cet article ne couvre pas les étapes pour chaque utilitaire individuel. Vous devez tout d’abord utiliser un de ces utilitaires pour joindre l’hôte Linux pour SQL Server au domaine avant de poursuivre vers l’avant.  

SQL Server n’utilise pas de code ou une bibliothèque de fournisseurs tiers intégrateur pour toutes les requêtes liées à AD. SQL Server interroge toujours AD à l’aide d’appels à des bibliothèques openldap directement dans ce programme d’installation. Les intégrateurs de fournisseurs tiers sont uniquement utilisées pour joindre l’ordinateur hôte Linux au domaine AD et SQL Server n’a pas de toute communication directe avec ces utilitaires.

> [!IMPORTANT]
> Veuillez consultez les recommandations relatives à l’aide de la **mssql-conf** `network.disablesssd` option de configuration dans le **options de configuration supplémentaires** section de l’article [utilisation Active L’authentification Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md#additionalconfig).

Vérifiez que votre **/etc/krb5.conf** est correctement configuré. Pour la plupart des fournisseurs d’Active Directory par des tiers, cette configuration est effectuée automatiquement. Toutefois, vérifiez **/etc/krb5.conf** pour les valeurs suivantes empêcher les problèmes futurs :

```/etc/krb5.conf
[libdefaults]
default_realm = CONTOSO.COM

[realms]
CONTOSO.COM = {
}

[domain_realm]
contoso.com = CONTOSO.COM
.contoso.com = CONTOSO.COM
```

## <a name="check-that-the-reverse-dns-is-properly-configured"></a>Vérifiez que le DNS inversé est correctement configuré

La commande suivante doit renvoyer le nom de domaine complet (FQDN) de l’hôte qui exécute SQL Server. Par exemple, **SqlHost.contoso.com**.

```bash
host **<IP address of SQL Server host>**
```

La sortie de cette commande doit être similaire à `**<reversed IP address>**.in-addr.arpa domain name pointer SqlHost.contoso.com`. Si cette commande ne retourne pas de nom de domaine complet de votre hôte, ou si le nom de domaine complet est incorrect, ajoutez une entrée DNS inversée pour votre serveur SQL Server sur un hôte Linux à votre serveur DNS.

## <a name="next-steps"></a>Étapes suivantes

Cet article décrit les conditions préalables de la configuration d’un serveur SQL Server sur un ordinateur hôte de Linux avec l’authentification Active Directory. Pour terminer la configuration de SQL Server sur Linux pour prendre en charge les comptes Active Directory, suivez les instructions de [l’authentification d’utilisation d’Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md).