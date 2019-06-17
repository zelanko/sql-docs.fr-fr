---
title: Comment les métadonnées sont-elles utilisées ? | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], metadata
- metadata [ODBC]
ms.assetid: 70fb976c-9342-4edd-b066-1140696fd0fa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a3604e9f3bd47a10ae1a6e5ec401b198675c2d3e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149289"
---
# <a name="how-is-metadata-used"></a>Comment les métadonnées sont-elles utilisées ?
Les applications requièrent des métadonnées pour la plupart des opérations de jeu de résultats. Par exemple, l'application utilise le type de données d'une colonne pour déterminer le type de variable à lier à cette colonne. Elle utilise la longueur d’octet d’une colonne de caractères pour déterminer la quantité d’espace qu’il doit afficher les données de cette colonne. La façon dont une application détermine les métadonnées d'une colonne dépend du type de l'application.  
  
 Applications verticales fonctionnent avec des tables prédéfinies et effectuent des opérations prédéfinies sur ces tables. Étant donné que les métadonnées du jeu de résultat pour de telles applications sont définie avant que l’application est écrit et est contrôlée par le développeur d’applications, il peut être codée en dur dans l’application. Par exemple, si une colonne d'ID d'ordre est définie en tant qu'entier de 4 octets dans la source de données, l'application peut toujours lier un entier de 4 octets à cette colonne. Lorsque les métadonnées sont codées de manière irréversible dans l'application, une modification des tables utilisées par l'application implique en général une modification du code de l'application. C’est rarement un problème, étant donné que les modifications sont généralement effectuées dans le cadre d’une nouvelle version de l’application.  
  
 Comme les applications verticales, des applications personnalisées en général des tables prédéfinies et effectuent des opérations prédéfinies sur ces tables. Par exemple, une application peut être écrite pour transférer des données entre les trois différentes sources de données ; les données à transférer sont généralement connues lorsque l’application est écrite. Par conséquent, les applications personnalisées ont également tendent à avoir codé en dur des métadonnées.  
  
 Applications génériques, en particulier ceux qui prennent en charge des requêtes ad hoc, presque jamais savoir les métadonnées des jeux de résultats qu’ils créent. Par conséquent, ils doivent découvrir les métadonnées au moment de l’exécution en utilisant les fonctions **SQLNumResultCols**, **SQLDescribeCol**, et **SQLColAttribute**, qui sont décrites dans le la section suivante, [SQLDescribeCol et SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md).  
  
 Toutes les applications, quel que soit leur type, peuvent coder en dur les métadonnées pour les jeux de résultats retournés par les fonctions de catalogue. Ces jeux de résultats est définis dans la section de référence de ce manuel.
