---
title: Modifier les instructions UPDATETEXT qui lisent et écrivent dans des objets binaires volumineux (BLOB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7bcf5b59aa79e471ef0fc7949990b9782550ec32
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63267723"
---
# <a name="modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs"></a>Modifier les instructions UPDATETEXT qui lisent et écrivent dans des objets blog (binary large object)
  Le Conseiller de mise à niveau a détecté des instructions UPDATETEXT qui lisent et écrivent dans les mêmes objets blob (binary large object) à l'aide du même pointeur de texte. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ne prend pas en charge l'utilisation des pointeurs de texte de cette manière.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Copiez l'objet blob dans une table temporaire ou dans une variable de table, puis réassignez la valeur dans la colonne d'origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
