---
title: sysmail_allitems (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_allitems_TSQL
- sysmail_allitems
dev_langs: TSQL
helpviewer_keywords: sysmail_allitems database mail view
ms.assetid: 21fb8432-7677-4435-902f-64a58bba4cbb
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0abb8eb792b85eed60df52f70a2c13c2e3f920d8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailallitems-transact-sql"></a>sysmail_allitems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque message traité par la messagerie de base de données. Utilisez cette vue lorsque vous voulez voir l'état de tous les messages.  
  
 Pour afficher uniquement les messages avec l’état d’échec, utilisez [sysmail_faileditems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md). Pour afficher uniquement les messages non envoyés, utilisez [sysmail_unsentitems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md). Pour afficher uniquement les messages qui ont été envoyés, utilisez [sysmail_sentitems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md).  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**mailitem_id**|**int**|Identificateur de l'élément de messagerie dans la file d'attente des messages.|  
|**profile_id**|**int**|Identificateur du profil utilisé pour envoyer le message.|  
|**destinataires**|**varchar(max)**|Adresses de messagerie des destinataires du message.|  
|**destinataires_en_copie**|**varchar(max)**|Adresses de messagerie des personnes qui reçoivent une copie du message.|  
|**destinataires_en_copie_aveugle**|**varchar(max)**|Adresses de messagerie des personnes qui reçoivent une copie du message mais dont le nom n'apparaît pas dans l'en-tête du message.|  
|**Objet**|**nvarchar(510)**|Ligne d'objet du message.|  
|**corps**|**varchar(max)**|Le corps du message.|  
|**body_format**|**varchar (20)**|Le format du corps du message. Les valeurs possibles sont TEXT et HTML.|  
|**importance**|**varchar(6)**|Le **importance** paramètre du message.|  
|**respect de la**|**varchar(12)**|Le **sensibilité** paramètre du message.|  
|**file_attachments**|**varchar(max)**|Liste des noms de fichiers joints au message électronique (délimitée par des points-virgules).|  
|**attachment_encoding**|**varchar (20)**|Type de pièce jointe.|  
|**requête**|**varchar(max)**|Requête exécutée par le programme de messagerie.|  
|**execute_query_database**|**sysname**|Contexte de base de données dans lequel le programme de messagerie a exécuté la requête.|  
|**attach_query_result_as_file**|**bit**|Lorsque la valeur est 0, les résultats de la requête ont été inclus dans le corps du message électronique, après le contenu du corps. Lorsque la valeur est 1, les résultats ont été renvoyés sous forme de pièce jointe.|  
|**query_result_header**|**bit**|Lorsque la valeur est 1, cela signifie que les résultats de la requête contenaient des en-têtes de colonne. Lorsque la valeur est 0, cela signifie que les résultats de la requête ne contenaient pas d'en-têtes de colonne.|  
|**query_result_width**|**int**|Le **query_result_width** paramètre du message.|  
|**query_result_separator**|**char (1)**|Caractère utilisé pour séparer les colonnes dans la sortie de la requête.|  
|**exclude_query_output**|**bit**|Le **exclude_query_output** paramètre du message. Pour plus d’informations, consultez [sp_send_dbmail &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).|  
|**append_query_error**|**bit**|Le **append_query_error** paramètre du message. La valeur 0 indique que la messagerie de base de données ne doit pas envoyer le message électronique s'il existe une erreur dans la requête.|  
|**send_request_date**|**datetime**|Date et heure d'arrivée du message dans la file d'attente des messages.|  
|**send_request_user**|**sysname**|Utilisateur qui a envoyé le message. Il s'agit du contexte utilisateur de la procédure de la messagerie de base de données, et non du champ De : du message.|  
|**sent_account_id**|**int**|Identificateur du compte de messagerie de base de données utilisé pour envoyer le message.|  
|**sent_status**|**varchar(8)**|État du message. Les valeurs possibles sont :<br /><br /> **envoyé** -le message a été envoyé.<br /><br /> **non envoyé** -messagerie de base de données tente toujours d’envoyer le message.<br /><br /> **une nouvelle tentative** -messagerie de base de données n’a pas pu envoyer le message, mais tente d’envoyer de nouveau.<br /><br /> **Échec de** -messagerie de base de données n’a pas pu envoyer le message.|  
|**sent_date**|**datetime**|Date et heure d'envoi du message.|  
|**last_mod_date**|**datetime**|Date et heure de la dernière modification de la ligne.|  
|**last_mod_user**|**sysname**|Dernier utilisateur qui a modifié la ligne.|  
  
## <a name="remarks"></a>Notes  
 Utilisez le **sysmail_allitems** pour afficher l’état de tous les messages traités par la messagerie de base de données. En cas de dépannage de la messagerie de base de données, cette vue peut vous aider à identifier la nature du problème en vous permettant de comparer les attributs des messages qui ont été envoyés aux attributs des messages qui n'ont pas été envoyés.  
  
 Les tables système affichées dans cette vue contiennent tous les messages et peut entraîner la **msdb** base de données augmente. Supprimez périodiquement les anciens messages de la vue afin de réduire la taille de ces tables. Pour plus d’informations, consultez [créer un travail de l’Agent SQL Server pour archiver les Messages de messagerie de base de données et les journaux des événements](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md).  
  
## <a name="permissions"></a>Permissions  
 Accordées à **sysadmin** rôle serveur fixe et **DatabaseMailUserRole** rôle de base de données. Lors de l’exécution par un membre de la **sysadmin** rôle serveur fixe, cette vue affiche tous les messages. Les autres utilisateurs voient uniquement les messages qu'ils ont essayé d'envoyer.  
  
  
