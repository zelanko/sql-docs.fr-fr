---
title: Utiliser un redirecteur DNS d’Analytique Platform System | Microsoft Docs »
description: Utiliser un redirecteur DNS pour résoudre les noms DNS non-appliance d’Analytique Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 645e2603af6d0447aae22bc7c29b5413501b722f
ms.sourcegitcommit: fc6a6eedcea2d98c93e33d39c1cecd99fbc9a155
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49168891"
---
# <a name="use-a-dns-forwarder-to-resolve-non-appliance-dns-names-in-analytics-platform-system"></a>Utiliser un redirecteur DNS pour résoudre les noms DNS de Non-Appliance d’Analytique Platform System
Un redirecteur DNS peut être configuré sur les nœuds de Services de domaine Active Directory (**_appliance\_domaine_-AD01** et  **_appliance\_ domaine_-AD02**) de votre appliance Analytique Platform System pour autoriser les scripts et les applications logicielles pour accéder aux serveurs externes.  
  
## <a name="ResolveDNS"></a>À l’aide d’un redirecteur DNS  
L’appliance Analytique Platform System est configuré pour empêcher la résolution de noms DNS des serveurs qui ne sont pas dans l’appliance. Certains processus, tels que Windows Software Update Services (WSUS), devez accéder aux serveurs en dehors de l’appliance. Pour prendre en charge ce scénario d’utilisation du système de plateforme Analytique DNS peut être configuré pour prendre en charge d’un redirecteur de nom externe qui autorise les hôtes Analytique Platform System et Machines virtuelles (VM) à utiliser les serveurs DNS externes pour résoudre les noms en dehors de l’appliance. Configuration personnalisée de suffixes DNS n’est pas possible, ce qui signifie que vous devez utiliser des noms de domaine complet pour résoudre un nom de serveur non-appliance.  
  
**Pour créer un redirecteur DNS avec l’interface utilisateur graphique de DNS**  
  
1.  Ouvrez une session sur le  **_appliance\_domaine_-AD01** nœud.  
  
2.  Ouvrez le Gestionnaire DNS (**dnsmgmt.msc**).  
  
3.  Cliquez sur le nom du serveur, puis **propriétés**.  
  
4.  Dans le **avancé** onglet, désélectionnez le **désactiver la récursivité (désactive également les redirecteurs)** option, puis cliquez sur **appliquer**.)  
  
5.  Cliquez sur le **redirecteurs** onglet, puis cliquez sur **modifier**.  
  
6.  Entrez l’adresse IP pour le serveur DNS externe qui fournit la résolution de noms. Les machines virtuelles et les serveurs (hôtes) dans l’appliance seront connecte aux serveurs externes en utilisant des noms de domaine complet.  
  
7.  Répétez les étapes 1 à 6 sur le  **_appliance\_domaine_-AD02** nœud  
  
**Création d’un redirecteur DNS à l’aide de Windows PowerShell**  
  
1.  Ouvrez une session sur le  **_appliance\_domaine_-AD01**nœud.  
  
2.  Exécutez le script Windows PowerShell suivant à partir de la  **_appliance\_domaine_-AD01** nœud. Avant d’exécuter le script Windows PowerShell, remplacez les adresses IP avec les adresses IP des serveurs DNS non-appliance.  
  
    ```  
    $DNS=Get-WmiObject -class "MicrosoftDNS_Server"  -Namespace "root\microsoftdns"  
    $DNS.Forwarders = ("xxx.xxx.xxx.xxx", "xxx.xxx.xxx.xxx")  
    $DNS.put()  
    ```  
  
3.  Exécuter la même commande sur le  **_appliance\_domaine_-AD02** nœud.  
  
## <a name="configuring-dns-resolution-for-wsus"></a>Configuration de la résolution DNS pour WSUS  
SQL Server 2012 PDW fournit des fonctionnalités de mise à jour corrective et de maintenance intégrée. SQL Server PDW utilise Microsoft Update et autres technologies de maintenance de Microsoft. Pour activer les mises à jour de que l’appliance doit être en mesure de vous connecter à un référentiel d’entreprise de WSUS ou vers le dépôt WSUS public de Microsoft.  
  
Pour les clients que vous choisissez de configurer l’appliance pour rechercher des mises à jour sur le référentiel WSUS public de Microsoft, les instructions suivantes définissent les détails de la configuration appropriée sur l’appliance.  
  
> [!NOTE]  
> L’administrateur de réseau de client doit fournir l’adresse IP d’un serveur DNS d’entreprise qui peut résoudre les noms à **Microsoft.com**.  
  
1.  À l’aide du Bureau à distance, ouvrez une session sur VMM VM (<fabric domain>- VMM) à l’aide de compte d’administrateur de domaine fabric.  
  
2.  Ouvrez le panneau de configuration, cliquez sur **réseau et Internet**, puis cliquez sur **Centre réseau et partage**.  
  
3.  Dans la liste des connexions, cliquez sur **VMSEthernet**, puis cliquez sur **propriétés**.  
  
4.  Sélectionnez **Internet Protocol Version 4 (TCP/IPv4)**, puis cliquez sur **propriétés**.  
  
5.  Dans le **serveur DNS auxiliaire** zone, ajoutez l’adresse IP fournie par l’administrateur de réseau client.  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
