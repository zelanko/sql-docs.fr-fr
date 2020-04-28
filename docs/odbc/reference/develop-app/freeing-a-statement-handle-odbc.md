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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 01e4cb46edf1b1a0f1c6dfaa0273c1dd5b392686
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305614"
---
# <a name="freeing-a-statement-handle-odbc"></a>Libération d’un handle d’instruction dans ODBC
Comme mentionné précédemment, il est plus efficace de réutiliser des instructions que de les supprimer et d’en allouer de nouvelles. Avant d’exécuter une nouvelle instruction SQL sur une instruction, les applications doivent s’assurer que les paramètres de l’instruction actuelle sont appropriés. Cela inclut les attributs d'instruction, les liaisons de paramètres et les liaisons de jeux de résultats. En règle générale, les paramètres et les jeux de résultats de l’ancienne instruction SQL doivent être indépendants (en appelant **SQLFreeStmt** avec les options SQL_RESET_PARAMS et SQL_UNBIND) et reliées pour la nouvelle instruction SQL.  
  
 Lorsque l’application a terminé d’utiliser l’instruction, elle appelle **SQLFreeHandle** pour libérer l’instruction. Après la libération de l’instruction, il s’agit d’une erreur de programmation d’application pour utiliser le handle de l’instruction dans un appel à une fonction ODBC. Cela a des conséquences non définies mais probablement irrécupérables.  
  
 Quand **SQLFreeHandle** est appelé, le pilote libère la structure utilisée pour stocker des informations sur l’instruction.  
  
 **SQLDisconnect** libère automatiquement toutes les instructions sur une connexion.
