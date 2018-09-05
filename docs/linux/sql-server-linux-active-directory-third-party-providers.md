---
title: Utiliser des fournisseurs d’Active Directory tiers avec SQL Server sur Linux | Microsoft Docs
description: Ce didacticiel fournit les étapes de configuration pour l’authentification Active Directory avec des fournisseurs tiers
author: dylan-MSFT
ms.date: 07/25/2018
ms.author: dygray
manager: mikehab
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
helpviewer_keywords:
- Linux, AD authentication
ms.openlocfilehash: 288f46a2084166a1b7164ff8f0c0ef82b81fb16b
ms.sourcegitcommit: ca5430ff8e3f20b5571d092c81b1fb4c950ee285
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43381497"
---
# <a name="use-third-party-active-directory-providers-with-sql-server-on-linux"></a>Utiliser des fournisseurs d’Active Directory tiers avec SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article explique comment configurer un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur l’ordinateur hôte de Linux avec l’authentification Active Directory lors de l’utilisation des AD fournisseurs tiers, tel que [PowerBroker identité Services (pbi)](https://www.beyondtrust.com/), [Vintela Authentication Services (VAS)](https://www.oneidentity.com/products/authentication-services/), et [Centrify](https://www.centrify.com/). Ce guide comprend les étapes permettant de vérifier votre configuration AD, et il n’est pas destinée à vous aiguillent sur la façon de joindre un ordinateur à un domaine. Pour obtenir des instructions détaillées sur la jonction un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] hôte à un domaine à l’aide du domaine Kerberos et SSSD, consultez [l’authentification d’utilisation d’Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md).

## <a name="prerequisites"></a>Prérequis

Avant de configurer l’authentification Active Directory, vous devez configurer un contrôleur de domaine Active Directory (Windows) sur votre réseau et la jointure votre [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur un hôte Linux à un domaine AD. Vous pouvez utiliser [pbi](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/), ou [Centrify](https://www.centrify.com/).

> [!NOTE]
>
>Ce didacticiel utilise « contoso.com » et « CONTOSO.COM » en tant qu’exemples de noms de domaine et le domaine respectivement. Il utilise également « DC1. « CONTOSO.COM » comme exemple de nom de domaine complet du contrôleur de domaine. Vous devez remplacer ces par vos propres valeurs.

## <a name="check-connection-to-domain-controller"></a>Vérifiez la connexion au contrôleur de domaine

Vérifiez que vous pouvez contacter le contrôleur de domaine avec le nom court et qualifié complet du domaine.

   ```bash
   ping contoso

   ping contoso.com
   ```

   Si une de ces échoue, mettez à jour votre liste de recherche du domaine.

   - **Ubuntu**:

     Modifier la `/etc/network/interfaces` de fichiers afin que votre domaine Active Directory est dans la liste de recherche du domaine : 

     ```/etc/network/interfaces
     <...>
     # The primary network interface
     auto eth0
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

     Maintenant vérifier que votre `/etc/resolv.conf` fichier contient une ligne comme dans l’exemple suivant :  

     ```/etc/resolv.conf
     search contoso.com com  
     nameserver **<AD domain controller IP address>**
     ```

   - **RHEL**:

     Modifier le `/etc/sysconfig/network-scripts/ifcfg-eth0` fichier (ou autres config interface fichier selon le cas) afin que votre domaine Active Directory est dans la liste de recherche du domaine :

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

   Si vous ne pouvez pas toujours tester le contrôleur de domaine, recherchez le nom de domaine complet (par exemple, DC1. CONTOSO.COM) et l’adresse IP du contrôleur de domaine et ajoutez l’entrée suivante à `/etc/hosts`

   ```/etc/hosts
   **<IP address>** DC1.CONTOSO.COM CONTOSO.COM CONTOSO
   ```

   - **SLES**:

     Modifier la `/etc/sysconfig/network/config` de fichiers afin que votre contrôleur de domaine AD adresse IP sera utilisé pour les requêtes DNS et votre domaine Active Directory est dans la liste de recherche du domaine :

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

## <a name="check-reverse-dns-is-properly-configured"></a>Vérifiez que DNS inverse est correctement configuré.

La commande suivante doit retourner le nom de domaine complet de l’hôte qui exécute SQL Server (par exemple) « SqlHost.contoso.com »).

   ```bash
   host **<IP address of SQL Server host>**
   # **<reversed IP address>**.in-addr.arpa domain name pointerSqlHost.contoso.com.
   ```

   Si cela ne retourne pas de nom de domaine complet de votre hôte, ou si le nom de domaine complet est incorrecte, ajoutez une entrée DNS inversée pour votre [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur un hôte Linux à votre serveur DNS.

## <a name="check-your-krb5-configuration-is-correct"></a>Vérifiez que votre configuration KRB5 est correcte

Vérifiez votre `/etc/krb5.conf` est correctement configuré. Pour la plupart des fournisseurs AD tiers, cela se fait automatiquement. Toutefois, vérifiez `/etc/krb5.conf` pour les valeurs suivantes empêcher les problèmes futurs :

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

Dans cet article, nous avons vu comment configurer un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur l’ordinateur hôte de Linux avec l’authentification Active Directory lors de l’utilisation des AD fournisseurs tiers. Pour terminer la configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur Linux pour prendre en charge les comptes Active Directory, suivez les instructions de [l’authentification d’utilisation d’Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md).

> [!div class="nextstepaction"]
> [Utiliser l’authentification Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md)

> [!NOTE]
>
> Vous pouvez ignorer la section « Hôte de jointure SQL Server au domaine AD » dans [l’authentification d’utilisation d’Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md) que vous venez d’apprendre que dans ce didacticiel.