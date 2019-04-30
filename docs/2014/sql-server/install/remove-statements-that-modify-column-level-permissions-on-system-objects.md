---
title: Supprimer les instructions qui modifient les autorisations au niveau des colonnes sur les objets système | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- column-level permissions [SQL Server]
- removed statement permissions [SQL Server]
ms.assetid: 7f4fbbef-2696-4911-903b-63f6d9e4484a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f61990ae0eb35a399a1efca4a5a2cf754892e3d0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63294840"
---
# <a name="remove-statements-that-modify-column-level-permissions-on-system-objects"></a>Supprimer les instructions qui modifient les autorisations de niveau colonne sur les objets système
  Le Conseiller de mise à niveau a détecté des autorisations non standard au niveau des colonnes sur les objets système. Ces changements d'autorisations ne seront pas conservés lors de la mise à niveau. De plus, les autorisations au niveau des colonnes sur les objets système ne sont plus prises en charge. Supprimez les instructions de vos applications qui définissent des autorisations au niveau des colonnes sur les objets système.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Supprimez de votre application les instructions qui accordent, refusent ou révoquent des autorisations au niveau des colonnes sur les objets système.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
