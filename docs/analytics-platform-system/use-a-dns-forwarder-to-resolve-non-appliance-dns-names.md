---
title: "Un redirecteur DNS permet de résoudre les noms DNS de l’Appliance Non (APS)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 123d8a83-b7fd-4dc9-90d4-fa01af2d629d
caps.latest.revision: "21"
ms.openlocfilehash: 6538ec32f141592b6cf21a325b74f3e451e73092
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="use-a-dns-forwarder-to-resolve-non-appliance-dns-names"></a>Un redirecteur DNS permet de résoudre les noms DNS de l’autre que l’Appliance
Un redirecteur DNS peut être configuré sur les nœuds des Services de domaine Active Directory (***appliance_domain*-AD01** et  ***appliance_domain*-AD02**) de votre matériel de système de plateforme Analytique pour autoriser les scripts et les applications logicielles pour accéder aux serveurs externes.  
  
## <a name="ResolveDNS"></a>Utilisation d’un redirecteur DNS  
Le matériel de système de plateforme Analytique est configuré pour empêcher la résolution de noms DNS des serveurs qui ne sont pas dans l’application. Certains processus, tels que Windows Software Update Services (WSUS) devez accéder aux serveurs en dehors de l’application. Pour prendre en charge ce scénario d’utilisation du système de plateforme Analytique DNS peut être configuré pour prendre en charge d’un redirecteur de nom externe qui autorise les hôtes de système de plateforme Analytique et Machines virtuelles (VM) à utiliser des serveurs DNS externes pour résoudre les noms en dehors de l’application. Configuration personnalisée de suffixes DNS n'est pas pris en charge, ce qui signifie que vous devez utiliser des noms de domaine complet pour résoudre un nom non-serveur.  
  
**Création d’un redirecteur DNS avec l’interface utilisateur graphique de DNS**  
  
1.  Ouvrez une session sur le  ***appliance_domain*-AD01** nœud.  
  
2.  Ouvrez le Gestionnaire DNS (**dnsmgmt.msc**).  
  
3.  Cliquez sur le nom du serveur, puis cliquez sur **propriétés**.  
  
4.  Dans le **avancé** onglet, désélectionnez la **désactiver la récursivité (désactive également les redirecteurs)** option, puis cliquez sur **appliquer**.)  
  
5.  Cliquez sur le **redirecteurs** onglet, puis cliquez sur **modifier**.  
  
6.  Entrez l’adresse IP pour le serveur DNS externe qui fournit la résolution de noms. Les machines virtuelles et les serveurs (hôtes) dans l’application seront connecte aux serveurs externes à l’aide de noms de domaine qualifié complet.  
  
7.  Répétez les étapes 1 à 6 sur le  ***appliance_domain*-AD02** nœud  
  
**Création d’un redirecteur DNS à l’aide de Windows PowerShell**  
  
1.  Ouvrez une session sur le  ***appliance_domain*-AD01**nœud.  
  
2.  Exécutez le script Windows PowerShell suivant à partir de la  ***appliance_domain*-AD01** nœud. Avant d’exécuter le script Windows PowerShell, remplacez les adresses IP avec les adresses IP des serveurs DNS non appliance.  
  
    ```  
    $DNS=Get-WmiObject -class "MicrosoftDNS_Server"  -Namespace "root\microsoftdns"  
    $DNS.Forwarders = ("xxx.xxx.xxx.xxx", "xxx.xxx.xxx.xxx")  
    $DNS.put()  
    ```  
  
3.  Exécuter la même commande sur le  ***appliance_domain*-AD02** nœud.  
  
## <a name="configuring-dns-resolution-for-wsus"></a>Configuration de la résolution DNS pour WSUS  
SQL Server 2012 PDW fournit des fonctionnalités de mise à jour corrective et de maintenance intégrée. SQL Server PDW utilise Microsoft Update et autres technologies de maintenance de Microsoft. Pour activer les mises à jour de que l’application doit être en mesure de vous connecter à un référentiel WSUS d’entreprise ou dans le référentiel WSUS public de Microsoft.  
  
Pour les clients que vous choisissez de configurer l’application pour rechercher des mises à jour sur le référentiel WSUS public de Microsoft, les instructions suivantes définissent les détails de la configuration appropriée sur l’appareil.  
  
> [!NOTE]  
> L’administrateur réseau de client doit fournir l’adresse IP d’un serveur DNS d’entreprise qui peut résoudre les noms à **Microsoft.com**.  
  
1.  À l’aide du Bureau à distance, ouvrez une session sur VMM VM (<fabric domain>- VMM) à l’aide du compte administrateur de domaine de l’ensemble fibre optique.  
  
2.  Ouvrez le panneau de configuration, cliquez sur **réseau et Internet**, puis cliquez sur **Centre réseau et partage**.  
  
3.  Dans la liste des connexions, cliquez sur **VMSEthernet**, puis cliquez sur **propriétés**.  
  
4.  Sélectionnez **Internet Protocol Version 4 (TCP/IPv4)**, puis cliquez sur **propriétés**.  
  
5.  Dans le **serveur DNS auxiliaire** box, indiquez l’adresse IP fournie par l’administrateur de réseau client.  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
