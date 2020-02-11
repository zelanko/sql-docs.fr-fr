---
title: Libération d’un descripteur d’instruction ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- statement handles [ODBC]
- handles [ODBC], statement
- freeing statement handles [ODBC]
ms.assetid: ee18e2f1-2690-4cc1-9e5c-e20244e5d480
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 638cf9fb3c7af73130cf1413559b9baee2a354c1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069780"
---
# <a name="freeing-a-statement-handle-odbc"></a>Libération d’un handle d’instruction dans ODBC
Comme mentionné précédemment, il est plus efficace de réutiliser des instructions que de les supprimer et d’en allouer de nouvelles. Avant d’exécuter une nouvelle instruction SQL sur une instruction, les applications doivent s’assurer que les paramètres de l’instruction actuelle sont appropriés. Cela inclut les attributs d'instruction, les liaisons de paramètres et les liaisons de jeux de résultats. En règle générale, les paramètres et les jeux de résultats de l’ancienne instruction SQL doivent être indépendants (en appelant **SQLFreeStmt** avec les options SQL_RESET_PARAMS et SQL_UNBIND) et reliées pour la nouvelle instruction SQL.  
  
 Lorsque l’application a terminé d’utiliser l’instruction, elle appelle **SQLFreeHandle** pour libérer l’instruction. Après la libération de l’instruction, il s’agit d’une erreur de programmation d’application pour utiliser le handle de l’instruction dans un appel à une fonction ODBC. Cela a des conséquences non définies mais probablement irrécupérables.  
  
 Quand **SQLFreeHandle** est appelé, le pilote libère la structure utilisée pour stocker des informations sur l’instruction.  
  
 **SQLDisconnect** libère automatiquement toutes les instructions sur une connexion.
