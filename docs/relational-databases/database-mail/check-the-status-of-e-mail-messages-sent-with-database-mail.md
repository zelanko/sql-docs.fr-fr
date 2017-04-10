---
title: "V&#233;rifier l&#39;&#233;tat des messages &#233;lectroniques envoy&#233;s avec la messagerie de base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "courrier électronique [SQL Server], informations d'état"
  - "messagerie [SQL Server], informations d'état"
  - "Messagerie de base de données [SQL Server], état du message"
  - "information d'état [messagerie de base de données]"
ms.assetid: eb290f24-b52f-46bc-84eb-595afee6a5f3
caps.latest.revision: 30
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 30
---
# V&#233;rifier l&#39;&#233;tat des messages &#233;lectroniques envoy&#233;s avec la messagerie de base de donn&#233;es
  Cette rubrique explique comment vérifier l'état du message électronique envoyé à l'aide de la messagerie de base de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Avant de commencer :**  
  
-   **Pour afficher l’état du message électronique envoyé à l’aide de la messagerie de base de données, utilisez :**  [Transact-SQL](#TsqlProcedure).  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
 La messagerie de base de données conserve un exemplaire des messages électroniques sortants qu’elle affiche dans les vues **sysmail_allitems**, **sysmail_sentitems**, **sysmail_unsentitems** et **sysmail_faileditems** de la base de données **msdb**. Le programme externe de la messagerie de base de données consigne les activités de l’application dans un journal qu’elle affiche par le biais du journal d’événements des applications Windows et la vue **sysmail_event_log** dans la base de données **msdb**. Pour vérifier l'état d'un message électronique, exécutez une requête sur cette vue. Les messages peuvent présenter quatre états distincts : **sent** (envoyé), **unsent** (non envoyé), **retrying** (nouvel essai) et **failed** (échec).  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour afficher l'état du message électronique envoyé à l'aide de la messagerie de base de données**  
  
1.  Sélectionnez des éléments dans la table **sysmail_allitems**, en spécifiant le ou les messages qui vous intéressent par le biais de l’option **mailitem_id** ou **sent_status**.  
  
2.  Pour vérifier l’état retourné par le programme externe pour les messages électroniques, définissez une jointure allant de **sysmail_allitems** à la vue **sysmail_event_log** dans la colonne **mailitem_id**, comme illustré dans la section suivante.  
  
     Par défaut, le programme externe n'enregistre pas d'informations sur les messages correctement envoyés. Si vous voulez activer le journal pour tous les messages, définissez le niveau de journalisation sur le mode commenté par le biais de la page **Configurer les paramètres du système** de l' **Assistant Configuration de la messagerie de base de données**.  
  
###  <a name="TsqlExample"></a> Exemple (Transact-SQL)  
 L'exemple suivant regroupe des informations sur tous les messages électroniques envoyés à `danw` que le programme externe n'a pas pu envoyer correctement. L'instruction renseigne sur l'objet ainsi que sur la date et l'heure auxquelles la tentative d'envoi du message par le programme externe a échoué, elle indique également le message d'erreur provenant du journal de la messagerie de base de données.  
  
```  
USE msdb ;  
GO  
  
-- Show the subject, the time that the mail item row was last  
-- modified, and the log information.  
-- Join sysmail_faileditems to sysmail_event_log   
-- on the mailitem_id column.  
-- In the WHERE clause list items where danw was in the recipients,  
-- copy_recipients, or blind_copy_recipients.  
-- These are the items that would have been sent  
-- to danw.  
  
SELECT items.subject,  
    items.last_mod_date  
    ,l.description FROM dbo.sysmail_faileditems as items  
INNER JOIN dbo.sysmail_event_log AS l  
    ON items.mailitem_id = l.mailitem_id  
WHERE items.recipients LIKE '%danw%'    
    OR items.copy_recipients LIKE '%danw%'   
    OR items.blind_copy_recipients LIKE '%danw%'  
GO  
```  
  
## Voir aussi  
 [Journal et audits de la messagerie de base de données](../../relational-databases/database-mail/database-mail-log-and-audits.md)  
  
  