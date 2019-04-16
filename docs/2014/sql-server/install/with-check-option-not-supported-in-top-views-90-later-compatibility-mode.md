---
title: WITH CHECK OPTION n’est pas pris en charge dans les vues contenant TOP en mode de compatibilité 90 ou ultérieur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- TOP clause
- WITH CHECK OPTION clause
ms.assetid: 1b9581d0-bad9-43e0-b8fc-f32d8a8a04ca
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0b91a4b5bb42ebc86e72d532b9f8d210fbba5506
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2019
ms.locfileid: "59583212"
---
# <a name="with-check-option-is-not-supported-in-views-that-contain-top-in-90-or-later-compatibility-modes"></a>L'option WITH CHECK OPTION n'est pas prise en charge dans les vues contenant TOP en mode de compatibilité 90 ou ultérieur
  Le Conseiller de mise à niveau a détecté qu'une vue est définie à l'aide du mot clé WITH CHECK OPTION et d'une clause TOP dans l'instruction SELECT de la vue ou dans une vue référencée. Les vues ainsi définies autorisent de manière incorrecte la modification des données par le biais de la vue, ce qui peut produire des résultats imprécis lorsque la base de données est définie en mode de compatibilité 80 ou antérieur. Les données ne peuvent pas être insérées ou mises à jour par le biais d'une vue qui utilise le mot clé WITH CHECK OPTION si la vue ou une vue référencée utilise la clause TOP et que la base de données est définie en mode de compatibilité 90 ou ultérieur.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Lorsque vous effectuez une mise à niveau, les bases de données utilisateur conservent leur mode de compatibilité. Avant de définir la base de données en mode de compatibilité 100 ou ultérieur, modifiez les vues qui utilisent WITH CHECK OPTION et TOP si la modification des données par le biais de la vue est requise. Pour plus d’informations, consultez [sp_dbcmptlevel &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
