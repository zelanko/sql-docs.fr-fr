---
title: OLTP en mémoire (optimisation en mémoire) | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- In-Memory OLTP
- memory-optimized tables
ms.assetid: e1d03d74-2572-4a55-afd6-7edf0bc28bdb
caps.latest.revision: 98
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a1df515a5a88c94e52d376394905a819d361281
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316199"
---
# <a name="in-memory-oltp-in-memory-optimization"></a>OLTP en mémoire (optimisation en mémoire)
  Nouveauté de [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)], l' [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] peut améliorer significativement les performances d'application de base de données OLTP. L'[!INCLUDE[hek_2](../../../includes/hek-2-md.md)] est un moteur de base de données optimisé en mémoire intégré au moteur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], qui est optimisé pour OLTP.  
  
|||  
|-|-|  
|![Machine virtuelle](../../master-data-services/media/azure-virtual-machine.png "Machine virtuelle Azure")|Voulez-vous essayer SQL Server 2016 ? Inscrivez-vous à Microsoft Azure, puis cliquez **[ici](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)** pour mettre en place une machine virtuelle sur laquelle SQL Server 2016 est déjà installé. Vous pouvez supprimer la machine virtuelle lorsque vous avez terminé.|  
  
 Pour utiliser l' [!INCLUDE[hek_2](../../../includes/hek-2-md.md)], vous définissez une table très sollicitée comme étant optimisée en mémoire. Les tables optimisées en mémoire sont transactionnelles, durables et accessibles via [!INCLUDE[tsql](../../../includes/tsql-md.md)] de la même manière que les tables sur disque. Une requête peut faire référence à des tables optimisées en mémoire et des tables sur disque. Une transaction peut mettre à jour des données dans des tables optimisées en mémoire et des tables sur disque. Les procédures stockées qui font référence uniquement aux tables optimisées en mémoire peuvent être compilées de façon native en code machine pour améliorer les performances. Le moteur de l' [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] est conçu pour prendre en charge des accès concurrentiels très nombreux de transactions de type OLTP qui sont gérés par une couche intermédiaire mise à l'échelle. Pour cela, il utilise des structures de données sans verrou et un contrôle d'accès concurrentiel optimiste et multiversion. Le résultat est une latence prévisible inférieure à une milliseconde et un débit élevé avec une mise à l'échelle linéaire pour les transactions de base de données. Le gain réel au niveau des performances dépend de plusieurs facteurs, mais une amélioration des performances de 5 à 20 fois est souvent obtenue.  
  
 Le tableau suivant résume les modèles de charge qui bénéficient le plus de l'utilisation de l' [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]:  
  
|Scénario d'implémentation|Scénario d'implémentation|Avantages de [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]|  
|-----------------------------|-----------------------------|-------------------------------------|  
|Taux d'insertion de données élevé à partir de plusieurs connexions simultanées.|Stockage append-only principal.<br /><br /> Impossible de rester au niveau de la charge de travail d'insertion.|Supprimer la contention.<br /><br /> Réduire la journalisation.|  
|Performances de lecture et mise à l'échelle avec des insertions et des mises à jour par lot périodiques.|Opérations de lecture haute performance, surtout quand chaque demande du serveur effectue plusieurs opérations de lecture.<br /><br /> Impossible de répondre aux besoins de mise à l'échelle.|Supprimer la contention quand de nouvelles données arrivent.<br /><br /> Diminuer la latence d'extraction des données.<br /><br /> Réduire le temps d'exécution du code.|  
|Traitement de logique métier intensif sur le serveur de base de données.|Insérer, mettre à jour et supprimer la charge de travail.<br /><br /> Calculs intensifs au sein des procédures stockées.<br /><br /> Contention de lecture/écriture.|Supprimer la contention.<br /><br /> Réduire la durée d'exécution du code pour une latence et un débit améliorés.|  
|Faible latence.|Transactions d'entreprise à faible latence, ce que les solutions de base de données traditionnelles ne proposent pas.|Supprimer la contention.<br /><br /> Réduire le temps d'exécution du code.<br /><br /> Exécution du code à faible latence.<br /><br /> Récupération efficace des données.|  
|Gestion de l'état de session.|Insertion, mise à jour et recherches de point fréquentes.<br /><br /> Charge élevée de nombreux serveurs web sans état.|Supprimer la contention.<br /><br /> Récupération efficace des données.<br /><br /> Réduction ou suppression des E/S facultative, lors de l'utilisation de tables non durables|  
  
 Pour plus d'informations sur des scénarios pour lesquels l' [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] donnera les meilleurs gains de performances, consultez [OLTP en mémoire – Modèles de charge de travail courants et considérations relatives à la migration](http://msdn.microsoft.com/library/dn673538.aspx).  
  
 L'[!INCLUDE[hek_2](../../../includes/hek-2-md.md)] améliorera davantage les performances dans l'OLTP avec des transactions à exécution courte.  
  
 Les modèles de programmation optimisés par l' [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] incluent les scénarios de concurrence, les recherches de point, les charges de travail avec de nombreuses insertions et mises à jour, et la logique métier dans les procédures stockées.  
  
 L'intégration avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] signifie que vous pouvez utiliser à la fois les tables optimisées en mémoire et les tables sur disques dans la même base de données, et interroger les deux types de tables.  
  
 Dans [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] , il existe des limitations concernant la surface d'exposition [!INCLUDE[tsql](../../../includes/tsql-md.md)] prise en charge pour l' [!INCLUDE[hek_2](../../../includes/hek-2-md.md)].  
  
 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] offre des gains significatifs sur les performances et l’évolutivité à l’aide de :  
  
