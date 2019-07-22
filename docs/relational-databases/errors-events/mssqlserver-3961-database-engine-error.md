---
title: MSSQLSERVER_3961 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3961 (Database Engine error)
ms.assetid: 3bbc6965-6445-400c-940a-2d85b037513f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9b89aab7a129aec5fcae840086b140f6975a8c99
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68043507"
---
# <a name="mssqlserver3961"></a>MSSQLSERVER_3961
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
Cette erreur peut se produire si vous interrogez les métadonnées en isolement d'instantané et s'il existe une instruction DDL simultanée qui met à jour les métadonnées accessibles en isolement d'instantané. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge le contrôle de version des métadonnées. Pour cette raison, il existe des restrictions sur les opérations DDL pouvant être effectuées dans une transaction explicite exécutée en isolement d'instantané. Par définition, une transaction implicite est une instruction unique qui permet d'appliquer la sémantique de l'isolement d'instantané, même avec des instructions DDL. Les instructions DDL suivantes ne sont pas autorisées en isolement d’instantanée après une instruction BEGIN TRANSACTION : ALTER TABLE, CREATE INDEX, CREATE XML INDEX, ALTER INDEX, DROP INDEX, DBCC REINDEX, ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME ou toute instruction DDL CLR (Common Language Runtime). Ces instructions sont autorisées lorsque vous avez recours à l'isolation d'instantané au sein des transactions implicites. Par définition, une transaction implicite est une instruction unique qui permet d'appliquer la sémantique de l'isolement d'instantané, même avec des instructions DDL.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Modifiez le niveau d'isolement de capture instantanée en le remplaçant par un niveau d'isolement qui n'est pas de capture instantanée, tel que la lecture validée, avant l'interrogation des métadonnées.  
  
