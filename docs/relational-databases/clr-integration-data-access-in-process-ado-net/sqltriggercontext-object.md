---
title: Objet SqlTriggerContext | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
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
ms.openlocfilehash: 7eff223dc255d5a44706e7b97f73963863428ae8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47661697"
---
# <a name="sqltriggercontext-object"></a>Objet SqlTriggerContext
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La classe **SqlTriggerContext** fournit des informations de contexte sur le déclencheur. Ces informations contextuelles comprennent le type d'action ayant provoqué l'activation du déclencheur, les colonnes qui ont été modifiées dans une opération UPDATE et, dans le cas d'un déclencheur en langage de définition de données (DDL), une structure **EventData** XML qui décrit l'opération de déclenchement. Pour plus d’informations et obtenir des exemples montrant comment utiliser le **SqlTriggerContext** de classe, consultez [déclencheurs CLR](http://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c).  
  
 Pour plus d'informations, consultez la documentation de référence sur la classe **Microsoft.SqlServer.Server.SqlTriggerContext** dans la documentation du Kit de développement logiciel (SDK) .NET Framework.  
  
## <a name="see-also"></a>Voir aussi  
 [Déclencheurs CLR](http://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
