---
title: Supprimer les instructions qui modifient les objets système | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- direct system catalog updates [SQL Server]
- system catalogs [SQL Server]
ms.assetid: 221b46c2-c27e-4df8-bd8c-8b990d6d5e98
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 526181bc4bf7ab81df2eaa25f19e7627c9b7af10
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059162"
---
# <a name="remove-statements-that-modify-system-objects"></a>Supprimer les instructions qui modifient les objets système
  Le Conseiller de mise à niveau a détecté des instructions qui mettent à jour le catalogue système. Les mises à jour directes du catalogue système ne sont pas autorisées. Modifiez vos scripts SQL pour utiliser des API officielles et documentées.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Les mises à jour directes du catalogue système ne sont pas autorisées. Toute tentative à cet égard génère l'erreur suivante :  
  
 `Server: Msg 259, Level 16, State 1, Line 1`  
  
 `Ad hoc updates to system catalogs are not allowed.`  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez vos scripts SQL pour utiliser des API officielles et documentées. Par exemple, utilisez ALTER DATABASE *database_name* SET EMERGENCY plutôt que d'exécuter une instruction UPDATE sur la table système **sysdatabases** .  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
