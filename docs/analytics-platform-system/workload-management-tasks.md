---
title: Tâches de gestion des charges de travail - Analytique Platform System | Microsoft Docs
description: Tâches de gestion de la charge de travail d’Analytique Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 8e538b96c482a6a16fffcfdac197e62885426b52
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63243798"
---
# <a name="workload-management-tasks-in-analytics-platform-system"></a>Tâches de gestion des charges de travail d’Analytique Platform System
Tâches de gestion de la charge de travail d’Analytique Platform System.

## <a name="view-login-members-of-each-resource-class"></a>Afficher les membres de connexion de chaque classe de ressources
Décrit comment afficher les membres de la connexion de chaque rôle de serveur de classe de ressources dans SQL Server PDW. Utilisez cette requête pour déterminer la classe de ressources autorisé pour les demandes envoyées par chaque connexion.  
  
Pour une description de classe de ressource, consultez [gestion de la charge de travail](workload-management.md).  
  
Cette requête affiche la liste des membres pour chaque classe de ressources. Il existe trois classes de ressources mediumrc, largerc et xlargerc.  
  
```sql  
SELECT l.name AS [member], r.name AS [server role]  
FROM sys.server_role_members AS rm  
JOIN sys.server_principals AS l  
  ON l.principal_id = rm.member_principal_id  
JOIN  
  sys.server_principals AS r  
  ON r.principal_id = rm.role_principal_id  
WHERE  
  ( l.[type] = 'S' OR l.[type] = 'U' OR l.[type] = 'G' )  
  AND r.[type] = 'R'  
  AND r.[name] in ('mediumrc', 'largerc', 'xlargerc');  
```  
  
Si une connexion n’est pas dans cette liste, ses demandes recevront les ressources par défaut. Si une connexion est membre de plusieurs classes de ressources, la plus grande classe a la priorité.  
  
Les allocations de ressources sont répertoriées dans [gestion de la charge de travail](workload-management.md).  
  
## <a name="change-the-system-resources-allocated-to-a-request"></a>Les ressources système allouées à une demande de modification
Décrit comment déterminer quelle ressource classe une demande de SQL Server PDW est en cours d’exécution sous, puis comment modifier les ressources système pour cette requête. Modifier les ressources pour une demande nécessite de modifier l’appartenance de classe de ressource de la connexion d’envoi de la demande, à l’aide de la [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md) instruction.  
  
### <a name="step-1-determine-the-resource-class-for-the-login-running-the-request"></a>Étape 1 : Déterminer la classe de ressource pour la connexion à la demande en cours d’exécution.  
Cette requête affiche les connexions qui sont membres de l’appartenance aux rôles de ressource classe serveur. Il existe trois classes de ressources, **mediumrc**, **largerc**, et **xlargerc**.  
  
> [!IMPORTANT]  
> Cette requête doit être exécutée par une connexion qui a **CONTROL SERVER** autorisation. Si exécutée par une connexion sans **CONTROL SERVER** autorisation, cette requête retourne uniquement les appartenances aux rôles pour la connexion actuelle.  
  
```sql  
SELECT l.name AS [member], r.name AS [server role]  
FROM sys.server_role_members AS rm  
JOIN sys.server_principals AS l  
  ON l.principal_id = rm.member_principal_id  
JOIN  
  sys.server_principals AS r  
  ON r.principal_id = rm.role_principal_id  
WHERE  
  l.[type] = 'S'   
  AND r.[type] = 'R'  
  AND r.[name] in ('mediumrc', 'largerc', 'xlargerc');  
GO  
```  
  
S’il n’y a aucune ouverture de session qui sont membres d’un rôle de serveur de classe de ressource, la table résultante sera vide. Dans ce cas, si la requête retourne une connexion nommée Ching, puis lorsque Ching soumet une demande, la requête reçoit les ressources système par défaut, qui sont plus petites que les ressources de système de classe de ressource. Si une connexion est membre de plusieurs classes de ressources, la plus grande classe a la priorité.  
  
Pour obtenir la liste des allocations de ressources pour chaque classe de ressources, consultez [gestion de la charge de travail](workload-management.md).  
  
