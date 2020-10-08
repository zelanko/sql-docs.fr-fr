---
title: Objet SqlTriggerContext | Microsoft Docs
description: Dans SQL Server intégration du CLR, la classe SqlTriggerContext fournit des informations de contexte pour un déclencheur, y compris le type d’action et les colonnes modifiées dans l’opération.
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
ms.openlocfilehash: c6f11eda2ef791eb8c987af8d82149507770d47a
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91809157"
---
# <a name="sqltriggercontext-object"></a>Objet SqlTriggerContext
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  La classe **SqlTriggerContext** fournit des informations de contexte sur le déclencheur. Ces informations contextuelles comprennent le type d'action ayant provoqué l'activation du déclencheur, les colonnes qui ont été modifiées dans une opération UPDATE et, dans le cas d'un déclencheur en langage de définition de données (DDL), une structure **EventData** XML qui décrit l'opération de déclenchement. Pour plus d’informations et pour obtenir des exemples d’utilisation de la classe **SqlTriggerContext** , consultez [déclencheurs CLR](/dotnet/framework/data/adonet/sql/clr-triggers).  
  
 Pour plus d’informations, consultez la documentation de référence sur la classe **Microsoft. SqlServer. Server. SqlTriggerContext** dans la documentation du kit de développement logiciel (SDK) .NET Framework.  
  
## <a name="see-also"></a>Voir aussi  
 [Déclencheurs CLR](/dotnet/framework/data/adonet/sql/clr-triggers)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
