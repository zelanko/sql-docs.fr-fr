---
title: Procédures stockées système XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- system stored procedures [SQL Server], XML
- sp_xml_removedocument
- OPENXML statement, system stored procedures
- sp_xml_preparedocument
- XML [SQL Server], system stored procedures
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7f84fbd7435a092abc326f8bb253e5d8565618fc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218135"
---
# <a name="xml-system-stored-procedures"></a>Procédures stockées système XML
  SQL Server propose les procédures stockées système suivantes utilisées en conjonction avec la clause OPENXML :  
  
-   [sp_xml_preparedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql)  
  
-   [sp_xml_removedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql)  
  
 Pour écrire des requêtes à l’aide d’OPENXML, vous devez d’abord créer une représentation interne du document XML en appelant **sp_xml_preparedocument**. Celle-ci renvoie un descripteur vers la représentation interne du document XML. Ce descripteur est ensuite transmis à OPENXML. OPENXML fournit des vues sur les ensembles de lignes du document s'appuyant sur des chemins XPaths. Plus précisément, ces vues correspondent à un modèle de ligne et à un ou plusieurs modèles de colonnes.  
  
> [!NOTE]  
>  Le descripteur du document renvoyé par **sp_xml_preparedocument** reste valide pendant toute la durée de la session.  
  
 Vous pouvez supprimer la représentation interne d’un document XML de la mémoire en appelant la procédure stockée système **sp_xml_removedocument** .  
  
## <a name="see-also"></a>Voir aussi  
 [OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql)   
 [OPENXML &#40;SQL Server&#41;](../xml/openxml-sql-server.md)  
  
  
