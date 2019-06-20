---
title: Utiliser l’authentification Active Directory (Kerberos)
titleSuffix: Azure Data Studio
description: Découvrez comment activer l’authentification Kerberos utiliser l’authentification Active Directory pour Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: meet-bhagdev
ms.author: meetb
manager: jroth
ms.openlocfilehash: 4836b22d9903b05d70170aad53fde7ac7101f537
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66778380"
---
# <a name="connect-includename-sosincludesname-sos-shortmd-to-your-sql-server-using-windows-authentication---kerberos"></a>Se connecter [!INCLUDE[name-sos](../includes/name-sos-short.md)] à votre serveur SQL à l’aide de l’authentification Windows - Kerberos 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] prend en charge la connexion à SQL Server à l’aide de Kerberos.

Pour pouvoir utiliser l’authentification intégrée (authentification Windows) sur macOS ou Linux, vous devez configurer un **ticket Kerberos** liaison votre utilisateur actuel à un compte de domaine Windows. 

## <a name="prerequisites"></a>Configuration requise

- Accès à un ordinateur joint au domaine Windows pour interroger votre contrôleur de domaine Kerberos.
- SQL Server doit être configuré pour autoriser l’authentification Kerberos. Le pilote du client en cours d’exécution sur Unix, l’authentification intégrée est uniquement pris en charge à l’aide de Kerberos. Vous pouvez trouver plus d’informations sur la configuration de Sql Server pour s’authentifier à l’aide de Kerberos [ici](https://support.microsoft.com/help/319723/how-to-use-kerberos-authentication-in-sql-server). Il doit y être SPN inscrits pour chaque instance de Sql Server, vous essayez de vous connecter. Plus d’informations sur le format des noms principaux de service SQL Server [ici](https://technet.microsoft.com/library/ms191153%28v=sql.105%29.aspx#SPN%20Formats)


## <a name="checking-if-sql-server-has-kerberos-setup"></a>Vérification de l’installation de Kerberos si Sql Server

Connectez-vous à l’ordinateur hôte de Sql Server. À partir de l’invite de commandes Windows, utilisez le `setspn -L %COMPUTERNAME%` pour répertorier tous les noms de principal du Service pour l’hôte. Vous devez voir des entrées qui commencent par MSSQLSvc/HostName.Domain.com ce qui signifie que Sql Server a inscrit un SPN est prêt à accepter l’authentification Kerberos. 
- Si vous n’avez pas accès à l’hôte de Sql Server, à partir de n’importe quel autre Windows du système d’exploitation joint au même Active Directory, vous pouvez utiliser la commande `setspn -L <SQLSERVER_NETBIOS>` où < SQLSERVER_NETBIOS > est le nom d’ordinateur de l’hôte de Sql Server.


## <a name="get-the-kerberos-key-distribution-center"></a>Obtenir le centre de Distribution de clés Kerberos

Recherchez la valeur de configuration de Kerberos KDC (Key Distribution Center). Sur un ordinateur Windows qui est joint à votre domaine Active Directory, exécutez la commande suivante : 

Démarrer `cmd.exe` et exécutez `nltest`.

```
nltest /dsgetdc:DOMAIN.COMPANY.COM (where "DOMAIN.COMPANY.COM" maps to your domain's name)

Sample Output
DC: \\dc-33.domain.company.com
Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
...
The command completed successfully
```
Copiez le nom du contrôleur de domaine qui est la valeur de configuration KDC requise, dans ce cas dc-33.domain.company.com

## <a name="join-your-os-to-the-active-directory-domain-controller"></a>Joindre votre système d’exploitation pour le contrôleur de domaine Active Directory

### <a name="ubuntu"></a>Ubuntu
```bash
sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
```

Modifier la `/etc/network/interfaces` de fichiers afin que l’adresse IP de votre contrôleur domaine AD est répertorié comme un serveur de noms dns. Par exemple : 

```/etc/network/interfaces
<...>
# The primary network interface
auth eth0
iface eth0 inet dhcp
dns-nameservers **<AD domain controller IP address>**
dns-search **<AD domain name>**
```

> [!NOTE]
> L’interface réseau (eth0) peut-être différer pour des ordinateurs différents. Pour déterminer l’application que vous utilisez, exécutez ifconfig et copier l’interface qui possède une adresse IP et les octets transmis et reçus.

Après avoir modifié ce fichier, redémarrez le service de réseau :

```bash
sudo ifdown eth0 && sudo ifup eth0
```

Maintenant vérifier que votre `/etc/resolv.conf` fichier contient une ligne semblable à la suivante :  

```Code
nameserver **<AD domain controller IP address>**
```

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
```
   
### <a name="redhat-enterprise-linux"></a>RedHat Enterprise Linux
```bash
sudo yum install realmd krb5-workstation
```

Modifier le `/etc/sysconfig/network-scripts/ifcfg-eth0` fichier (ou autres config interface fichier selon le cas) afin que l’adresse IP de votre contrôleur domaine AD est répertorié comme un serveur DNS :

```/etc/sysconfig/network-scripts/ifcfg-eth0
<...>
PEERDNS=no
DNS1=**<AD domain controller IP address>**
```

Après avoir modifié ce fichier, redémarrez le service de réseau :

```bash
sudo systemctl restart network
```

Maintenant vérifier que votre `/etc/resolv.conf` fichier contient une ligne semblable à la suivante :  

```Code
nameserver **<AD domain controller IP address>**
```

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
   
```

### <a name="macos"></a>macOS

- Joignez votre macOS pour le contrôleur de domaine Active Directory en procédant comme suit :



## <a name="configure-kdc-in-krb5conf"></a>Configurer le contrôleur de domaine Kerberos dans krb5.conf

Modifier le `/etc/krb5.conf` dans un éditeur de votre choix. Configurez les clés suivantes

```bash
sudo vi /etc/krb5.conf

[libdefaults]
  default_realm = DOMAIN.COMPANY.COM
 
[realms]
DOMAIN.COMPANY.COM = {
   kdc = dc-33.domain.company.com
}
```

Puis enregistrez le fichier krb5.conf et sortie

> [!NOTE]
> Domaine doit être en majuscules


## <a name="test-the-ticket-granting-ticket-retrieval"></a>Tester la récupération de Ticket Granting Ticket

Obtenir un Ticket d’accord de Ticket (TGT ticket) à partir du contrôleur de domaine Kerberos.

```bash
kinit username@DOMAIN.COMPANY.COM
```

Afficher les tickets disponibles à l’aide de kinit. Si le kinit a réussi, vous devez voir un ticket. 

```bash
klist

krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.
```

## <a name="connect-using-includename-sosincludesname-sos-shortmd"></a>Se connecter à l’aide de [!INCLUDE[name-sos](../includes/name-sos-short.md)]

* Créer un nouveau profil de connexion

* Choisissez **l’authentification Windows** comme type d’authentification

* Terminez le profil de connexion, cliquez sur **Connect**

Une fois connecté, votre serveur s’affiche dans le *serveurs* encadré.
