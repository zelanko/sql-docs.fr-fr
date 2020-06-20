---
title: Modifier les instructions UPDATETEXT qui lisent et écrivent dans des objets BLOB (Binary Large Objects) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 061e7bad0bae5a74d103406265ad79195f79f7db
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059206"
---
# <a name="modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs"></a>Modifier les instructions UPDATETEXT qui lisent et écrivent dans des objets blog (binary large object)
  Le Conseiller de mise à niveau a détecté des instructions UPDATETEXT qui lisent et écrivent dans les mêmes objets blob (binary large object) à l'aide du même pointeur de texte. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ne prend pas en charge l'utilisation des pointeurs de texte de cette manière.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Copiez l'objet blob dans une table temporaire ou dans une variable de table, puis réassignez la valeur dans la colonne d'origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
