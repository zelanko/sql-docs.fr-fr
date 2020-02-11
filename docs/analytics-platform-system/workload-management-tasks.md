---
title: Tâches de gestion des charges de travail
description: Tâches de gestion des charges de travail dans Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 88d95eb0a2e0805930cb5f01f5af05b8fc6b3f2e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74399412"
---
# <a name="workload-management-tasks-in-analytics-platform-system"></a>Tâches de gestion des charges de travail dans Analytics Platform System
Tâches de gestion des charges de travail dans Analytics Platform System.

## <a name="view-login-members-of-each-resource-class"></a>Afficher les membres de connexion de chaque classe de ressources
Décrit comment afficher les membres de connexion de chaque rôle de serveur de classe de ressource dans SQL Server PDW. Utilisez cette requête pour déterminer la classe de ressources autorisée pour les demandes soumises par chaque connexion.  
  
Pour obtenir des descriptions des classes de ressources, consultez [gestion des charges de travail](workload-management.md).  
  
Cette requête affiche la liste des membres de chaque classe de ressources. Il existe trois classes de ressources, mediumrc, largerc et xlargerc.  
  
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
  
Si une connexion ne figure pas dans cette liste, ses demandes recevront les ressources par défaut. Si une connexion est membre de plusieurs classes de ressources, la classe la plus grande est prioritaire.  
  
Les allocations de ressources sont répertoriées dans la [gestion des charges de travail](workload-management.md).  
  
## <a name="change-the-system-resources-allocated-to-a-request"></a>Modifier les ressources système allouées à une demande
Décrit comment déterminer la classe de ressources dans laquelle une demande de SQL Server PDW s’exécute, puis comment modifier les ressources système pour cette demande. La modification des ressources pour une demande nécessite la modification de l’appartenance à la classe de ressource de la connexion qui soumet la demande, à l’aide de l’instruction [ALTER Server Role](../t-sql/statements/alter-server-role-transact-sql.md) .  
  
### <a name="step-1-determine-the-resource-class-for-the-login-running-the-request"></a>Étape 1 : déterminer la classe de ressource pour la connexion qui exécute la demande.  
Cette requête affiche les connexions qui sont membres des appartenances aux rôles de serveur de la classe de ressources. Il existe trois classes de ressources, **mediumrc**, **largerc**et **xlargerc**.  
  
> [!IMPORTANT]  
> Cette requête doit être exécutée par une connexion disposant de l’autorisation **Control Server** . Si elle est exécutée par une connexion sans autorisation **Control Server** , cette requête retourne uniquement les appartenances aux rôles pour la connexion actuelle.  
  
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
  
Si aucune connexion n’est membre d’un rôle de serveur de classe de ressources, la table résultante est vide. Dans ce cas, si la requête retourne une connexion nommée Ching, lorsque Ching envoie une demande, celle-ci reçoit les ressources système par défaut, qui sont plus petites que les ressources système de la classe de ressources. Si une connexion est membre de plusieurs classes de ressources, la classe la plus grande est prioritaire.  
  
Pour obtenir la liste des allocations de ressources pour chaque classe de ressources, consultez Gestion de la [charge de travail](workload-management.md).  
  
### <a name="step-2-run-the-request-under-a-login-with-different-resource-class-membership"></a>Étape 2 : exécuter la demande sous une connexion avec une appartenance à une classe de ressource différente  
Il existe deux façons d’exécuter une demande avec des ressources système plus volumineuses ou plus petites :  
  
-   Exécutez la demande sous une connexion différente qui est membre d’une classe de ressources plus grande ou plus petite.  
  
-   Ajoutez la connexion nécessaire à l’un des rôles de la classe de ressources. Choisissez cette option avec précaution ; la modification de la classe de ressource pour la connexion modifie le niveau des ressources système pour toutes les demandes soumises par la connexion.  
  
Supposons que Ching est membre du rôle de serveur largerc. L’exemple suivant montre comment ajouter Ching de connexion au rôle de serveur xlargerc.  
  
```sql  
ALTER SERVER ROLE xlargerc ADD MEMBER Ching;  
```  
  
Ching est désormais membre des rôles de serveur largerc et xlargerc. Lorsque Ching envoie des demandes, les demandes reçoivent les ressources système xlargerc.  
  
L’exemple suivant déplace Ching vers le rôle de serveur mediumrc.  Pour passer au nouveau rôle, la connexion doit être supprimée des rôles serveur xlargerc et largerc, puis ajoutée au rôle serveur mediumrc.  
  
```sql  
-- Move login Ching back to using medium system resources for requests.  
ALTER SERVER ROLE xlargerc DROP MEMBER Ching;  
ALTER SERVER ROLE largerc DROP MEMBER Ching;  
ALTER SERVER ROLE mediumrc ADD MEMBER Ching;  
```  
  
Ching est désormais membre du rôle de serveur mediumrc.  L’exemple suivant modifie Ching pour avoir les ressources système par défaut pour les demandes.  
  
```sql  
-- Move login Ching to use the default system resources for requests.  
ALTER SERVER ROLE mediumrc DROP MEMBER Ching;  
```  
  
Pour plus d’informations sur la modification de l’appartenance au rôle de la classe de ressources, consultez [ALTER Server Role](../t-sql/statements/alter-server-role-transact-sql.md).  

## <a name="change-a-login-to-the-default-system-resources-for-its-requests"></a>Changer une connexion aux ressources système par défaut pour ses demandes
Décrit comment modifier les allocations de ressources système affectées à un SQL Server PDW connexion aux montants par défaut. 
  
Pour obtenir des descriptions des classes de ressources, consultez [gestion des charges de travail](workload-management.md)  
  
Lorsqu’un compte de connexion n’est membre d’aucun rôle de serveur de classe de ressources, les demandes envoyées par la connexion reçoivent la quantité par défaut de ressources système.  
  
Supposons que la connexion Matt est actuellement un membre de tous les rôles de serveur de classes de ressources et qu’elle souhaite restaurer les ressources par défaut uniquement pour les requêtes.  L’exemple suivant affecte les ressources par défaut aux demandes de Matt en supprimant son appartenance des trois rôles de serveur de classe de ressources.  
  
```sql  
--Give the requests submitted by Matt the default system resources   
--by dropping Matt from all resource class server roles.  
ALTER SERVER ROLE XLargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE LargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE MediumRC DROP MEMBER Matt;  
```  
  
## <a name="display-the-number-of-concurrency-slots-needed-for-a-waiting-request"></a>Afficher le nombre d’emplacements de concurrence requis pour une demande en attente
Décrit comment déterminer le nombre d’emplacements de concurrence requis par une demande en attente d’exécution sur SQL Server PDW.  
  
Pour plus d’informations, consultez Gestion de la [charge de travail](workload-management.md).  
  
Une demande peut être en attente trop longue sans être exécutée. L’une des façons de résoudre la demande consiste à examiner le nombre d’emplacements de concurrence dont la demande a besoin.  L’exemple suivant montre le nombre d’emplacements de concurrence requis par chaque demande en attente.  
  
```sql  
--Display the number of concurrency slots required   
--for each request that is waiting to run.  
SELECT request_id, concurrency_slots_used AS [Slots Needed], resource_class AS [Resource Class]  
FROM sys.dm_pdw_resource_waits;  
```  
  
  
## <a name="see-also"></a>Voir aussi  
[Gestion des charges de travail](workload-management.md)  
  
