---
title: Connecter votre serveur SQL Server à l’aide de l’authentification Windows (Kerberos)
description: Découvrez comment connecter Azure Data Studio à SQL Server à l’aide de l’authentification intégrée Microsoft Kerberos.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.topic: conceptual
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: bb9735ec85ba8b6481156fb55e662bc55363dc7a
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89283731"
---
# <a name="connect-azure-data-studio-to-your-sql-server-using-windows-authentication---kerberos"></a>Connecter Azure Data Studio à votre serveur SQL Server à l’aide de l’authentification Windows - Kerberos

Azure Data Studio prend en charge la connexion à SQL Server à l’aide de Kerberos.

Pour utiliser l’authentification intégrée (authentification Windows) sur macOS ou Linux, vous devez configurer un **ticket Kerberos** qui lie votre utilisateur actuel à un compte de domaine Windows.

## <a name="prerequisites"></a>Prérequis

- Accédez à un ordinateur Windows joint à un domaine afin d’interroger votre contrôleur de domaine Kerberos.
- SQL Server doit être configuré pour autoriser l’authentification Kerberos. Pour le pilote client s’exécutant sur UNIX, l’authentification intégrée est prise en charge uniquement avec Kerberos. Pour plus d’informations, consultez [Utiliser l’authentification intégrée Kerberos pour se connecter à SQL Server](../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md). Des noms de principal du service doivent être inscrits pour chaque instance de SQL Server à laquelle vous essayez de vous connecter. Pour plus d’informations, consultez [Inscription d’un nom de principal du service](/previous-versions/sql/sql-server-2008-r2/ms191153(v=sql.105)#SPN%20Formats).


## <a name="checking-if-sql-server-has-kerberos-setup"></a>Vérification de la configuration de Kerberos pour SQL Server

Connectez-vous à l’ordinateur hôte de SQL Server. À partir de l’invite de commandes Windows, utilisez `setspn -L %COMPUTERNAME%` pour répertorier tous les noms de principal de service pour l’ordinateur hôte. Vous devez voir des entrées qui commencent par MSSQLSvc/HostName.Domain.com, ce qui signifie que SQL Server a inscrit un nom de principal du service et qu’il est prêt à accepter l’authentification Kerberos. 
- Si vous n’avez pas accès à l’hôte de SQL Server, à partir de tout autre système d’exploitation Windows joint au même Active Directory, vous pouvez utiliser la commande `setspn -L <SQLSERVER_NETBIOS>`, où <SQLSERVER_NETBIOS> est le nom de l’ordinateur hôte de SQL Server.


## <a name="get-the-kerberos-key-distribution-center"></a>Obtenir le centre de distribution de clés Kerberos

Recherchez la valeur de configuration du KDC (centre de distribution de clés) de Kerberos. Exécutez la commande suivante sur un ordinateur Windows joint à votre domaine Active Directory : 

Démarrez `cmd.exe` et exécutez `nltest`.

```
nltest /dsgetdc:DOMAIN.COMPANY.COM (where "DOMAIN.COMPANY.COM" maps to your domain's name)

Sample Output
DC: \\dc-33.domain.company.com
Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
...
The command completed successfully
```
Copiez le nom du contrôleur de domaine correspondant à la valeur de configuration KDC requise, dans ce cas dc-33.domain.company.com

## <a name="join-your-os-to-the-active-directory-domain-controller"></a>Joindre votre système d’exploitation au contrôleur de domaine Active Directory

### <a name="ubuntu"></a>Ubuntu
```bash
sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
```

Modifiez le fichier `/etc/network/interfaces` de sorte que l’adresse IP de votre contrôleur de domaine Active Directory soit répertoriée en tant que dns-nameserver. Par exemple : 

```/etc/network/interfaces
<...>
# The primary network interface
auth eth0
iface eth0 inet dhcp
dns-nameservers **<AD domain controller IP address>**
dns-search **<AD domain name>**
```

> [!NOTE]
> L’interface réseau (eth0) peut différer selon les machines. Pour déterminer celle que vous utilisez, exécutez ifconfig et copiez l’interface qui a une adresse IP et des octets transmis et reçus.

Après avoir modifié ce fichier, redémarrez le service réseau :

```bash
sudo ifdown eth0 && sudo ifup eth0
```

Vérifiez maintenant que votre fichier `/etc/resolv.conf` contient une ligne semblable à la suivante:  

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

Modifiez le fichier `/etc/sysconfig/network-scripts/ifcfg-eth0` (ou tout autre fichier de configuration d’interface selon le cas) afin que l’adresse IP de votre contrôleur de domaine Active Directory soit listée en tant que serveur DNS :

```/etc/sysconfig/network-scripts/ifcfg-eth0
<...>
PEERDNS=no
DNS1=**<AD domain controller IP address>**
```

Après avoir modifié ce fichier, redémarrez le service réseau :

```bash
sudo systemctl restart network
```

Vérifiez maintenant que votre fichier `/etc/resolv.conf` contient une ligne semblable à la suivante:  

```Code
nameserver **<AD domain controller IP address>**
```

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
   
```

### <a name="macos"></a>macOS

- Joignez votre macOS au contrôleur domaine Active Directory en procédant comme suit :

## <a name="configure-kdc-in-krb5conf"></a>Configurer KDC dans krb5.conf

Modifiez `/etc/krb5.conf` dans l’éditeur de votre choix. Configurez les clés suivantes

```bash
sudo vi /etc/krb5.conf

[libdefaults]
  default_realm = DOMAIN.COMPANY.COM
 
[realms]
DOMAIN.COMPANY.COM = {
   kdc = dc-33.domain.company.com
}
```

Enregistrez ensuite le fichier krb5.conf et quittez

> [!NOTE]
> Le domaine doit être en MAJUSCULES


## <a name="test-the-ticket-granting-ticket-retrieval"></a>Tester la récupération de ticket d’attribution de ticket

Obtenez un TGT (Ticket Granting Ticket) auprès du KDC.

```bash
kinit username@DOMAIN.COMPANY.COM
```

Affichez les tickets disponibles à l’aide de klist. Si kinit réussit, vous devez voir un ticket. 

```bash
klist

krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.
```

## <a name="connect-using-azure-data-studio"></a>Connexion à l’aide d’Azure Data Studio

* Créez un nouveau profil de connexion

* Choisissez **l’authentification Windows** comme type d’authentification

* Complétez le profil de connexion, puis cliquez sur **Se connecter**

Une fois la connexion établie, votre serveur s'affiche dans la barre latérale *Serveurs*.