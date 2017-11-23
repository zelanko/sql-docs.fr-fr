---
title: Les Modules SQL | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL modules [ODBC]
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], modules
- modules [ODBC]
- SQL statements [ODBC], modules
ms.assetid: 07551472-87ee-4765-951f-1364ed32f0c0
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ee18719a325135af480645de3446042339a44f8b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sql-modules"></a>Modules SQL
La seconde technique pour l’envoi d’instructions SQL au SGBD est via les modules. En résumé, un module se compose d’un groupe de procédures qui sont appelées à partir de l’hôte de langage de programmation. Chaque procédure contient une instruction SQL unique, et les données sont transmises vers et à partir de la procédure de paramètres.  
  
 Un module peut être considéré comme une bibliothèque d’objets qui est liée au code d’application. Toutefois, exactement comment les procédures et le reste de l’application sont liés sont dépendant de l’implémentation. Par exemple, les procédures peuvent être compilés en code objet et directement liés au code de l’application, peut être compilés et stockés dans le SGBD et les appels pour accéder aux identificateurs de plan placés dans le code d’application, ou ils pourraient être interprétés au moment de l’exécution.  
  
 Le principal avantage des modules est séparer correctement les instructions SQL à partir du langage de programmation. En théorie, il doit être possible de modifier une sans modifier l’autre et simplement les réassocier.
