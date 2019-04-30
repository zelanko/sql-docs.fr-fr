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
ms.openlocfilehash: 835e5fae4717748664affef9491ea1f7eeaec8b2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199925"
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
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
