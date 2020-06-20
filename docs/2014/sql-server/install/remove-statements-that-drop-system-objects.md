---
title: Supprimer les instructions qui suppriment des objets système | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d9e8fbfd4a436e87cee413d95468ccf5dd36b9dd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059180"
---
# <a name="remove-statements-that-drop-system-objects"></a>Supprimer les instructions qui suppriment des objets système
  Le Conseiller de mise à niveau a détecté des instructions qui suppriment les objets système. Les objets système, y compris les procédures stockées étendues, sont déployés dans une base de données de **ressources** en lecture seule (mssqlsystemresource) et ne peuvent pas être supprimés. Modifiez vos applications pour révoquer ou refuser l'autorisation EXECUTE sur les objets système.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Des instructions telles que DROP TABLE, DROP PROCEDURE et **sp_dropextendedproc** ne peuvent pas être utilisées pour supprimer des objets système parce que ces objets sont déployés dans la base de données des **ressources** en lecture seule.  
  
## <a name="corrective-action"></a>Action corrective  
 Supprimez toutes les instructions qui tentent d'éliminer des objets système de votre application. Modifiez vos applications pour révoquer ou refuser l'autorisation EXECUTE sur les objets système. Vous pouvez également utiliser l'outil Configuration de la surface d'exposition pour désactiver certains de ces objets. Par exemple, la procédure stockée étendue **xp_cmdshell** peut être désactivée ou activée à l'aide de l'outil SAC.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
