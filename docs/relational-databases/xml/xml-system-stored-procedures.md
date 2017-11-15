---
title: "Procédures stockées système XML | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system stored procedures [SQL Server], XML
- sp_xml_removedocument
- OPENXML statement, system stored procedures
- sp_xml_preparedocument
- XML [SQL Server], system stored procedures
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
caps.latest.revision: "27"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 54e74e7b2fcb6660785ecaf62a4c829a5e7722af
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="xml-system-stored-procedures"></a>Procédures stockées système XML
  SQL Server propose les procédures stockées système suivantes utilisées en conjonction avec la clause OPENXML :  
  
-   [sp_xml_preparedocument &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql.md)  
  
-   [sp_xml_removedocument &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql.md)  
  
 Pour écrire des requêtes à l’aide d’OPENXML, vous devez d’abord créer une représentation interne du document XML en appelant **sp_xml_preparedocument**. Celle-ci renvoie un descripteur vers la représentation interne du document XML. Ce descripteur est ensuite transmis à OPENXML. OPENXML fournit des vues sur les ensembles de lignes du document s'appuyant sur des chemins XPaths. Plus précisément, ces vues correspondent à un modèle de ligne et à un ou plusieurs modèles de colonnes.  
  
> [!NOTE]  
>  Le descripteur du document renvoyé par **sp_xml_preparedocument** reste valide pendant toute la durée de la session.  
  
 Vous pouvez supprimer la représentation interne d’un document XML de la mémoire en appelant la procédure stockée système **sp_xml_removedocument** .  
  
## <a name="see-also"></a>Voir aussi  
 [OPENXML &#40;Transact-SQL&#41;](../../t-sql/functions/openxml-transact-sql.md)   
 [OPENXML &#40;SQL Server&#41;](../../relational-databases/xml/openxml-sql-server.md)  
  
  
