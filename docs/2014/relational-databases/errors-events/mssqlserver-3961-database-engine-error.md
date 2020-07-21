---
title: MSSQLSERVER_3961 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3961 (Database Engine error)
ms.assetid: 3bbc6965-6445-400c-940a-2d85b037513f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 63662b3f5b7c058e80090b7b979fb326b0be1d6f
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551534"
---
# <a name="mssqlserver_3961"></a>MSSQLSERVER_3961
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|3961|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|XACT_METADATA_INVALID|  
|Texte du message|La transaction d'isolement d'instantané a échoué dans la base de données '%.*ls' car l'objet auquel l'instruction a eu accès a été modifié par une instruction DDL dans une autre transaction simultanée depuis le début de cette transaction.  Elle est rejetée, car les métadonnées ne font pas l’objet d’une gestion des versions. Une mise à jour simultanée des métadonnées peut provoquer des incohérences si elle est combinée avec un isolement d’instantané.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur peut se produire si vous interrogez des métadonnées avec isolement d’instantané et s’il existe une instruction DDL simultanée qui met à jour les métadonnées faisant l’objet d’un accès avec isolement d’instantané. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge le contrôle de version des métadonnées. Pour cette raison, des restrictions existent sur les opérations DDL qui peuvent être effectuées dans une transaction explicite exécutée avec isolement d’instantané. Par définition, une transaction implicite est une instruction unique qui permet d’appliquer la sémantique de l’isolement d’instantané même avec des instructions DDL. Les instructions DDL suivantes ne sont pas autorisées en isolement d’instantanée après une instruction BEGIN TRANSACTION : ALTER TABLE, CREATE INDEX, CREATE XML INDEX, ALTER INDEX, DROP INDEX, DBCC REINDEX, ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME ou toute instruction DDL CLR (Common Language Runtime). Ces instructions sont autorisées quand vous utilisez l’isolement d’instantané au sein de transactions implicites. Par définition, une transaction implicite est une instruction unique qui permet d’appliquer la sémantique de l’isolement d’instantané même avec des instructions DDL.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Modifiez le niveau d'isolement de capture instantanée en le remplaçant par un niveau d'isolement qui n'est pas de capture instantanée, tel que la lecture validée, avant l'interrogation des métadonnées.  
  
  
