---
title: Utiliser la session system_health | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], system health session
- extended events [SQL Server], system_health session
- system_health session [SQL Server extended events]
- system health session [SQL Server extended events]
ms.assetid: 1e1fad43-d747-4775-ac0d-c50648e56d78
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 6ea2e46b38919ae72ea70440523d75517e6efa92
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52804141"
---
# <a name="use-the-systemhealth-session"></a>Utiliser la session system_health
  La session system_health est une session Événements étendus incluse par défaut avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette session démarre automatiquement en même temps que le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et s’exécute sans effet notable sur les performances. Elle recueille des données système qui peuvent vous aider à résoudre des problèmes de performances dans le [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Il est donc déconseillé de l'arrêter ou de la supprimer.  
  
 Cette session recueille des informations, dont les suivantes :  
  
-   Le sql_text et le session_id des sessions qui rencontrent une erreur de gravité >= 20.  
  
-   Le sql_text et le session_id des sessions qui rencontrent une erreur de mémoire. Il s'agit des erreurs 17803, 701, 802, 8645, 8651, 8657 et 8902.  
  
-   L'historique des problèmes d'improductivité du planificateur. (Ceux-ci s'affichent dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sous l'erreur 17883).  
  
-   Les interblocages détectés.  
  
-   Le callstack, sql_text et le session_id des sessions ayant attendu des verrous (ou d’autres ressources pertinentes) pendant plus de 15 secondes.  
  
-   Le callstack, le sql_text et le session_id des sessions ayant attendu des verrous pendant plus de 30 secondes.  
  
-   Le callstack, le sql_text et le session_id des sessions ayant attendu longtemps des attentes préemptives. La durée varie selon le type d'attente. Une attente préemptive est une situation où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attend des appels d'API externes.  
  
-   callstack et session_id pour l'allocation CLR et les échecs d'allocation virtuelle.  
  
-   Les événements ring_buffer pour le gestionnaire d'allocation mémoire, le moniteur du planificateur, l'insuffisance mémoire du nœud de mémoire, la sécurité et la connectivité.  
  
-   Résultats des composants système depuis sp_server_diagnostics.  
  
-   Intégrité de l'instance recueillie par scheduler_monitor_system_health_ring_buffer_recorded.  
  
-   Échecs d'allocation CLR  
  
-   Erreurs de connectivité avec connectivity_ring_buffer_recorded.  
  
-   Erreurs de sécurité avec security_error_ring_buffer_recorded.  
  
## <a name="viewing-the-session-data"></a>Consultation des données de session  
 La session utilise la cible de mémoire tampon en anneau pour stocker les données. Pour consulter les données de session, utilisez la requête suivante :  
  
```  
SELECT CAST(xet.target_data as xml) FROM sys.dm_xe_session_targets xet  
JOIN sys.dm_xe_sessions xe  
ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'system_health'  
```  
  
 Pour afficher les données de session depuis les fichier d'événements, utilisez l'interface utilisateur Événements étendus disponible dans Management Studio. Consultez [afficher les données de Session événements](../../database-engine/view-event-session-data.md) pour plus d’informations.  
  
## <a name="restoring-the-systemhealth-session"></a>Restauration de la session system_health  
 Si vous supprimez la session system_health, vous pouvez la restaurer en exécutant le fichier **u_tables.sql** dans l’Éditeur de requête. Ce fichier se trouve dans le dossier suivant, où C: représente le lecteur sur lequel vous avez installé les fichiers du programme [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
 C:\Program Files\Microsoft SQL Server\MSSQL12. \< *instanceid*> \MSSQL\Install  
  
 Sachez qu’après avoir restauré la session, vous devez la démarrer en utilisant l’instruction ALTER EVENT SESSION ou en utilisant le nœud **Événements étendus** dans l’Explorateur d’objets. Sinon, la session démarre automatiquement la prochaine fois que vous redémarrerez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Outils associés aux événements étendus](extended-events-tools.md)  
  
  
