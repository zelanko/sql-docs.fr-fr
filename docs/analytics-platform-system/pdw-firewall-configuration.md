---
title: "Configuration du pare-feu PDW (système de plateforme Analytique)"
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
ms.assetid: 191f292d-16bc-4166-b855-158854ad062d
caps.latest.revision: "28"
ms.openlocfilehash: e74ffd88f0b2c10a6120c4411e4647c2fb84f249
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="pdw-firewall-configuration"></a>Configuration du pare-feu PDW
Le **pare-feu** page du Gestionnaire de Configuration PDW SQL Server vous permet d’activer ou désactiver des règles de pare-feu qui autorisent ou empêchent l’accès à des ports spécifiques sur le matériel de système de plateforme Analytique.  
  
## <a name="to-manage-ports-and-firewall-rules-for-appliance-nodes"></a>Pour gérer les ports et les règles de pare-feu pour les nœuds de l’équipement  
  
1.  Lancez le Gestionnaire de Configuration. Pour plus d’informations, consultez [lance le Gestionnaire de Configuration &#40; Système de plateforme Analytique &#41; ](launch-the-configuration-manager.md).  
  
2.  Dans le volet gauche du Gestionnaire de Configuration, développez **topologie de l’entrepôt de données parallèle**, puis cliquez sur **pare-feu**.  
  
3.  Recherchez la règle de port ou un pare-feu pour mettre à jour dans la liste des configurations, puis activez ou désactivez la case en regard de cet élément. Seules les options configurables par l’administrateur SQL Server PDW sont indiquées dans cette liste, y compris l’ouverture et de fermeture des ports sur les nœuds.  
  
4.  Cliquez sur **appliquer** pour enregistrer vos modifications.  
  
![Pare-feu de PDW des appliances DWConfig](./media/pdw-firewall-configuration/SQL_Server_PDW_DWConfig_ApplPDWFirewall.png "SQL_Server_PDW_DWConfig_ApplPDWFirewall")  
  
## <a name="external-ports"></a>Ports externes  
Les ports suivants sont ouverts pour les connexions client provenant en dehors de PDW.  
  
|Fonction|Port #|Nœuds|  
|-----------|-----------|---------|  
|Accès Client SQL pour PDW (TDS)|17001|LISTE CTL|  
|Accès au Client de chargeur (dwloader & SSIS)|8001|LISTE CTL|  
|Accès Bureau à distance|3389|CTL, CMP|  
|SSIS BinaryLoaderDataChannel|16551|LISTE CTL|  
|dwloader BinaryLoaderDataChannel|16551|CMP|  
|SSL chiffrée connexions (pour les communications internes, pour accéder à la Console d’administration et d’accéder aux services de cluster HDInsight)|443|Tous les nœuds|  
|Flux de contrôle SQL Server PDW charge - informations d’identification Windows|8002|LISTE CTL|  
|_Kerberos|88|AD01 et AD02,|  
|_ldap|389|AD01 et AD02|  
  
## <a name="internal-ports"></a>Ports internes  
Les ports suivants sont utilisés par PDW pour la communication interne, mais ne sont pas ouverts pour les connexions en provenance d’en dehors de l’appliance PDW.  
  
|Fonction|Port #|Nœuds|  
|-----------|-----------|---------|  
|Trafic du canal de contrôle DMS|16450|CTL, CMP|  
|Trafic du canal de données DMS|16550|CTL, CMP|  
|Diagnostics internes|16650|CTL, CMP|  
|État de basculement (DMS)|15000|CTL, CMP|  
|État de basculement (moteur)|15001|CMP|  
|Plage de ports dynamiques (éphémère)|20000-65535|CTL, CMP|  
|Plages de ports SQL Server (TDS)|1433, 1500-1508|CTL, CMP|  
  
> [!NOTE]  
> Création de tables externes ou les sources de données externes utilise le port TCP 8020 par défaut. Ces instructions peuvent être configurées pour utiliser les autres ports à la place. Le port par défaut Hortonworks JOB_TRACKER_LOCATION est 50300. Intégration avec d’autres systèmes et les outils peut-être nécessiter des ports supplémentaires.  
  
<!-- MISSING LINKS ## See Also  
[HDInsight Firewall Configuration &#40;Analytics Platform System&#41;](hdinsight-firewall-configuration.md)  -->  
  
