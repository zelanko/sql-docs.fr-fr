---
title: Spécifier le mot clé WITH lors de l’utilisation d’indicateurs de table en mode de compatibilité 90 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- table hints [SQL Server]
ms.assetid: 7636cc85-5155-44db-baf6-df807761adb8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ff2fee26c6f71cc398f8dbacf91f3ad8dbdb3358
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66092162"
---
# <a name="specify-the-with-keyword-when-using-table-hints-in-90-compatibility-mode"></a>Spécifier le mot clé WITH lors de l'utilisation d'indicateurs de table en mode de compatibilité 90
  À quelques exceptions près, les indicateurs de table ne sont pris en charge dans la clause FROM d'une requête que s'ils sont spécifiés à l'aide du mot clé WITH. Pour plus d'informations, consultez les rubriques « FROM ([!INCLUDE[tsql](../../includes/tsql-md.md)]) » et « Indicateur de table ([!INCLUDE[tsql](../../includes/tsql-md.md)]) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez les requêtes comportant des indicateurs de table dans la clause FROM en incluant le mot clé WITH avant les indicateurs de table.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
