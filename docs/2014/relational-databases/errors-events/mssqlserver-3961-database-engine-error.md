---
title: MSSQLSERVER_3961 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 3961 (Database Engine error)
ms.assetid: 3bbc6965-6445-400c-940a-2d85b037513f
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 19e0e49ea3b9648600de6974d227fad3d25a728e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426408"
---
# <a name="mssqlserver3961"></a>MSSQLSERVER_3961
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|3961|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|XACT_METADATA_INVALID|  
|Texte du message|La transaction d'isolement d'instantané a échoué dans la base de données '%.*ls' car l'objet auquel l'instruction a eu accès a été modifié par une instruction DDL dans une autre transaction simultanée depuis le début de cette transaction.  Cela est interdit, car les métadonnées n'ont pas de version. Une mise à jour simultanée des métadonnées peut provoquer des incohérences si elle est mélangée à un isolement d'instantané.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur peut se produire si vous interrogez les métadonnées en isolement d'instantané et s'il existe une instruction DDL simultanée qui met à jour les métadonnées accessibles en isolement d'instantané. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge le contrôle de version des métadonnées. Pour cette raison, il existe des restrictions sur les opérations DDL pouvant être effectuées dans une transaction explicite exécutée en isolement d'instantané. Par définition, une transaction implicite est une instruction unique qui permet d'appliquer la sémantique de l'isolement d'instantané, même avec des instructions DDL. Les instructions DDL suivantes ne sont pas autorisées avec le niveau d'isolation d'instantané après une instruction BEGIN TRANSACTION : ALTER TABLE, CREATE INDEX, CREATE XML INDEX, ALTER INDEX, DROP INDEX, DBCC REINDEX, ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME ou toute autre instruction DDL utilisant le langage CLR (Common Language Runtime). Ces instructions sont autorisées lorsque vous avez recours à l'isolation d'instantané au sein des transactions implicites. Par définition, une transaction implicite est une instruction unique qui permet d'appliquer la sémantique de l'isolement d'instantané, même avec des instructions DDL.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Modifiez le niveau d'isolement de capture instantanée en le remplaçant par un niveau d'isolement qui n'est pas de capture instantanée, tel que la lecture validée, avant l'interrogation des métadonnées.  
  
  
