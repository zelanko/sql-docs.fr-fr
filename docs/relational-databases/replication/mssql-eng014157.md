---
description: MSSQL_ENG014157
title: MSSQL_ENG014157 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014157 error
ms.assetid: 1a0890cf-d977-43e0-a2ba-9c5ff1a8f856
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 341f6877c03314cc79a1357a70f0e3f1a109bbe5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470232"
---
# <a name="mssql_eng014157"></a>MSSQL_ENG014157
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Détails du message  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|14157|  
|Source de l’événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|L'abonnement créé par l'Abonné '%1!' à la publication '%2!' a expiré et a été supprimé.|  
  
## <a name="explanation"></a>Explication  
 Un Abonné doit effectuer une synchronisation avec le serveur de publication dans les délais définis par la période de rétention de la publication. Si un Abonné n'effectue pas la synchronisation dans cette période, l'abonnement expire. Pour plus d’informations, voir [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 L'abonnement doit être recréé et initialisé avant que l'Abonné ne recommence à recevoir des modifications de données :  
  
-   Pour plus d’informations sur la création d’abonnements, consultez [S’abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md).  
  
-   Pour plus d’informations sur l’initialisation des abonnements, consultez [Initialiser un abonnement](../../relational-databases/replication/initialize-a-subscription.md).  
  
 Si la base de données d'abonnement contient des modifications qui n'ont pas été synchronisées avec le serveur de publication, vous pouvez utiliser l' [tablediff Utility](../../tools/tablediff-utility.md) pour identifier les lignes qui sont différentes dans les bases de publication et les bases d'abonnement.  
  
 Vous pouvez augmenter la période de rétention de la publication afin d'empêcher l'expiration des abonnements. Faites preuve de la plus grande vigilance lors de la définition d'une valeur élevée car plus le nombre de données et de métadonnées stockées est important, moins les performances sont bonnes. Pour plus d’informations, voir [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
