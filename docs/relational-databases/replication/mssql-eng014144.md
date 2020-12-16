---
description: MSSQL_ENG014144
title: MSSQL_ENG014144 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014144 error
ms.assetid: fdc744d5-530e-48c4-9420-cca032fd482b
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: 6469373e327d4b7eef48819f3f266c36a10a3237
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97469110"
---
# <a name="mssql_eng014144"></a>MSSQL_ENG014144
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Détails du message  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|14144|  
|Source de l’événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Impossible de supprimer l’Abonné '%s'. La base de données de publication '%s' comporte des abonnements qui lui sont associés.|  
  
## <a name="explanation"></a>Explication  
 Une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est configurée en tant qu'Abonné ne peut pas être supprimée du rôle Abonné tant qu'il y a des abonnements actifs configurés pour l'instance.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Supprimez tous les abonnements associés avant d'essayer de modifier l'état de l'Abonné de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
1.  Exécutez [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md) dans la base de données de publication sur le serveur de publication pour rechercher des abonnements.  
  
2.  Exécutez [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md) dans la base de données de publication pour supprimer des abonnements.  

## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