-   Algorithmes qui sont optimisés pour accéder aux données résidantes en mémoire.  
  
-   Contrôle d'accès concurrentiel optimiste qui élimine les verrous logiques.  
  
-   Des objets sans verrou qui suppriment tous les verrous physiques (internes et externes). Les threads qui exécutent le travail transactionnel n'utilisent pas de verrous ou de verrous internes pour le contrôle d'accès concurrentiel.  
  
-   Les procédures stockées compilées nativement, qui ont des performances supérieures aux procédures stockées interprétées, lors de l'accès à une table optimisée en mémoire.  
  
> [!IMPORTANT]  
>  Certaines modifications de la syntaxe des tables et des procédures stockées sont nécessaires pour utiliser l' [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]. Pour plus d’informations, consultez [Migration vers OLTP en mémoire](migrating-to-in-memory-oltp.md). Avant de migrer une table sur disque vers une table mémoire optimisée, consultez [Déterminer si un tableau ou une procédure stockée doit être déplacée vers l’OLTP en mémoire](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) pour voir les tables et les procédures stockées qui tireront parti d’[!INCLUDE[hek_2](../../../includes/hek-2-md.md)].  
  
## <a name="in-this-section"></a>Contenu de cette section  
 Cette section fournit des informations sur les concepts suivants :  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Conditions requises pour l’utilisation des tables optimisées en mémoire](memory-optimized-tables.md)|Décrit les configurations matérielle et logicielle requises et fournit des instructions pour l'utilisation des tables optimisées en mémoire.|  
|[Utilisation de l’OLTP en mémoire dans un environnement de machine virtuelle](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)|Décrit l'utilisation de l' [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] dans un environnement virtualisé.|  
|[Exemples de code OLTP en mémoire](in-memory-oltp-code-samples.md)|Contient des exemples de code qui montrent comment créer et utiliser une table optimisée en mémoire.|  
|[Tables optimisées en mémoire](memory-optimized-tables.md)|Présente les tables optimisées en mémoire.|  
|[Variables de table mémoire optimisée](../../database-engine/memory-optimized-table-variables.md)|L'exemple de code illustre comment utiliser une variable de table optimisée en mémoire plutôt qu'une variable de table traditionnelle pour réduire l'utilisation de tempdb.|  
|[Index sur des tables optimisées en mémoire](../../database-engine/indexes-on-memory-optimized-tables.md)|Présente les index optimisés en mémoire.|  
|[Procédures stockées compilées en mode natif](natively-compiled-stored-procedures.md)|Présente les procédures stockées compilées en mode natif.|  
|[Gestion de la mémoire pour l’OLTP en mémoire](../../database-engine/managing-memory-for-in-memory-oltp.md)|Comprendre et gérer l'utilisation de la mémoire sur votre système.|  
|[Création et gestion du stockage des objets mémoire optimisés](creating-and-managing-storage-for-memory-optimized-objects.md)|Traite des fichiers de données et delta, qui stockent les informations sur les transactions dans les tables optimisées en mémoire.|  
|[Sauvegarder, restaurer et récupérer des tables optimisées en mémoire](restore-and-recovery-of-memory-optimized-tables.md)|Décrit la sauvegarde, la restauration et la récupération des tables optimisées en mémoire.|  
|[Prise en charge d’OLTP en mémoire par Transact-SQL](transact-sql-support-for-in-memory-oltp.md)|Décrit la prise en charge [!INCLUDE[tsql](../../../includes/tsql-md.md)] pour l' [!INCLUDE[hek_2](../../../includes/hek-2-md.md)].|  
|[Prise en charge de la haute disponibilité pour les bases de données OLTP en mémoire](high-availability-support-for-in-memory-oltp-databases.md)|Décrit les groupes de disponibilité et le clustering de basculement dans l' [!INCLUDE[hek_2](../../../includes/hek-2-md.md)].|  
|[Prise en charge d'OLTP en mémoire par SQL Server](sql-server-support-for-in-memory-oltp.md)|Répertorie les nouveautés et les mises à jour en matière de syntaxe et de fonctionnalités prenant en charge les tables optimisées en mémoire.|  
|[Migration vers OLTP en mémoire](migrating-to-in-memory-oltp.md)|Explique comment migrer les tables sur disque vers des tables optimisées en mémoire.|  
  
 Des informations supplémentaires sur l' [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] sont disponibles dans :  
  
-   [Guide du produit Server® 2014 Microsoft® SQL](http://www.microsoft.com/download/confirmation.aspx?id=39269)  
  
-   [Blog OLTP en mémoire](http://go.microsoft.com/fwlink/?LinkId=311696)  
  
-   [OLTP en mémoire – Modèles de charge de travail courants et considérations relatives à la migration](http://msdn.microsoft.com/library/dn673538.aspx)  
  
-   [Vue d’ensemble SQL Server In-Memory OLTP Internals](http://msdn.microsoft.com/library/dn720242.aspx)  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de base de données](../database-features.md)  
  
  
