---
title: Comportement du verrouillage
description: Découvrez comment le Data Warehouse parallèle utilise le verrouillage pour garantir l’intégrité des transactions et maintenir la cohérence des bases de données lorsque plusieurs utilisateurs accèdent aux données en même temps.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: f3ecf5cf783b707b75c90dfa70d502e3c81d28c3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401002"
---
# <a name="locking-behavior-in-parallel-data-warehouse"></a>Comportement de verrouillage en parallèle Data Warehouse
Découvrez comment le Data Warehouse parallèle utilise le verrouillage pour garantir l’intégrité des transactions et maintenir la cohérence des bases de données lorsque plusieurs utilisateurs accèdent aux données en même temps.  
  
## <a name="Basics"></a>Notions de base du verrouillage  
**Façons**  
  
SQL Server PDW prend en charge quatre modes de verrouillage :  
  
Exclusif  
Le verrou exclusif interdit l’écriture ou la lecture de l’objet verrouillé jusqu’à ce que la transaction qui maintient le verrou exclusif se termine. Aucun autre verrou de n’importe quel mode n’est autorisé tant que le verrou exclusif est en vigueur. Par exemple, DROP TABLE et CREATe DATABASE utilisent un verrou exclusif.  
  
Partagé  
Le verrou partagé interdit l’initiation d’un verrou exclusif sur l’objet affecté, mais autorise tous les autres modes de verrouillage. Par exemple, l’instruction SELECT initie un verrou partagé et, par conséquent, permet à plusieurs requêtes d’accéder simultanément aux données sélectionnées, mais empêche les mises à jour des enregistrements en cours de lecture, jusqu’à ce que l’instruction SELECT soit terminée.  
  
ExclusiveUpdate  
Le verrou ExclusiveUpdate interdit l’écriture dans l’objet verrouillé, mais autorise la lecture via le verrou partagé. Aucun autre verrou n’est autorisé tant que le verrou ExclusiveUpdate est en vigueur. Par exemple, BACKUP DATABASE et RESTORE DATABASE utilisent un verrou de mise à jour exclusif.  
  
SharedUpdate  
Le verrou SharedUpdate interdit les modes de verrouillage exclusif et ExclusiveUpdate, et autorise les modes de verrouillage partagé et SharedUpdate sur l’objet. SharedUpdate modifie un objet, mais ne restreint pas l’accès en lecture au cours de la modification. Par exemple, INSERT et UPDATE utilisent un verrou SharedUpdate.  
  
**Classes de ressources**  
  
Les verrous sont conservés sur les classes d’objets suivantes : base de données, schéma, objet (table, vue ou procédure), APPLICATION (utilisée en interne), EXTERNALDATASOURCE, EXTERNALFILEFORMAT et SCHEMARESOLUTION (verrou de niveau base de données pris lors de la création, de la modification ou suppression des objets de schéma ou des utilisateurs de base de données). Ces classes d’objets peuvent apparaître dans la colonne object_type de [sys. dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md).  
  
## <a name="Remarks"></a>Remarques d'ordre général  
Les verrous peuvent être appliqués aux bases de données, aux tables ou aux vues.  
  
SQL Server PDW n’implémente aucun niveau d’isolement configurable. Il prend en charge le niveau d’isolation READ_UNCOMMITTED, tel que défini par la norme ANSI. Toutefois, étant donné que les opérations de lecture sont exécutées sous READ_UNCOMMITTED, très peu d’opérations de blocage se produisent ou conduisent à une contention dans le système.  
  
SQL Server PDW s’appuie sur le moteur de SQL Server sous-jacent pour implémenter le verrouillage et le contrôle d’accès concurrentiel. Si les opérations mènent à un blocage SQL Server sous-jacent au sein du même nœud, SQL Server PDW tire parti de la fonctionnalité de détection de blocage SQL Server et met fin à l’une des instructions bloquantes.  
  
