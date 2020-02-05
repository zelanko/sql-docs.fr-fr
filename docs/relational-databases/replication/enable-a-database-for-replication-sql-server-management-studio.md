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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 03c532b6dcb0ad55a39afdae71f6879d7bc327cc
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76288376"
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>activer une base de données pour la réplication (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  
Une base de données est activée implicitement pour la réplication lorsqu'un membre du rôle serveur fixe **sysadmin** crée une publication à l'aide de l'Assistant Nouvelle publication. Un membre du rôle serveur fixe **sysadmin** peut également activer une base de données de manière explicite, afin qu'un membre du rôle de base de données fixe **db_owner** puisse créer une ou plusieurs publications dans la base de données. Pour activer une base de données de manière explicite, utilisez la page **Bases de données de publication** de la boîte de dialogue **Propriétés du serveur de publication - \<Serveur_de_publication>** . Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
## <a name="using-sql-server-management-studio-ssms"></a>Utilisation de SQL Server Management Studio (SSMS)
  
1.  Dans la page **Bases de données de publication** de la boîte de dialogue **Propriétés du serveur de publication - \<Serveur_de_publication>** , cochez la case **Transactionnelle** et/ou **Fusionner** pour chaque base de données à répliquer. Sélectionnez **Transactionnel** pour activer la base de données pour la réplication d'instantané.  
  
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