### <a name="step-2-run-the-request-under-a-login-with-different-resource-class-membership"></a>Étape 2 : Exécuter la requête sous un compte de connexion avec l’appartenance de classe de ressources différents  
Il existe deux façons d’exécuter une requête avec des ressources système supérieure ou inférieure :  
  
-   Exécuter la demande sous une autre connexion est membre d’une classe de ressource supérieure ou inférieure.  
  
-   Ajouter la connexion nécessaire à un des rôles de classe de ressource. Choisissez cette option avec précaution ; modification de la classe de ressource pour la connexion modifiera le niveau de ressources système pour toutes les demandes soumises par la connexion.  
  
Supposons que Ching est un membre du rôle de serveur largerc. L’exemple suivant montre comment ajouter la connexion Ching au rôle de serveur xlargerc.  
  
```sql  
ALTER SERVER ROLE xlargerc ADD MEMBER Ching;  
```  
  
Ching est maintenant un membre de la largerc et xlargerc des serveurs. Lorsque Ching soumet des demandes, les demandes reçoit les ressources du système xlargerc.  
  
L’exemple suivant déplace Ching vers le rôle de serveur mediumrc.  Pour basculer vers le nouveau rôle, la connexion doit être supprimée à partir des rôles de serveur de largerc et xlargerc et ajoutée au rôle de serveur mediumrc.  
  
```sql  
-- Move login Ching back to using medium system resources for requests.  
ALTER SERVER ROLE xlargerc DROP MEMBER Ching;  
ALTER SERVER ROLE largerc DROP MEMBER Ching;  
ALTER SERVER ROLE mediumrc ADD MEMBER Ching;  
```  
  
Ching est maintenant membre du rôle de serveur mediumrc.  L’exemple suivant modifie Ching de disposer des ressources système par défaut pour les demandes.  
  
```sql  
-- Move login Ching to use the default system resources for requests.  
ALTER SERVER ROLE mediumrc DROP MEMBER Ching;  
```  
  
Pour plus d’informations sur la modification d’appartenance au rôle de classe de ressource, consultez [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md).  

## <a name="change-a-login-to-the-default-system-resources-for-its-requests"></a>Modifier une connexion aux ressources système par défaut pour ses demandes
Décrit comment modifier les allocations de ressources système affectées à une connexion SQL Server PDW pour les quantités par défaut. 
  
Pour une description de classe de ressource, consultez [gestion de la charge de travail](workload-management.md)  
  
Quand une connexion n’est pas un membre de n’importe quel rôle de serveur de classe de ressource, demandes soumises par la connexion reçoit la quantité par défaut des ressources système.  
  
Supposons que la connexion est actuellement membre de tous les rôles de serveur de classe de ressource de Matt et souhaite revenir à des requêtes à recevoir uniquement les ressources par défaut.  L’exemple suivant affecte les ressources par défaut pour les demandes de Matt a en déposant son appartenance à partir de tous les rôles de serveur de classe de ressource de trois.  
  
```sql  
--Give the requests submitted by Matt the default system resources   
--by dropping Matt from all resource class server roles.  
ALTER SERVER ROLE XLargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE LargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE MediumRC DROP MEMBER Matt;  
```  
  
## <a name="display-the-number-of-concurrency-slots-needed-for-a-waiting-request"></a>Afficher que le nombre d’emplacements de concurrence nécessaire pour un attente demande
Décrit comment déterminer le nombre d’accès concurrentiel emplacements sont nécessaires à une demande en attente d’exécution sur SQL Server PDW.  
  
Pour plus d’informations, consultez [gestion de la charge de travail](workload-management.md).  
  
Une demande peut attendre trop longtemps sans exécutée. Un des moyens de résoudre les problèmes de la demande consiste à examiner le nombre d’emplacements de concurrence qu'a besoin de la demande.  L’exemple suivant montre le nombre d’emplacements de concurrence requises par chaque requête en attente.  
  
```sql  
--Display the number of concurrency slots required   
--for each request that is waiting to run.  
SELECT request_id, concurrency_slots_used AS [Slots Needed], resource_class AS [Resource Class]  
FROM sys.dm_pdw_resource_waits;  
```  
  
  
## <a name="see-also"></a>Voir aussi  
[Gestion de la charge de travail](workload-management.md)  
  
