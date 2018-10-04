---
title: Modifier les applications attendent des valeurs bigint de sysperfinfo.cntr_value | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- sysperfinfo
- bigint values [SQL Server]
ms.assetid: b0345303-6e9a-4078-8148-6e1bce207b8c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e4f7945a5657cefb43af402523a6aee3e12eb63a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137529"
---
# <a name="modify-applications-to-expect-bigint-values-from-sysperfinfocntrvalue"></a>Modifier les applications pour qu'elles attendent des valeurs bigint de sysperfinfo.cntr_value
  sysperfinfo retourne une `bigint` valeur pour la colonne cntr_value.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez les applications qui utilisent sysperfinfo pour vous assurer qu'elles peuvent traiter les valeurs `bigint` de la colonne cntr_value.  
  
> [!NOTE]  
>  sysperfinfo est une vue de compatibilité. Utilisez de préférence la vue de gestion dynamique sys.dm_os_performance_counter.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
