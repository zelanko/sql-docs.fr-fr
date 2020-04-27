---
title: Modifier les applications pour qu’elles attendent des valeurs bigint de sysperfinfo. cntr_value | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sysperfinfo
- bigint values [SQL Server]
ms.assetid: b0345303-6e9a-4078-8148-6e1bce207b8c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ced1e07b5423dcdc7c13d24e8528a2b6ac240aaa
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66093959"
---
# <a name="modify-applications-to-expect-bigint-values-from-sysperfinfocntr_value"></a>Modifier les applications pour qu'elles attendent des valeurs bigint de sysperfinfo.cntr_value
  sysperfinfo retourne une `bigint` valeur pour la colonne cntr_value.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez les applications qui utilisent sysperfinfo pour vous assurer qu'elles peuvent traiter les valeurs `bigint` de la colonne cntr_value.  
  
> [!NOTE]  
>  sysperfinfo est une vue de compatibilité. Utilisez de préférence la vue de gestion dynamique sys.dm_os_performance_counter.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
