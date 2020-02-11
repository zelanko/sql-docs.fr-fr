---
title: MSSQLSERVER_11409 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 11409 (Database Engine error)
ms.assetid: 99b71a1c-a72d-4ca9-9d00-4230c9042ba5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bc894e8b7a058e1f85f4068c9de7eb3a91a62721
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62870170"
---
# <a name="mssqlserver_11409"></a>MSSQLSERVER_11409
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|11409|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|ALTERCOL_COLSET_DROP|  
|Texte du message|Impossible de supprimer le jeu de colonnes '%.*ls' dans la table '%.\*ls', car celle-ci contient plus de 1 025 colonnes.|  
  
## <a name="explanation"></a>Explication  
 Les tables peuvent contenir un maximum de 1 024 colonnes non désignées en tant que colonnes éparses ou calculées. Lorsqu'une table dépasse 1 024 colonnes en raison de colonnes éparses, il convient de définir un jeu de colonnes pour la table en question. La table référencée comporte plus de 1 024 colonnes et vous avez essayé de supprimer le jeu de colonnes.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Étant donné le nombre actuel de colonnes dans la table, vous devez conserver le jeu de colonnes.  
  
 Pour supprimer le jeu de colonnes, vous devez au préalable supprimer de la table un nombre de colonnes qui vous permettra de réduire leur nombre à 1 024. Vous pourrez alors supprimer le jeu de colonnes.  
  
  
