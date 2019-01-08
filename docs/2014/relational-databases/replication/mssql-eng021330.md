---
title: MSSQL_ENG021330 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021330 error
ms.assetid: e2bb2e21-62a7-4689-b68b-bdfba3fdd985
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 913559815f2157f487db429f2cf9975f68d8da89
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52805795"
---
# <a name="mssqleng021330"></a>MSSQL_ENG021330
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|21330|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Impossible de créer un sous-répertoire dans le répertoire de travail de la réplication.(%1!)|  
  
## <a name="explanation"></a>Explication  
 Cette erreur peut se produire quand un abonnement est initialisé manuellement et qu'il y a un problème de création du répertoire où les scripts de réplication sont stockés. L'erreur peut être due à un problème d'autorisations : lorsqu'un abonnement est initialisé sans utiliser d'instantané, le compte sous lequel le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute sur le serveur de publication doit disposer d'autorisations en écriture sur le dossier d'instantané hébergé sur le serveur de distribution.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez que le chemin d'accès correct a été spécifié pour le dossier d'instantané et que le compte sous lequel le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute sur le serveur de publication a des autorisations suffisantes.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier l’emplacement par défaut des instantanés &#40;SQL Server Management Studio&#41;](specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)   
 [Initialiser un abonnement transactionnel sans instantané](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
