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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68069780"
---
# <a name="freeing-a-statement-handle-odbc"></a>Libération d’un handle d’instruction dans ODBC
Comme mentionné précédemment, il est plus efficace de réutiliser des instructions que to déposez-les et allouer de nouveaux. Avant d’exécuter une nouvelle instruction SQL sur une instruction, les applications doivent être sûr que les paramètres actuels de l’instruction sont appropriées. Cela inclut les attributs d'instruction, les liaisons de paramètres et les liaisons de jeux de résultats. En règle générale, les paramètres et jeux de résultats pour l’ancienne instruction SQL doivent être indépendantes (en appelant **SQLFreeStmt** avec les options SQL_RESET_PARAMS et SQL_UNBIND) et élastique pour la nouvelle instruction SQL.  
  
 Lorsque l’application a terminé d’utiliser l’instruction, elle appelle **SQLFreeHandle** pour libérer de l’instruction. Après la libération de l’instruction, il est une erreur de programmation d’application à utiliser le handle d’instruction dans un appel à une fonction ODBC ; Cette approche présente des conséquences non définis mais probablement irrécupérables.  
  
 Lorsque **SQLFreeHandle** est appelée, les versions de pilote la structure utilisée pour stocker des informations sur l’instruction.  
  
 **SQLDisconnect** libère automatiquement toutes les instructions sur une connexion.
