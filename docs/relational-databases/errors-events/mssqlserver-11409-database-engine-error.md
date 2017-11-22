---
title: MSSQLSERVER_11409 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 11409 (Database Engine error)
ms.assetid: 99b71a1c-a72d-4ca9-9d00-4230c9042ba5
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1c2e15a828cfa41612ed7c2c7eebfbb6eb1aa59d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver11409"></a>MSSQLSERVER_11409
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|11409|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|ALTERCOL_COLSET_DROP|  
|Texte du message|Impossible de supprimer le jeu de colonnes '%.*ls' dans la table '%.\*ls', car celle-ci contient plus de 1 025 colonnes.|  
  
## <a name="explanation"></a>Explication  
Les tables peuvent contenir un maximum de 1 024 colonnes non désignées en tant que colonnes éparses ou calculées. Lorsqu'une table dépasse 1 024 colonnes en raison de colonnes éparses, il convient de définir un jeu de colonnes pour la table en question. La table référencée comporte plus de 1 024 colonnes et vous avez essayé de supprimer le jeu de colonnes.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Étant donné le nombre actuel de colonnes dans la table, vous devez conserver le jeu de colonnes.  
  
Pour supprimer le jeu de colonnes, vous devez au préalable supprimer de la table un nombre de colonnes qui vous permettra de réduire leur nombre à 1 024. Vous pourrez alors supprimer le jeu de colonnes.  
  
