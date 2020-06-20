---
title: Activer une base de données pour la réplication (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 307d52e24187e35c1c30f609facd13bfad569216
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010735"
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>activer une base de données pour la réplication (SQL Server Management Studio)
   Une base de données est activée implicitement pour la réplication lorsqu’un membre du rôle serveur fixe **sysadmin** crée une publication à l’aide de l’Assistant Nouvelle publication. Un membre du rôle serveur fixe **sysadmin** peut également activer une base de données de manière explicite, afin qu'un membre du rôle de base de données fixe **db_owner** puisse créer une ou plusieurs publications dans la base de données. Pour activer une base de données de manière explicite, utilisez la page **bases de données de publication** de la boîte de dialogue Propriétés du serveur de publication ** \<Publisher> -** . Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Create a Publication](publish/create-a-publication.md).  
  
### <a name="to-enable-a-database-for-replication"></a>Pour activer une base de données pour la réplication  
  
1.  Dans la page **bases de données de publication** de la boîte de dialogue Propriétés du serveur de publication **- \<Publisher> ** , cochez la case **transactionnelle** et/ou **fusionner** pour chaque base de données que vous souhaitez répliquer. Sélectionnez **Transactionnel** pour activer la base de données pour la réplication d'instantané.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
