---
description: Modules SQL
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 39739ed5469b791cd0faf3df3946bebeb5d21761
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499642"
---
# <a name="sql-modules"></a>Modules SQL
La deuxième technique pour l’envoi d’instructions SQL au SGBD s’effectue par le biais de modules. Brièvement, un module se compose d’un groupe de procédures, qui sont appelées à partir du langage de programmation de l’hôte. Chaque procédure contient une instruction SQL unique, et les données sont passées vers et à partir de la procédure via des paramètres.  
  
 Un module peut être considéré comme une bibliothèque d’objets liée au code de l’application. Toutefois, la façon dont les procédures et le reste de l’application sont liées dépend de l’implémentation. Par exemple, les procédures peuvent être compilées en code objet et liées directement au code de l’application, elles peuvent être compilées et stockées sur le SGBD et les appels aux identificateurs de plan d’accès placés dans le code d’application, ou elles peuvent être interprétées au moment de l’exécution.  
  
 Le principal avantage des modules est qu’ils séparent correctement les instructions SQL du langage de programmation. En théorie, il doit être possible d’en modifier un sans modifier les autres et les lier simplement.
