---
title: "La libération d’un descripteur d’instruction ODBC | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- statement handles [ODBC]
- handles [ODBC], statement
- freeing statement handles [ODBC]
ms.assetid: ee18e2f1-2690-4cc1-9e5c-e20244e5d480
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b33d262c846d9ef8a41bf9440802664ac7d4b75f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="freeing-a-statement-handle-odbc"></a>La libération d’un descripteur d’instruction ODBC
Comme mentionné précédemment, il est plus efficace de réutiliser des instructions à to les supprimer et d’allouer de nouveaux. Avant d’exécuter une nouvelle instruction SQL sur une instruction, les applications doivent être sûr que les paramètres actuels de l’instruction sont appropriées. Cela inclut les attributs d'instruction, les liaisons de paramètres et les liaisons de jeux de résultats. En règle générale, les paramètres et jeux de résultats pour l’ancienne instruction SQL doivent être indépendants (en appelant **SQLFreeStmt** avec les options SQL_RESET_PARAMS et SQL_UNBIND) et détente pour la nouvelle instruction SQL.  
  
 Lorsque l’application a terminé à l’aide de l’instruction, il appelle **SQLFreeHandle** pour libérer de l’instruction. Après la libération de l’instruction, il s’agit d’une erreur de programmation d’application à utiliser le handle de l’instruction dans un appel à une fonction ODBC ; Cette opération donc des conséquences non défini mais probablement irrécupérable.  
  
 Lorsque **SQLFreeHandle** est appelée, les versions de pilote la structure utilisée pour stocker des informations sur l’instruction.  
  
 **SQLDisconnect** libère automatiquement toutes les instructions sur une connexion.

