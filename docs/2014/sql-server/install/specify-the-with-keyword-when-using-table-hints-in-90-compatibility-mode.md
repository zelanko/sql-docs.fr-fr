---
title: Spécifiez le mot clé WITH lors de l’utilisation d’indicateurs de table en mode de compatibilité 90. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- table hints [SQL Server]
ms.assetid: 7636cc85-5155-44db-baf6-df807761adb8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8ffa920d49bac601354d9364dd308c94696def46
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227199"
---
# <a name="specify-the-with-keyword-when-using-table-hints-in-90-compatibility-mode"></a>Spécifier le mot clé WITH lors de l'utilisation d'indicateurs de table en mode de compatibilité 90
  À quelques exceptions près, les indicateurs de table ne sont pris en charge dans la clause FROM d'une requête que s'ils sont spécifiés à l'aide du mot clé WITH. Pour plus d'informations, consultez les rubriques « FROM ([!INCLUDE[tsql](../../includes/tsql-md.md)]) » et « Indicateur de table ([!INCLUDE[tsql](../../includes/tsql-md.md)]) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez les requêtes comportant des indicateurs de table dans la clause FROM en incluant le mot clé WITH avant les indicateurs de table.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
