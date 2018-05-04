---
title: La libération d’un descripteur d’instruction ODBC | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- statement handles [ODBC]
- handles [ODBC], statement
- freeing statement handles [ODBC]
ms.assetid: ee18e2f1-2690-4cc1-9e5c-e20244e5d480
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6c0e8e41468636254288186c5b9f810514c7fdee
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="freeing-a-statement-handle-odbc"></a>La libération d’un descripteur d’instruction ODBC
Comme mentionné précédemment, il est plus efficace de réutiliser des instructions à to les supprimer et d’allouer de nouveaux. Avant d’exécuter une nouvelle instruction SQL sur une instruction, les applications doivent être sûr que les paramètres actuels de l’instruction sont appropriées. Cela inclut les attributs d'instruction, les liaisons de paramètres et les liaisons de jeux de résultats. En règle générale, les paramètres et jeux de résultats pour l’ancienne instruction SQL doivent être indépendants (en appelant **SQLFreeStmt** avec les options SQL_RESET_PARAMS et SQL_UNBIND) et détente pour la nouvelle instruction SQL.  
  
 Lorsque l’application a terminé à l’aide de l’instruction, il appelle **SQLFreeHandle** pour libérer de l’instruction. Après la libération de l’instruction, il s’agit d’une erreur de programmation d’application à utiliser le handle de l’instruction dans un appel à une fonction ODBC ; Cette opération donc des conséquences non défini mais probablement irrécupérable.  
  
 Lorsque **SQLFreeHandle** est appelée, les versions de pilote la structure utilisée pour stocker des informations sur l’instruction.  
  
 **SQLDisconnect** libère automatiquement toutes les instructions sur une connexion.
