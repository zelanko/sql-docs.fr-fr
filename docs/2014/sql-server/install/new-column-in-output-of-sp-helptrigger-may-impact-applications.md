---
title: Nouvelle colonne dans la sortie de sp_helptrigger peut avoir un impact sur les applications | Documents Microsoft
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
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2d62b9b9546fa113557bf962d68876d8c55a71ef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042601"
---
# <a name="new-column-in-output-of-sphelptrigger-may-impact-applications"></a>La nouvelle colonne dans la sortie de sp_helptrigger peut avoir un impact sur des applications
  trigger_schemaias la dernière colonne du jeu de résultats retournée par le système sp_helptrigger de procédure stockée.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Pour obtenir des informations sur les déclencheurs définis sur une table particulière, interrogez l'affichage catalogue sys.triggers.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Vérifiez l'emploi de sp_helptrigger dans vos applications. Vous devrez peut-être modifier vos applications pour tenir compte de cette colonne supplémentaire. Vous pouvez également utiliser l'affichage catalogue sys.triggers à la place.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
