---
title: Supprimer les instructions qui modifient les autorisations au niveau des colonnes sur les objets système | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- column-level permissions [SQL Server]
- removed statement permissions [SQL Server]
ms.assetid: 7f4fbbef-2696-4911-903b-63f6d9e4484a
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3bb611f4ccad6f6c5d89680857d4e96eabf79611
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052338"
---
# <a name="remove-statements-that-modify-column-level-permissions-on-system-objects"></a>Supprimer les instructions qui modifient les autorisations de niveau colonne sur les objets système
  Le Conseiller de mise à niveau a détecté des autorisations non standard au niveau des colonnes sur les objets système. Ces changements d'autorisations ne seront pas conservés lors de la mise à niveau. De plus, les autorisations au niveau des colonnes sur les objets système ne sont plus prises en charge. Supprimez les instructions de vos applications qui définissent des autorisations au niveau des colonnes sur les objets système.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Supprimez de votre application les instructions qui accordent, refusent ou révoquent des autorisations au niveau des colonnes sur les objets système.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