> [!NOTE]  
> SQL Server n’autorise pas les instructions qui attendent que les verrous soient bloqués par les demandes de verrouillage plus récentes. SQL Server PDW n’a pas entièrement implémenté ce processus. Dans SQL Server PDW, les demandes continues de nouveaux verrous partagés peuvent parfois bloquer une demande précédente (mais en attente) pour un verrou exclusif. Par exemple, une instruction **Update** (nécessitant un verrou exclusif) peut être bloquée par des verrous partagés qui sont accordés à une série d’instructions **Select** . Pour résoudre un processus bloqué (identifié par l’examen de la [sys. dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md) DVM), arrêtez d’envoyer de nouvelles demandes jusqu’à ce que le verrou exclusif soit respecté.  
  
## <a name="lock-definition-table"></a>Verrouiller la table de définitions  
SQL Server prend en charge les types de verrous suivants. Tous les types de verrous ne sont pas disponibles sur le nœud de contrôle, mais ils peuvent se produire sur les nœuds de calcul.  
  
-   SCH-S (stabilité du schéma). Garantit que l'élément d'un schéma, tel qu'une table ou un index, n'est pas supprimé alors qu'une session contient un verrou de stabilité du schéma sur l'élément du schéma.  
  
-   SCH-M (modification du schéma). Doit être détenu par toute session destinée à modifier le schéma de la ressource spécifiée. Garantit qu'aucune autre session ne fait référence à l'objet indiqué.  
  
-   S (partagé). La session détenant le verrou peut disposer d'un accès partagé à la ressource.  
  
-   U (mise à jour). Indique qu'un verrouillage de mise à jour a été posé sur des ressources qui peuvent finalement être mises à jour. Utilisé pour empêcher l'occurrence d'une forme de blocage courante qui apparaît lorsque plusieurs sessions verrouillent les ressources pour une mise à jour potentielle ultérieure.  
  
-   X (exclusif). La session détenant le verrou peut disposer d'un accès exclusif à la ressource.  
  
-   IS (partage intentionnel). Indique l'intention de placer des verrous S sur certaines ressources subordonnées dans la hiérarchie de verrouillage.  
  
-   IU (mise à jour intentionnelle). Indique l'intention de placer des verrous U sur certaines ressources subordonnées dans la hiérarchie de verrouillage.  
  
-   IX (Intent exclusif). Indique l'intention de placer des verrous X sur certaines ressources subordonnées dans la hiérarchie de verrouillage.  
  
-   SIU (mise à jour intentionnelle partagée). Signale des accès partagés à une ressource dans le but de poser des verrous de mise à jour sur les ressources subordonnées dans la hiérarchie de verrouillage.  
  
-   SIX (mode partagé intentionnelle exclusif). Signale des accès partagés à une ressource dans le but de poser des verrous exclusifs sur les ressources subordonnées dans la hiérarchie de verrouillage.  
  
-   UIX (mise à jour intentionnelle exclusive). Signale un verrou de mise à jour sur une ressource dans le but de poser des verrous exclusifs sur les ressources subordonnées dans la hiérarchie de verrouillage.  
  
-   BU. Utilisé par les opérations en bloc.  
  
-   RangeS_S (verrou de plage de clés partagé et de ressource partagée). Indique une analyse de plage sérialisable.  
  
-   RangeS_U (verrou de la plage de clés partagée et mise à jour des ressources). Indique une analyse de mise à jour sérialisable.  
  
-   RangeI_N (verrou d’insertion de la plage de clés et de ressources null). Utilisé pour tester les étendues avant l'insertion d'une nouvelle clé dans un index.  
  
-   RangeI_S. Verrou de conversion de groupes de clés, créé par un chevauchement de verrous RangeI_N et S.  
  
-   RangeI_U. Verrou de conversion de groupes de clés, créé par un chevauchement de verrous RangeI_N et U.  
  
-   RangeI_X. Verrou de conversion de groupes de clés, créé par un chevauchement de verrous RangeI_N et X.  
  
-   RangeX_S. Verrou de conversion de groupes de clés, créé par un chevauchement de verrous RangeI_N et RangeS_S.  
  
-   RangeX_U. Verrou de conversion de groupes de clés, créé par un chevauchement de verrous RangeI_N et RangeS_U.  
  
-   RangeX_X (verrou de plage de clés et de ressources exclusives exclusives). Verrou de conversion utilisé lors de la mise à jour d'une clé dans une étendue.  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[sys.dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
