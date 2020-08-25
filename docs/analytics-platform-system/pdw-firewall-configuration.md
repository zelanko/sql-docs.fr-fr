---
title: Configuration du pare-feu PDW
description: La page pare-feu de la SQL Server PDW Configuration Manager vous permet d’activer ou de désactiver les règles de pare-feu qui autorisent ou empêchent l’accès à des ports spécifiques sur l’appliance Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 4ed739ce12170aa6d0ab79b996de0075cd6723ee
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "74400886"
---
# <a name="parallel-data-warehouse-firewall-configuration-in-analytics-platform-system"></a>Configuration du pare-feu Data Warehouse parallèle dans Analytics Platform System

La page **pare-feu** de la SQL Server PDW Configuration Manager vous permet d’activer ou de désactiver les règles de pare-feu qui autorisent ou empêchent l’accès à des ports spécifiques sur l’appliance Analytics Platform System.  
  
## <a name="to-manage-ports-and-firewall-rules-for-appliance-nodes"></a>Pour gérer les ports et les règles de pare-feu pour les nœuds d’appliance  
  
1.  Lancez le Configuration Manager. Pour plus d’informations, consultez [la page lancement du&#41;Configuration Manager &#40;Analytics Platform System ](launch-the-configuration-manager.md).  
  
2.  Dans le volet gauche de la Configuration Manager, développez **topologie de Data Warehouse parallèle**, puis cliquez sur **pare-feu**.  
  
3.  Localisez la règle de port ou de pare-feu à mettre à jour dans la liste Configuration, puis activez ou désactivez la case à cocher en regard de cet élément. SQL Server PDW seules les options configurables par l’administrateur sont affichées dans cette liste, y compris les ports d’ouverture et de fermeture sur les nœuds accessibles de l’extérieur.  
  
4.  Cliquez sur **appliquer** pour enregistrer vos modifications.  
  
![Pare-feu d'PDW des appliances DWConfig](./media/pdw-firewall-configuration/SQL_Server_PDW_DWConfig_ApplPDWFirewall.png "SQL_Server_PDW_DWConfig_ApplPDWFirewall")  
  
## <a name="external-ports"></a>Ports externes  
Les ports suivants sont ouverts pour les connexions clientes provenant de l’extérieur de PDW.  
  
|Fonction|Importer #|Nœuds|  
|-----------|-----------|---------|  
|Accès client SQL pour PDW (TDS)|17001|CONFIANCE|  
|Accès client du chargeur (dwloader & SSIS)|8001|CONFIANCE|  
|Accès au Bureau à distance|3389|CTL, CMP|  
|BinaryLoaderDataChannel SSIS|16551|CONFIANCE|  
|dwloader BinaryLoaderDataChannel|16551|CMP|  
|Connexions chiffrées SSL (pour les communications internes, pour accéder à la console d’administration)|443|Tous les nœuds|  
|SQL Server PDW le contrôle de charge-informations d’identification Windows|8002|CONFIANCE|  
|_Kerberos|88|AD01 et AD02,|  
|_ldap|389|AD01 et AD02|  
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="internal-ports"></a>Ports internes  
Les ports suivants sont utilisés par PDW pour la communication interne, mais ne sont pas ouverts pour les connexions provenant de l’extérieur de l’appliance PDW.  
  
|Fonction|Importer #|Nœuds|  
|-----------|-----------|---------|  
|Trafic du canal de contrôle DMS|16450|CTL, CMP|  
|Trafic du canal de données DMS|16550|CTL, CMP|  
|Diagnostics internes|16650|CTL, CMP|  
|État du basculement (DMS)|15000|CTL, CMP|  
|État du basculement (moteur)|15001|CMP|  
|Plage de ports dynamique (éphémère)|20000-65535|CTL, CMP|  
|SQL Server les plages de ports (TDS)|1433, 1500-1508|CTL, CMP|  
| &nbsp; | &nbsp; | &nbsp; |
  
> [!NOTE]  
> La création de tables externes ou de sources de données externes utilise le port TCP 8020 par défaut. Ces instructions peuvent être configurées pour utiliser d’autres ports à la place. Le port par défaut Hortonworks JOB_TRACKER_LOCATION est 50300. L’intégration à d’autres systèmes et outils peut nécessiter des ports supplémentaires.  
  
<!-- MISSING LINKS ## See Also  
[HDInsight Firewall Configuration &#40;Analytics Platform System&#41;](hdinsight-firewall-configuration.md)
-->
  
