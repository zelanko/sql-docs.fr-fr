---
title: "Quelles sont les métadonnées utilisées ? | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], metadata
- metadata [ODBC]
ms.assetid: 70fb976c-9342-4edd-b066-1140696fd0fa
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0920797887e8fa1d156401a2b91255396f6e24d2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-is-metadata-used"></a>Quelles sont les métadonnées utilisées ?
Les applications requièrent des métadonnées pour la plupart des opérations de jeu de résultats. Par exemple, l'application utilise le type de données d'une colonne pour déterminer le type de variable à lier à cette colonne. Il utilise la longueur d’octet d’une colonne de caractères pour déterminer la quantité d’espace qu’il doit afficher les données de cette colonne. La façon dont une application détermine les métadonnées d'une colonne dépend du type de l'application.  
  
 Les applications verticales travailler avec des tables prédéfinies et effectuent des opérations prédéfinies sur ces tables. Étant donné que les métadonnées du jeu de résultats pour de telles applications sont définie avant l’application est écrit et contrôlée par le développeur d’applications, il peut être codée en dur dans l’application. Par exemple, si une colonne d'ID d'ordre est définie en tant qu'entier de 4 octets dans la source de données, l'application peut toujours lier un entier de 4 octets à cette colonne. Lorsque les métadonnées sont codées de manière irréversible dans l'application, une modification des tables utilisées par l'application implique en général une modification du code de l'application. Cela est rarement un problème, car les modifications sont généralement effectuées dans le cadre d’une nouvelle version de l’application.  
  
 Comme les applications verticales, des applications personnalisées généralement travailler avec des tables prédéfinies et effectuent des opérations prédéfinies sur ces tables. Par exemple, une application peut être écrite pour transférer des données entre trois différentes sources de données ; les données à transférer sont généralement connues lorsque l’application est écrite. Par conséquent, des applications personnalisées comportent généralement codées en dur des métadonnées.  
  
 Applications génériques, en particulier ceux qui prennent en charge les requêtes ad hoc, presque jamais de connaître les métadonnées, les jeux de résultats qu’ils créent. Par conséquent, ils doivent découvrir les métadonnées au moment de l’exécution en utilisant les fonctions **SQLNumResultCols**, **SQLDescribeCol**, et **SQLColAttribute**, qui sont décrites dans la section suivante, [SQLDescribeCol et SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md).  
  
 Toutes les applications, quel que soit leur type, peuvent coder en dur les métadonnées pour les jeux de résultats retournés par les fonctions de catalogue. Ces jeux de résultats est définis dans la section de référence de ce manuel.
