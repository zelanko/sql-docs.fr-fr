---
title: Sessions utilisateur
description: Sessions utilisateur dans les Data Warehouse parallèles d’Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: a0e5b338cc616be214ef39527551ee4a6ffd8f56
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "74399401"
---
# <a name="user-sessions-in-analytics-platform-system"></a>Sessions utilisateur dans Analytics Platform System
Une connexion avec les autorisations appropriées peut gérer les sessions de toutes les connexions sur un appareil SQL Server PDW, y compris l’exécution des actions suivantes :  
  
-   Affichez les sessions actuelles sur l’appliance, y compris les sessions actives et inactives.  
  
-   Affichez les requêtes actives et récentes pour une session.  
  
-   Terminer les sessions actives.  
  
Ces actions peuvent être effectuées à l’aide de l' [analyse de l’appliance à l’aide de la console d’administration](monitor-the-appliance-by-using-the-admin-console.md) ou des [vues système](tsql-system-views.md) via les commandes SQL, comme indiqué ci-dessous.  
  
Les autorisations requises pour gérer les sessions à l’aide de l’une ou l’autre méthode sont les mêmes, et sont décrites dans [accorder des autorisations pour gérer les connexions, les utilisateurs et les rôles de base de données](grant-permissions.md#grant-permissions-to-manage-logins-users-and-database-roles).  
  
## <a name="manage-sessions-by-using-the-admin-console"></a>Gérer les sessions à l’aide de la console d’administration  
  
### <a name="to-view-current-sessions-by-using-the-admin-console"></a>Pour afficher les sessions en cours à l’aide de la console d’administration  
  
1.  Dans le menu supérieur, cliquez sur **sessions**.  
  
2.  La liste résultante affiche toutes les sessions récentes. Pour afficher uniquement les sessions actives ou inactives, cliquez sur l’en-tête de colonne **État** pour trier les résultats par État.  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-the-admin-console"></a>Pour afficher les requêtes actives et récentes pour une session à l’aide de la console d’administration  
  
1.  Dans le menu supérieur, cliquez sur **sessions**.  
  
2.  Dans la liste des résultats, cliquez sur l’ID de session de la session souhaitée.  
  
3.  La liste requêtes résultantes affiche les requêtes récentes pour la session. Pour plus d’informations sur l’affichage des détails d’une requête, consultez [surveillance des requêtes actives](monitoring-active-queries.md).  
  
### <a name="to-end-sessions-by-using-the-admin-console"></a>Pour terminer des sessions à l’aide de la console d’administration  
  
1.  Dans le menu supérieur, cliquez sur **sessions**.  
  
2.  Recherchez l’ID de session pour la session à annuler.  
  
3.  Cliquez sur le **X** rouge à gauche de l’ID de session pour mettre fin à la session. Seules les sessions dont l’État est « actif » ou « inactif » auront un **X**rouge. seules ces sessions peuvent être terminées.  
  
## <a name="manage-sessions-by-using-system-views-and-sql-commands"></a>Gérer les sessions à l’aide des vues système et des commandes SQL  
  
### <a name="to-view-current-sessions-by-using-system-views"></a>Pour afficher les sessions en cours à l’aide des vues système  
Utilisez [sys. dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) pour générer une liste des sessions actives.  
  
Cet exemple retourne le session_id, login_name et l’état de toutes les sessions dont l’État est « actif » ou « inactif ».  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions WHERE status='Active' OR status='Idle';  
```  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-system-views"></a>Pour afficher les requêtes actives et récentes pour une session à l’aide des vues système  
Pour afficher les requêtes actives et récemment terminées associées à une session, vous utilisez les vues [sys. dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) et [sys. dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md) . Cette requête renvoie une liste de toutes les sessions actives ou inactives, ainsi que toutes les requêtes actives ou récentes associées à chaque ID de session.  
  
```sql  
SELECT es.session_id, es.login_name, es.status AS sessionStatus,   
er.request_id, er.status AS requestStatus, er.command   
FROM sys.dm_pdw_exec_sessions es   
LEFT OUTER JOIN sys.dm_pdw_exec_requests er   
ON (es.session_id=er.session_id)   
WHERE (es.status='Active' OR es.status='Idle') AND   
(er.status!= 'Completed' AND er.status!= 'Failed' AND er.status!= 'Cancelled');  
```  
  
### <a name="to-end-sessions-by-using-sql-commands"></a>Pour terminer des sessions à l’aide de commandes SQL  
Utilisez la commande [Kill](../t-sql/language-elements/kill-transact-sql.md) pour mettre fin à une session active. Vous aurez besoin de l’ID de session pour terminer le processus, qui peut être obtenu à l’aide de la vue [sys. dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) .  
  
Dans cet exemple, sélectionnez les valeurs login_name, session_id et État pour rechercher une session en fonction du nom de connexion.  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions;  
```  
  
Les sessions dont l’État est « actif » ou « inactif » peuvent être terminées à l’aide de la commande KILL.  
  
```sql  
KILL 'SID137';  
```  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
