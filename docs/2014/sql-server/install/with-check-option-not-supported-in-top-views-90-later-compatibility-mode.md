---
title: WITH CHECK OPTION n’est pas pris en charge dans les vues contenant TOP en mode de compatibilité 90 ou ultérieur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- TOP clause
- WITH CHECK OPTION clause
ms.assetid: 1b9581d0-bad9-43e0-b8fc-f32d8a8a04ca
caps.latest.revision: 14
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c8c64ce7395b5ecbb33530672d93817f7938db6d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243991"
---
# <a name="with-check-option-is-not-supported-in-views-that-contain-top-in-90-or-later-compatibility-modes"></a>L'option WITH CHECK OPTION n'est pas prise en charge dans les vues contenant TOP en mode de compatibilité 90 ou ultérieur
  Le Conseiller de mise à niveau a détecté qu'une vue est définie à l'aide du mot clé WITH CHECK OPTION et d'une clause TOP dans l'instruction SELECT de la vue ou dans une vue référencée. Les vues ainsi définies autorisent de manière incorrecte la modification des données par le biais de la vue, ce qui peut produire des résultats imprécis lorsque la base de données est définie en mode de compatibilité 80 ou antérieur. Les données ne peuvent pas être insérées ou mises à jour par le biais d'une vue qui utilise le mot clé WITH CHECK OPTION si la vue ou une vue référencée utilise la clause TOP et que la base de données est définie en mode de compatibilité 90 ou ultérieur.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Lorsque vous effectuez une mise à niveau, les bases de données utilisateur conservent leur mode de compatibilité. Avant de définir la base de données en mode de compatibilité 100 ou ultérieur, modifiez les vues qui utilisent WITH CHECK OPTION et TOP si la modification des données par le biais de la vue est requise. Pour plus d’informations, consultez [sp_dbcmptlevel &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
