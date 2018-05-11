---
title: MSSQLSERVER_611 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d32d67f02af9c377720480ec27dd7e3078c069a1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver611"></a>MSSQLSERVER_611
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|611|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|VAR_SIZE_TOO_BIG|  
|Texte du message|Impossible d'insérer ou de mettre à jour une ligne, car la taille totale de colonne variable, surcharge comprise, dépasse la limite de %d octets.|  
  
## <a name="explanation"></a>Explication  
La taille de colonne variable maximale est supérieure à celle autorisée par le schéma. L'erreur 611 est retournée lorsque la colonne variable est supérieure à la limite dans le cas où le format de stockage VarDecimal est activé, ou lorsque la taille de la colonne variable est supérieure à la limite autorisée dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour un enregistrement de données compressé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Réduisez la taille de l'enregistrement.  
  
