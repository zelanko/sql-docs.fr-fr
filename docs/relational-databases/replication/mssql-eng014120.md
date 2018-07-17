---
title: MSSQL_ENG014120 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014120 error
ms.assetid: 6b169a3b-30da-4981-b998-b52d61811572
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 98924053d69f2681c271e9f2ce3d501eccee8aea
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37351501"
---
# <a name="mssqleng014120"></a>MSSQL_ENG014120
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14120|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Impossible de supprimer la base de données de distribution '%s'. La base de données de distribution est associée à un éditeur.|  
  
## <a name="explanation"></a>Explication  
 La base de données de distribution stocke les métadonnées et les données d'historique pour tous les types de réplications, et les transactions pour la réplication transactionnelle. Cette erreur se produit si vous tentez de supprimer une base de données de distribution qui est associée à un ou plusieurs serveurs de publication.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour supprimer une base de données de distribution, vous devez d'abord supprimer l'association entre le serveur de distribution et le serveur de publication. Pour plus d’informations, consultez [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)  
  
  
