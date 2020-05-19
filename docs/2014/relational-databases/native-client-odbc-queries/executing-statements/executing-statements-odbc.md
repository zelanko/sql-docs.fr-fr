---
title: Exécution d’instructions (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a367d5ee7def19ffdfd40e24860ebf95f642fae9
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82700429"
---
# <a name="executing-statements-odbc"></a>Exécution d'instructions (ODBC)
  Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client offre plusieurs moyens d’exécuter des instructions SQL dans une [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] base de données :  
  
-   Exécution directe  
  
-   Exécution préparée  
  
 L’exécution directe implique la génération d’une chaîne de caractères contenant une [!INCLUDE[tsql](../../../includes/tsql-md.md)] instruction et son envoi en vue d’une exécution à l’aide de la fonction **SQLExecDirect** . L'exécution préparée implique la génération d'une chaîne de caractères contenant une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] et son exécution en deux étapes. La première étape utilise la fonction [SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360) pour analyser et compiler le plan d’exécution de l’instruction dans le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] . La deuxième étape utilise la fonction **SQLExecute** pour exécuter le plan d’exécution précédemment préparé. Cela permet de réduire la charge d'analyse et de compilation pour chaque exécution. L'exécution préparée est couramment utilisée par les applications pour exécuter de manière répétée la même instruction SQL paramétrable.  
  
 Les exécutions directe et préparée peuvent exécuter une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] unique ou un lot d'instructions SQL, ou elles peuvent appeler une procédure stockée.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Exécution directe](direct-execution.md)  
  
-   [Exécution préparée](prepared-execution.md)  
  
-   [Procédures](procedures.md)  
  
-   [Lots d'instructions](batches-of-statements.md)  
  
-   [Conséquences des options ISO](effects-of-iso-options.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de requêtes &#40;ODBC&#41;](../executing-queries-odbc.md)  
  
  
