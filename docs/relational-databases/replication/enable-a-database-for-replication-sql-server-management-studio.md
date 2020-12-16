---
title: Activer une base de données pour la réplication (SSMS)
description: Découvrez comment activer une base de données pour la réplication à l’aide de SQL Server Management Studio (SSMS) ou de Transact-SQL (T-SQL).
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: a22a2bb5e57bd80fdc868bf461af758831a3c9ec
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97460272"
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>activer une base de données pour la réplication (SQL Server Management Studio)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  
Une base de données est activée implicitement pour la réplication lorsqu'un membre du rôle serveur fixe **sysadmin** crée une publication à l'aide de l'Assistant Nouvelle publication. Un membre du rôle serveur fixe **sysadmin** peut également activer une base de données de manière explicite, afin qu'un membre du rôle de base de données fixe **db_owner** puisse créer une ou plusieurs publications dans la base de données. Pour activer une base de données de manière explicite, utilisez la page **Bases de données de publication** de la boîte de dialogue **Propriétés du serveur de publication - \<Publisher>** . Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
## <a name="using-sql-server-management-studio-ssms"></a>Utilisation de SQL Server Management Studio (SSMS)
  
1.  Dans la page **Bases de données de publication** de la boîte de dialogue **Propriétés du serveur de publication - \<Publisher>** , cochez la case **Transactionnelle** et/ou **Fusionner** pour chaque base de données à répliquer. Sélectionnez **Transactionnel** pour activer la base de données pour la réplication d'instantané.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
## <a name="using-transact-sql-t-sql"></a>Utilisation de Transact-SQL (T-SQL)
Vous pouvez activer une base de données pour la réplication avec le code Transact-SQL suivant : 

```sql
USE master
EXEC sp_replicationdboption @dbname = 'AdventureWorks2017',
@optname = 'publish',
@value = 'true'
GO
```

Pour désactiver la publication, définissez @value = « false ». 
