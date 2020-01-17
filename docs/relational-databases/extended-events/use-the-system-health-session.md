---
title: Utiliser la session system_health
ms.date: 11/27/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xevents
ms.topic: tutorial
helpviewer_keywords:
- extended events [SQL Server], system health session
- extended events [SQL Server], system_health session
- system_health session [SQL Server extended events]
- system health session [SQL Server extended events]
ms.assetid: 1e1fad43-d747-4775-ac0d-c50648e56d78
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ab31461888588ee54f1715f5e98ddb0f3b9aa23b
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75246140"
---
# <a name="use-the-system_health-session"></a>Utiliser la session system_health

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

La session system_health est une session Événements étendus incluse par défaut avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette session démarre automatiquement en même temps que le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et s’exécute sans effet notable sur les performances. Elle recueille des données système qui peuvent vous aider à résoudre des problèmes de performances dans le [!INCLUDE[ssDE](../../includes/ssde-md.md)]. 

> [!IMPORTANT]
> Nous vous déconseillons d’arrêter, de modifier ou de supprimer la session system_health. Tout changement apporté aux paramètres de la session system_health peut être remplacé par une mise à jour future du produit.
  
Cette session recueille des informations, dont les suivantes :  
  
-   Le *sql_text* et le *session_id* des sessions qui rencontrent une erreur de gravité >= 20.  
  
-   Le *sql_text* et le *session_id* des sessions qui rencontrent une erreur de mémoire. Il s'agit des erreurs 17803, 701, 802, 8645, 8651, 8657 et 8902.  
  
-   L'historique des problèmes d'improductivité du planificateur. Ceux-ci s’affichent dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sous l’erreur 17883.  
  
-   Tous les blocages qui sont détectés, y compris le graphique de blocage.  
  
-   Le *callstack*, le *sql_text* et le *session_id* des sessions ayant attendu des verrous (ou d’autres ressources pertinentes) pendant plus de 15 secondes.  
  
-   Le *callstack*, le *sql_text* et le *session_id* des sessions ayant attendu des verrous pendant plus de 30 secondes.  
  
-   Le *callstack*, le *sql_text* et le *session_id* des sessions ayant attendu longtemps des attentes préemptives. La durée varie selon le type d'attente. Une attente préemptive est une situation où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attend des appels d'API externes.  
  
-   Le *callstack* et le *session_id* pour l’allocation CLR et les échecs d’allocation virtuelle.  
  
-   Les événements de mémoire tampon en anneau pour le gestionnaire d’allocation mémoire, le moniteur du planificateur, l’insuffisance mémoire du nœud de mémoire, la sécurité et la connectivité.  
  
-   Résultats des composants système à partir de `sp_server_diagnostics`.  
  
-   Intégrité de l’instance recueillie par *scheduler_monitor_system_health_ring_buffer_recorded*.  
  
-   Échecs d'allocation CLR  
  
-   Erreurs de connectivité avec *connectivity_ring_buffer_recorded*.  
  
-   Erreurs de sécurité avec *security_error_ring_buffer_recorded*.  

> [!NOTE]
> Pour plus d’informations sur les blocages, consultez la [section Interblocage du Guide du verrouillage des transactions et du contrôle de version de ligne](../../relational-databases/sql-server-transaction-locking-and-row-versioning-guide.md#deadlocks).   
> Pour plus d’informations sur les messages d’erreur SQL, consultez [Erreurs du moteur de base de données](../../relational-databases/errors-events/database-engine-events-and-errors.md).

## <a name="viewing-the-session-data"></a>Consultation des données de session  
La session utilise la cible de mémoire tampon en anneau et la cible de fichier d’événements pour stocker les données. La cible de fichier d’événements est configurée avec une taille maximale de 5 Mo et une stratégie de rétention de fichier de 4 fichiers. 

Pour afficher les données de session à partir de la cible de mémoire tampon en anneau avec l’interface utilisateur Événements étendus disponible dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], consultez [Affichage avancé des données cibles d’événements étendus dans SQL Server - Surveiller les données actives](../../relational-databases/extended-events/advanced-viewing-of-target-data-from-extended-events-in-sql-server.md#b3-watch-live-data).

Pour afficher les données de session à partir de la cible de mémoire tampon en anneau avec [!INCLUDE[tsql](../../includes/tsql-md.md)], utilisez la requête suivante :  
  
```sql  
SELECT CAST(xet.target_data as xml) 
FROM sys.dm_xe_session_targets xet  
JOIN sys.dm_xe_sessions xe ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'system_health'  
```  
  
Pour afficher les données de session depuis le fichier d’événements, utilisez l’interface utilisateur Événements étendus disponible dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, consultez [Affichage avancé des données cibles à partir d’événements étendus dans SQL Server](../../relational-databases/extended-events/advanced-viewing-of-target-data-from-extended-events-in-sql-server.md).
  
## <a name="restoring-the-system_health-session"></a>Restauration de la session system_health  
Si vous supprimez la session system_health, vous pouvez la restaurer en exécutant le fichier **u_tables.sql** dans l’Éditeur de requête. Ce fichier se trouve dans le dossier suivant, où **C:** représente le lecteur sur lequel vous avez installé les fichiers du programme [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et **MSSQL1x** la version principale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
 `C:\Program Files\Microsoft SQL Server\MSSQL1x.\<*instanceid*>\MSSQL\Install`  
  
Sachez qu’après avoir restauré la session, vous devez la démarrer en utilisant l’instruction `ALTER EVENT SESSION` ou en utilisant le nœud **Événements étendus** dans l’Explorateur d’objets. Sinon, la session démarre automatiquement la prochaine fois que vous redémarrerez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)    
 [Outils associés aux événements étendus](../../relational-databases/extended-events/extended-events-tools.md)    
 [Erreurs du moteur de base de données](../../relational-databases/errors-events/database-engine-events-and-errors.md)    
 [Affichages catalogue des messages (d’erreur) - sys.messages](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md) 
