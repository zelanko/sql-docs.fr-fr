---
title: MSSQLSERVER_611 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 16f0a8de9e55759e78c8fd2cd136ff4db3a677a8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47606197"
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
  
