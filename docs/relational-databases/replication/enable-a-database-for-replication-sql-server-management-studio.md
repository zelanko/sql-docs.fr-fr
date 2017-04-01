---
title: "activer une base de donn&#233;es pour la r&#233;plication (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bases de données [réplication SQL Server]"
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# activer une base de donn&#233;es pour la r&#233;plication (SQL Server Management Studio)
  Une base de données est activée implicitement pour la réplication lorsqu'un membre du rôle serveur fixe **sysadmin** crée une publication à l'aide de l'Assistant Nouvelle publication. Un membre de la **sysadmin** rôle serveur fixe permettre également activer explicitement, une base de données pour la réplication afin qu’un membre de la **db_owner** rôle fixe de base de données peut créer une ou plusieurs publications dans la base de données. Pour activer explicitement une base de données, utilisez la **bases de données de Publication** page de le **Propriétés du serveur de publication - \< serveur de publication>** boîte de dialogue. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
### Pour activer une base de données pour la réplication  
  
1.  Sur le **bases de données de Publication** page de le **Propriétés du serveur de publication - \< Publisher>** boîte de dialogue, sélectionnez le **transactionnel** et/ou **fusion** case à cocher pour chaque base de données que vous souhaitez répliquer. Sélectionnez **Transactionnel** pour activer la base de données pour la réplication d'instantané.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  