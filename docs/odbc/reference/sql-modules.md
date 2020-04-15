---
title: Modules SQL Microsoft Docs
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
ms.openlocfilehash: 351d1c6a34413b385bd76dfebb009b34c4c0f150
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280422"
---
# <a name="sql-modules"></a>Modules SQL
La deuxième technique d’envoi des relevés SQL au DBMS est par le biais de modules. En bref, un module se compose d’un groupe de procédures, qui sont appelées à partir de la langue de programmation hôte. Chaque procédure contient une seule déclaration SQL, et les données sont transmises à et à partir de la procédure par des paramètres.  
  
 Un module peut être considéré comme une bibliothèque d’objets qui est liée au code d’application. Cependant, la façon exacte dont les procédures et le reste de l’application sont liées dépend de la mise en œuvre. Par exemple, les procédures peuvent être compilées dans le code des objets et directement liées au code d’application, elles peuvent être compilées et stockées sur le DBMS et les appels aux identifiants du plan d’accès placés dans le code d’application, ou elles peuvent être interprétées au moment de l’exécution.  
  
 Le principal avantage des modules est qu’ils séparent proprement les déclarations SQL du langage de programmation. En théorie, il devrait être possible de changer l’un sans changer l’autre et simplement les reconnecter.
