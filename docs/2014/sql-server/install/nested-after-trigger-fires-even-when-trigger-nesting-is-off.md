---
title: Un déclencheur AFTER imbriqué déclenche même si imbrication du déclencheur est désactivée (OFF) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, nested
- nested triggers option
- triggers [SQL Server], nested
ms.assetid: 94d72960-676e-40d9-81bc-08bffe778110
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0675c412d753a1ce60fa41c7ced40528b3c58f75
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66093831"
---
# <a name="nested-after-trigger-fires-even-when-trigger-nesting-is-off"></a>Un déclencheur AFTER imbriqué est exécuté même lorsque l'imbrication du déclencheur est OFF
  Le Conseiller de mise à niveau a détecté un déclencheur AFTER imbriqué à l'intérieur d'un déclencheur INSTEAD OF défini sur une ou plusieurs tables. Les déclencheurs imbriqués AFTER peuvent s'exécuter même lorsque l'option de configuration du serveur `nested triggers` a la valeur 0.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Le premier déclencheur AFTER imbriqué dans un déclencheur INSTEAD OF se déclenche même si l'option de configuration du serveur `nested triggers` est définie à 0. Toutefois, les déclencheurs AFTER suivants ne se déclenchent pas sous ce paramètre.  
  
## <a name="corrective-action"></a>Action corrective  
 Contrôlez les déclencheurs imbriqués de vos applications afin de déterminer si ces applications sont toujours conformes aux règles d'entreprise relatives à ce nouveau comportement lorsque l'option de configuration du serveur de `nested triggers` est définie à 0, puis effectuez les modifications nécessaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
