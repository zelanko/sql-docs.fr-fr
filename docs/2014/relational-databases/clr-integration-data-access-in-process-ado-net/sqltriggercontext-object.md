---
title: SqlTriggerContext, objet | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SqlTriggerContext object
- triggers [CLR integration]
- context [CLR integration]
ms.assetid: 472a2d0b-64ae-4877-8f11-a5620aa698b7
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dbdaefa1e3c5e1c5a53cd6179f4b96320434dbdf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040177"
---
# <a name="sqltriggercontext-object"></a>Objet SqlTriggerContext
  La classe `SqlTriggerContext` fournit des informations de contexte sur le déclencheur. Ces informations contextuelles comprennent le type d'action ayant provoqué l'activation du déclencheur, les colonnes qui ont été modifiées dans une opération UPDATE et, dans le cas d'un déclencheur en langage de définition de données (DDL), une structure `EventData` XML qui décrit l'opération de déclenchement. Pour plus d’informations et des exemples montrant comment utiliser les `SqlTriggerContext` de classe, consultez [déclencheurs CLR](../../database-engine/dev-guide/clr-triggers.md).  
  
 Pour plus d’informations, consultez la `Microsoft.SqlServer.Server.SqlTriggerContext` classe documentation de référence dans la documentation du Kit de développement logiciel .NET Framework.  
  
## <a name="see-also"></a>Voir aussi  
 [Déclencheurs CLR](../../database-engine/dev-guide/clr-triggers.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
