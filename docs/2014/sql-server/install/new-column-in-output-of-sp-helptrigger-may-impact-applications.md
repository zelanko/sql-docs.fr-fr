---
title: La nouvelle colonne dans la sortie de sp_helptrigger peut avoir un impact sur les applications | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0b1f5e936843ed84a5c6b88e2f3685e7a4272bc2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012166"
---
# <a name="new-column-in-output-of-sp_helptrigger-may-impact-applications"></a>La nouvelle colonne dans la sortie de sp_helptrigger peut avoir un impact sur des applications
  trigger_schemaias la dernière colonne dans le jeu de résultats retourné par la procédure stockée système sp_helptrigger.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Pour obtenir des informations sur les déclencheurs définis sur une table particulière, interrogez l'affichage catalogue sys.triggers.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Vérifiez l'emploi de sp_helptrigger dans vos applications. Vous devrez peut-être modifier vos applications pour tenir compte de cette colonne supplémentaire. Vous pouvez également utiliser l'affichage catalogue sys.triggers à la place.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
