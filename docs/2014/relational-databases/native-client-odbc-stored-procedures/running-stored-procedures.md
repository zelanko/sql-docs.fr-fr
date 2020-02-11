---
title: Exécution de procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- stored procedures [ODBC], running
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], executing
ms.assetid: 866b6dd3-2acd-4dfb-aeca-a0352b2d4c6a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6bdf66ed9214a151886caedcf2247935a07f7811
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206730"
---
# <a name="running-stored-procedures"></a>Exécution des procédures stockées
  Une procédure stockée est un objet exécutable stocké dans une base de données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]permet  
  
-   Procédures stockées :  
  
     une ou plusieurs instructions SQL précompilées en une seule procédure exécutable.  
  
-   Les procédures stockées étendues :  
  
     Les DLL C ou C++ écrites dans l'API SQL Server Open Data Services pour les procédures stockées étendues. L'API Open Data Services étend les fonctions des procédures stockées pour inclure un code C ou C++.  
  
 Lorsque vous exécutez des instructions, l'appel d'une procédure stockée sur la source de données (au lieu d'exécuter ou de préparer directement une instruction dans l'application cliente) peut fournir les éléments suivants :  
  
-   Performances accrues  
  
     Les instructions SQL sont analysées et compilées lorsque les procédures sont créées. Cette charge est ensuite enregistrée lorsque les procédures sont exécutées.  
  
-   Charge réseau réduite  
  
     L'exécution d'une procédure au lieu d'envoyer des requêtes complexes à travers le réseau peut réduire le trafic réseau. Si une application ODBC utilise la syntaxe ODBC {CALL} pour exécuter une procédure stockée, le pilote ODBC procède à des optimisations supplémentaires qui éliminent le besoin de convertir les données des paramètres.  
  
-   Cohérence supérieure  
  
     Si les règles d'une organisation sont implémentées dans une ressource centrale, telle qu'une procédure stockée, elles peuvent être codées, testées et déboguées une fois. Les programmeurs individuels peuvent utiliser ensuite les procédures stockées testées au lieu de développer leurs propres implémentations.  
  
-   Exactitude supérieure  
  
     Comme les procédures stockées sont développées habituellement par des programmeurs expérimentés, elles tendent à être plus efficaces et à comporter moins d'erreurs qu'un code développé plusieurs fois par des programmeurs aux niveaux de compétence variables.  
  
-   Fonctionnalités supplémentaires  
  
     Les procédures stockées étendues peuvent utiliser les fonctionnalités C et C++ non disponibles dans les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
     Pour obtenir un exemple d’appel d’une procédure stockée, consultez [traiter les codes de retour et les paramètres de sortie &#40;ODBC&#41;](../native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Appel d'une procédure stockée](calling-a-stored-procedure.md)  
  
-   [Traitement par lot des appels aux procédures stockées](batching-stored-procedure-calls.md)  
  
-   [Traitement des résultats des procédures stockées](processing-stored-procedure-results.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;&#41;ODBC](../native-client/odbc/sql-server-native-client-odbc.md)   
 [Rubriques de procédures relatives à l’exécution de procédures stockées &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)  
  
  
