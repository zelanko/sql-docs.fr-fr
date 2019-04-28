---
title: SqlTriggerContext Object | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlTriggerContext object
- triggers [CLR integration]
- context [CLR integration]
ms.assetid: 472a2d0b-64ae-4877-8f11-a5620aa698b7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: df384324ba16aac03a4c889cf4f3959c23374510
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874692"
---
# <a name="sqltriggercontext-object"></a>Objet SqlTriggerContext
  La classe `SqlTriggerContext` fournit des informations de contexte sur le déclencheur. Ces informations contextuelles comprennent le type d'action ayant provoqué l'activation du déclencheur, les colonnes qui ont été modifiées dans une opération UPDATE et, dans le cas d'un déclencheur en langage de définition de données (DDL), une structure `EventData` XML qui décrit l'opération de déclenchement. Pour plus d’informations et obtenir des exemples montrant comment utiliser le `SqlTriggerContext` de classe, consultez [déclencheurs CLR](../../database-engine/dev-guide/clr-triggers.md).  
  
 Pour plus d’informations, consultez la `Microsoft.SqlServer.Server.SqlTriggerContext` classe documentation de référence dans la documentation du SDK de .NET Framework.  
  
## <a name="see-also"></a>Voir aussi  
 [Déclencheurs CLR](../../database-engine/dev-guide/clr-triggers.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
