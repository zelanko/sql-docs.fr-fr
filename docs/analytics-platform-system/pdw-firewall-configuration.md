---
title: Configuration du pare-feu PDW - Analytique Platform System | Microsoft Docs
description: La page pare-feu du Gestionnaire de Configuration PDW SQL Server vous permet d’activer ou désactiver les règles de pare-feu qui autorisent ou empêchent l’accès à des ports spécifiques sur l’appliance Analytique Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 6f650aac34e3a5299cabae500a8ee73250c3974d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960417"
---
# <a name="parallel-data-warehouse-firewall-configuration-in-analytics-platform-system"></a>Configuration du pare-feu entrepôt de données parallèle d’Analytique Platform System

Le **pare-feu** page du Gestionnaire de Configuration PDW SQL Server vous permet d’activer ou désactiver les règles de pare-feu qui autorisent ou empêchent l’accès à des ports spécifiques sur l’appliance Analytique Platform System.  
  
## <a name="to-manage-ports-and-firewall-rules-for-appliance-nodes"></a>Pour gérer des ports et de règles de pare-feu pour les nœuds d’appliance  
  
1.  Lancez le Gestionnaire de Configuration. Pour plus d’informations, consultez [lancer le Gestionnaire de Configuration &#40;Analytique Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Dans le volet gauche du Gestionnaire de Configuration, développez **topologie de l’entrepôt de données parallèle**, puis cliquez sur **pare-feu**.  
  
3.  Recherchez la règle de pare-feu ou un port pour mettre à jour dans la liste des configurations, puis activez ou désactivez la case en regard de cet élément. Seules les options configurables par l’administrateur SQL Server PDW sont affichées dans cette liste, y compris l’ouverture et fermeture des ports sur les nœuds.  
  
4.  Cliquez sur **appliquer** pour enregistrer vos modifications.  
  
![Pare-feu de PDW des appliances DWConfig](./media/pdw-firewall-configuration/SQL_Server_PDW_DWConfig_ApplPDWFirewall.png "SQL_Server_PDW_DWConfig_ApplPDWFirewall")  
  
## <a name="external-ports"></a>Ports externes  
Les ports suivants sont ouverts pour les connexions client provenant en dehors de PDW.  
  
|Objectif|N° de port|Nœuds|  
|-----------|-----------|---------|  
|Accès Client SQL pour PDW (TDS)|17001|LISTE CTL|  
|Accès au Client de chargeur (dwloader & SSIS)|8001|LISTE CTL|  
|Accès Bureau à distance|3389|CTL, CMP|  
|SSIS BinaryLoaderDataChannel|16551|LISTE CTL|  
|dwloader BinaryLoaderDataChannel|16551|CMP|  
|SSL chiffrée des connexions (pour les communications internes, pour accéder à la Console d’administration)|443|Tous les nœuds|  
|Flux de contrôle SQL Server PDW charge - informations d’identification Windows|8002|LISTE CTL|  
|_Kerberos|88|AD01 et AD02,|  
|_ldap|389|AD01 et AD02|  
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="internal-ports"></a>Ports internes  
Les ports suivants sont utilisés par PDW pour la communication interne, mais ne sont pas ouverts pour les connexions en provenance d’en dehors de l’appliance PDW.  
  
|Objectif|N° de port|Nœuds|  
|-----------|-----------|---------|  
|Trafic du canal de contrôle DMS|16450|CTL, CMP|  
|Trafic du canal de données DMS|16550|CTL, CMP|  
|Diagnostics internes|16650|CTL, CMP|  
|État de basculement (DMS)|15000|CTL, CMP|  
|État de basculement (moteur)|15001|CMP|  
|Plage de ports dynamiques (éphémère)|20000-65535|CTL, CMP|  
|Plages de ports SQL Server (TDS)|1433, 1500-1508|CTL, CMP|  
| &nbsp; | &nbsp; | &nbsp; |
  
> [!NOTE]  
> Création de tables externes ou des sources de données externe utilise le port TCP 8020 par défaut. Ces instructions peuvent être configurées pour utiliser les autres ports à la place. Le port par défaut de Hortonworks JOB_TRACKER_LOCATION est 50300. L’intégration avec d’autres systèmes et les outils peut-être nécessiter des ports supplémentaires.  
  
<!-- MISSING LINKS ## See Also  
[HDInsight Firewall Configuration &#40;Analytics Platform System&#41;](hdinsight-firewall-configuration.md)
-->
  
