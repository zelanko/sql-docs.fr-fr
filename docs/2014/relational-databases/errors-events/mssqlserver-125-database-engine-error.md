---
title: MSSQLSERVER_125 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "125"
helpviewer_keywords:
- 125 (Database Engine error)
ms.assetid: 0f58338d-2ea0-48b8-8a20-c438b0940433
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: c2739d0dace0b1cd1180611d406abb9bc88f56a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043162"
---
# <a name="mssqlserver125"></a>MSSQLSERVER_125
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|125|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique||  
|Texte du message|Les expressions Case ne peuvent être imbriquées que jusqu'au niveau %d.|  
  
## <a name="explanation"></a>Explication  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autorise uniquement 10 niveaux d'imbrication dans les expressions CASE.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Réduisez le niveau des instructions CASE à 10 ou une valeur inférieure.  
  
## <a name="see-also"></a>Voir aussi  
 [CASE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/case-transact-sql)  
  
  
