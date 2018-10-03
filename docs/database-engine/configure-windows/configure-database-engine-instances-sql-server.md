---
title: Configurer des instances du moteur de base de données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 84e36fcb-2c78-48e8-8e4b-bf784a3ee557
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8a233814c86779b3c8fca67e6fb79c9f183a91d7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670877"
---
# <a name="configure-database-engine-instances-sql-server"></a>Configurer des instances du moteur de base de données (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Chaque instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] doit être configurée pour répondre aux exigences en matière de performances et de disponibilité définies pour les bases de données hébergées par l'instance. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] comprend des options de configuration qui contrôlent des comportements (tels que l'utilisation des ressources) et la disponibilité de fonctionnalités (telles que l'audit ou la récursivité des déclencheurs).  
  
## <a name="instance-configuration"></a>Configuration de l'instance  
 Lorsqu'une base de données est déployée dans l'environnement de production, il existe souvent un contrat de niveau de service (SLA) qui définit des zones telles que les niveaux de performances requis de la base de données et le niveau de disponibilité requis de la base de données. Les termes du contrat de niveau de service définissent généralement les exigences de configuration pour l'instance.  
  
 Une instance est généralement configurée dès son installation terminée. La configuration initiale est généralement déterminée par les exigences du contrat de niveau de service concernant les types de bases de données dont le déploiement sur l'instance est planifié. Une fois les bases de données déployées, les administrateurs de base de données surveillent les performances de l'instance et règlent les paramètres de configuration en conséquence si les métriques de performances indiquent que l'instance ne répond pas aux spécifications du contrat de niveau de service.  
  
## <a name="configuration-tasks"></a>Tâches de configuration  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Décrit les différentes options de configuration de l'instance et explique comment afficher ou modifier ces options.|[Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)|  
|Explique comment afficher et configurer les emplacements par défaut des nouveaux fichiers de données et fichiers journaux de l'instance.|[Afficher ou modifier les emplacements par défaut des fichiers de données et des fichiers journaux &#40;SQL Server Management Studio&#41;](../../database-engine/configure-windows/view-or-change-the-default-locations-for-data-and-log-files.md)|  
|Explique comment configurer SQL Server pour utiliser soft-NUMA.|[Soft-NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md)|  
|Explique comment mapper un port TCP/IP à une affinité de nœud NUMA.|[Mapper les ports TCP/IP aux nœuds NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/map-tcp-ip-ports-to-numa-nodes-sql-server.md)|  
|Explique comment activer la stratégie Verrouiller les pages en mémoire de Windows. Cette stratégie détermine quels comptes peuvent utiliser un processus destiné à conserver les données en mémoire physique pour éviter leur pagination en mémoire virtuelle sur le disque.|[Activer l’option Lock Pages in Memory &#40;Windows&#41;](../../database-engine/configure-windows/enable-the-lock-pages-in-memory-option-windows.md)|  
  
## <a name="see-also"></a> Voir aussi  
 [Instances du moteur de base de données &#40;SQL Server&#41;](../../database-engine/configure-windows/database-engine-instances-sql-server.md)  
  
  
