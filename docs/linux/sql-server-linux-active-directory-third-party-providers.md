---
title: Utiliser des fournisseurs d’Active Directory tiers avec SQL Server sur Linux
titleSuffix: SQL Server
description: Ce didacticiel décrit les étapes de configuration d’authentification Active Directory avec des fournisseurs tiers
author: dylan-MSFT
ms.date: 07/25/2018
ms.author: dygray
manager: mikehab
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux, seodec18
ms.technology: linux
helpviewer_keywords:
- Linux, AD authentication
ms.openlocfilehash: de28696efd16a2be61864a810b3fd713b1066258
ms.sourcegitcommit: de8ef246a74c935c5098713f14e9dd06c4733713
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160567"
---
# <a name="use-third-party-active-directory-providers-with-sql-server-on-linux"></a>Utiliser des fournisseurs d’Active Directory tiers avec SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article explique comment configurer un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur un ordinateur hôte de Linux avec l’authentification Active Directory lors de l’utilisation de fournisseurs d’Active Directory par des tiers. Sont des exemples [PowerBroker identité Services (pbi)](https://www.beyondtrust.com/), [une seule identité](https://www.oneidentity.com/products/authentication-services/), et [Centrify](https://www.centrify.com/). Ce guide comprend les étapes permettant de vérifier votre configuration Active Directory. Il n’est pas destinée à vous aiguillent sur la façon de joindre un ordinateur à un domaine. Pour obtenir des instructions détaillées sur la jonction un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] hôte à un domaine à l’aide de realmd et SSSD, consultez [l’authentification d’utilisation d’Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md).

## <a name="prerequisites"></a>Prérequis

Avant de configurer l’authentification Active Directory, vous devez configurer un Active Directory contrôleur de domaine Windows, sur votre réseau. Puis joignez votre [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur un hôte Linux à un domaine Active Directory. Vous pouvez utiliser [pbi](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/), ou [Centrify](https://www.centrify.com/).

> [!NOTE]
>
>Ce didacticiel utilise **`contoso.com`** et **`CONTOSO.COM`** en tant qu’exemples de noms de domaine et le domaine, respectivement. Il utilise également **`DC1.CONTOSO.COM`** comme l’exemple de nom de domaine du contrôleur de domaine complet. Vous devez remplacer ces noms par vos propres valeurs.

## <a name="check-the-connection-to-a-domain-controller"></a>Vérifiez la connexion à un contrôleur de domaine

Vérifiez que vous pouvez contacter le contrôleur de domaine avec les noms courts et qualifiés complet du domaine :

```bash
ping contoso

ping contoso.com
```

Si une de ces vérifications de nom échoue, mettez à jour votre liste de recherche du domaine :

- **Ubuntu**

  Modifier la `/etc/network/interfaces` fichiers, afin que votre domaine Active Directory est dans la liste de recherche du domaine : 

  ```/etc/network/interfaces
  <...>
  # The primary network interface
  auto eth0
  iface eth0 inet dhcp
  dns-nameservers **<AD domain controller IP address>**
  dns-search **<AD domain name>**
  ```

  > [!NOTE]  
  > L’interface réseau, **eth0**, peuvent différer pour des ordinateurs différents. Pour connaître le celui que vous utilisez, exécutez **ifconfig**. Copiez ensuite l’interface qui a une adresse IP et les octets transmis et reçus.

  Après avoir modifié ce fichier, redémarrez le service de réseau :

  ```bash
  sudo ifdown eth0 && sudo ifup eth0
  ```

  Maintenant vérifier que votre `/etc/resolv.conf` fichier contient une ligne comme dans l’exemple suivant :  

  ```/etc/resolv.conf
  search contoso.com com  
  nameserver **<AD domain controller IP address>**
  ```

- **RHEL**

  Modifier la `/etc/sysconfig/network-scripts/ifcfg-eth0` fichiers, afin que votre domaine Active Directory est dans la liste de recherche du domaine. Ou modifiez un autre fichier de configuration d’interface comme il convient :

  ```/etc/sysconfig/network-scripts/ifcfg-eth0
  <...>
  PEERDNS=no
  DNS1=**<AD domain controller IP address>**
  DOMAIN="contoso.com com"
  ```

  Après avoir modifié ce fichier, redémarrez le service de réseau :

  ```bash
  sudo systemctl restart network
  ```

  Maintenant vérifier que votre `/etc/resolv.conf` fichier contient une ligne comme dans l’exemple suivant :  

  ```/etc/resolv.conf
  search contoso.com com  
  nameserver **<AD domain controller IP address>**
  ```

  Si vous ne pouvez pas toujours tester le contrôleur de domaine, recherchez le nom de domaine complet et l’adresse IP du contrôleur de domaine. Un exemple de nom de domaine est `DC1.CONTOSO.COM`. Ajoutez l’entrée suivante à `/etc/hosts`:

  ```/etc/hosts
  **<IP address>** DC1.CONTOSO.COM CONTOSO.COM CONTOSO
  ```

- **SLES**

  Modifier la `/etc/sysconfig/network/config` fichiers, afin que votre IP de contrôleur de domaine Active Directory est utilisé pour les requêtes DNS et votre domaine Active Directory est dans la liste de recherche du domaine :

  ```/etc/sysconfig/network/config
  <...>
  NETCONFIG_DNS_STATIC_SEARCHLIST=""
  NETCONFIG_DNS_STATIC_SERVERS="**<AD domain controller IP address>**"
  ```

  Après avoir modifié ce fichier, redémarrez le service de réseau :

  ```bash
  sudo systemctl restart network
  ```

  Maintenant vérifier que votre `/etc/resolv.conf` fichier contient une ligne comme dans l’exemple suivant :

  ```/etc/resolv.conf
  search contoso.com com
  nameserver **<AD domain controller IP address>**
  ```

## <a name="check-that-the-reverse-dns-is-properly-configured"></a>Vérifiez que le DNS inversé est correctement configuré

La commande suivante doit retourner le nom de domaine complet de l’hôte qui exécute SQL Server. Par exemple, **`SqlHost.contoso.com`**.

```bash
host **<IP address of SQL Server host>**
# **<reversed IP address>**.in-addr.arpa domain name pointerSqlHost.contoso.com.
```

Si cette commande ne retourne le nom de domaine complet de votre hôte, ou si le nom de domaine complet est incorrect, ajoutez une entrée DNS inversée pour vous sont [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur un hôte Linux à votre serveur DNS.

## <a name="check-that-your-krb5-configuration-is-correct"></a>Vérifiez que votre configuration KRB5 est correcte

Vérifiez que votre `/etc/krb5.conf` est correctement configuré. Pour la plupart des fournisseurs d’Active Directory par des tiers, cette configuration est effectuée automatiquement. Toutefois, vérifiez `/etc/krb5.conf` pour les valeurs suivantes empêcher les problèmes futurs :

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

## <a name="next-steps"></a>Étapes suivantes

Cet article explique comment configurer un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur un ordinateur hôte de Linux avec l’authentification Active Directory lors de l’utilisation de fournisseurs d’Active Directory par des tiers. Pour terminer la configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur Linux pour prendre en charge les comptes Active Directory, suivez les instructions de [l’authentification d’utilisation d’Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md).

> [!div class="nextstepaction"]
> [Utiliser l’authentification Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md)

> [!NOTE]
>
> Vous pouvez ignorer la **hôte Join de SQL Server au domaine Active Directory** section [l’authentification d’utilisation d’Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md) comme vous venez de faire que dans ce didacticiel.
