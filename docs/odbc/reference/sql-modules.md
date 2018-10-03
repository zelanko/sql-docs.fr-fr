---
title: Modules SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL modules [ODBC]
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], modules
- modules [ODBC]
- SQL statements [ODBC], modules
ms.assetid: 07551472-87ee-4765-951f-1364ed32f0c0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30c116878049c4f6a8f36e988731ab641e03c6d7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47834747"
---
# <a name="sql-modules"></a>Modules SQL
La deuxième technique pour l’envoi d’instructions SQL au SGBD est dans des modules. En bref, un module se compose d’un groupe de procédures qui sont appelées à partir de l’hôte de langage de programmation. Chaque procédure contient une instruction SQL unique, et les données sont passées vers et à partir de la procédure au moyen de paramètres.  
  
 Un module peut être considéré comme une bibliothèque d’objets qui est liée au code d’application. Cependant, exactement comment les procédures et le reste de l’application sont liés sont dépend de l’implémentation. Par exemple, les procédures peuvent être compilés en code objet et liés directement au code d’application, peut être compilés et stockés dans le SGBD et les appels pour accéder aux identificateurs de plan placés dans le code d’application, ou elles pourraient être interprétées au moment de l’exécution.  
  
 Le principal avantage de modules est qu’ils distinctement les instructions SQL à partir du langage de programmation. En théorie, il doit être possible de modifier une sans modifier l’autre et simplement les réassocier.
