---
title: sysmail_faileditems (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- sysmail_faileditems
- sysmail_faileditems_TSQL
dev_langs: TSQL
helpviewer_keywords: sysmail_faileditems database mail view
ms.assetid: a31562c5-358e-4cfc-a72d-b3faccc53851
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9872591d38bfedcd0b6c4e0f28a7922ace26b849
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailfaileditems-transact-sql"></a>sysmail_faileditems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque message de la messagerie de base de données avec le **échec** état. Utilisez cette vue pour déterminer quels messages n'ont pas pu être envoyés.  
  
 Pour afficher tous les messages traités par la messagerie de base de données, utilisez [sysmail_allitems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md). Pour afficher uniquement les messages non envoyés, utilisez [sysmail_unsentitems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md). Pour afficher uniquement les messages qui ont été envoyés, utilisez [sysmail_sentitems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md). Pour afficher les pièces jointes, utilisez [sysmail_mailattachments &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql.md).  
  
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
|**Attachment_encoding**|**varchar (20)**|Type de pièce jointe.|  
|**Requête**|**varchar(max)**|Requête exécutée par le programme de messagerie.|  
|**execute_query_database**|**sysname**|Contexte de base de données dans lequel le programme de messagerie a exécuté la requête.|  
|**attach_query_result_as_file**|**bit**|Lorsque la valeur est 0, les résultats de la requête ont été inclus dans le corps du message électronique, après le contenu du corps. Lorsque la valeur est 1, les résultats ont été renvoyés sous forme de pièce jointe.|  
|**query_result_header**|**bit**|Lorsque la valeur est 1, cela signifie que les résultats de la requête contenaient des en-têtes de colonne. Lorsque la valeur est 0, cela signifie que les résultats de la requête ne contenaient pas d'en-têtes de colonne.|  
|**query_result_width**|**int**|Le **query_result_width** paramètre du message.|  
|**query_result_separator**|**char (1)**|Caractère utilisé pour séparer les colonnes dans la sortie de la requête.|  
|**exclude_query_output**|**bit**|Le **exclude_query_output** paramètre du message. Pour plus d’informations, consultez [sp_send_dbmail &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).|  
|**append_query_error**|**bit**|Le **append_query_error** paramètre du message. La valeur 0 indique que la messagerie de base de données ne doit pas envoyer le message électronique s'il existe une erreur dans la requête.|  
|**send_request_date**|**datetime**|Date et heure d'arrivée du message dans la file d'attente des messages.|  
|**send_request_user**|**sysname**|Utilisateur qui a envoyé le message. Il s'agit du contexte utilisateur de la procédure de la messagerie de base de données, et non du champ De : du message.|  
|**sent_account_id**|**int**|Identificateur du compte de messagerie de base de données utilisé pour envoyer le message. La valeur est toujours NULL pour cette vue.|  
|**sent_status**|**varchar(8)**|État du message. Toujours **échec** pour cette vue.|  
|**sent_date**|**datetime**|Date et heure à laquelle le message a été retiré de la file d'attente des messages.|  
|**last_mod_date**|**datetime**|Date et heure de la dernière modification de la ligne.|  
|**last_mod_user**|**sysname**|Dernier utilisateur qui a modifié la ligne.|  
  
## <a name="remarks"></a>Notes  
 Utilisez le **sysmail_faileditems** pour afficher les messages qui n’ont pas été envoyés par la messagerie de base de données. En cas de dépannage de la messagerie de base de données, cette vue peut vous aider à identifier la nature du problème en vous montrant les attributs des messages qui n'ont pas pu être envoyés. Pour afficher la raison de l’échec, consultez l’entrée pour le message ayant échoué dans le [sysmail_event_log &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md) vue.  
  
## <a name="permissions"></a>Permissions  
 Accordées à **sysadmin** rôle serveur fixe et **databasemailuserrole** rôle de base de données. Lors de l’exécution par un membre de la **sysadmin** rôle serveur fixe, cette vue affiche tous les échecs de messages. Les autres utilisateurs voient uniquement les messages qu'ils ont essayé d'envoyer et qui ont échoué.  
  
  
