---
title: Comment les métadonnées sont-elles utilisées ? | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fbbba96fa2e99a2ccc0618f31e3b29e7d479f703
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300169"
---
# <a name="how-is-metadata-used"></a>Comment les métadonnées sont-elles utilisées ?
Les applications requièrent des métadonnées pour la plupart des opérations de jeu de résultats. Par exemple, l'application utilise le type de données d'une colonne pour déterminer le type de variable à lier à cette colonne. Il utilise la longueur d’entrée d’une colonne de caractère pour déterminer combien d’espace il a besoin pour afficher les données de cette colonne. La façon dont une application détermine les métadonnées d'une colonne dépend du type de l'application.  
  
 Les applications verticales fonctionnent avec des tables prédéfinies et effectuent des opérations prédéfinies sur ces tables. Étant donné que les métadonnées définies de résultat pour de telles applications sont définies avant même que l’application ne soit écrite et contrôlée par le développeur d’applications, elle peut être codée en dur dans l’application. Par exemple, si une colonne d'ID d'ordre est définie en tant qu'entier de 4 octets dans la source de données, l'application peut toujours lier un entier de 4 octets à cette colonne. Lorsque les métadonnées sont codées de manière irréversible dans l'application, une modification des tables utilisées par l'application implique en général une modification du code de l'application. Il s’agit rarement d’un problème, car de tels changements sont généralement apportés dans le cadre d’une nouvelle version de l’application.  
  
 Comme les applications verticales, les applications personnalisées fonctionnent généralement avec des tables prédéfinies et effectuent des opérations prédéfinies sur ces tables. Par exemple, une application peut être écrite pour transférer des données entre trois sources de données différentes; les données à transférer sont généralement connues lorsque l’application est écrite. Ainsi, les applications personnalisées ont également tendance à avoir des métadonnées codées par des durs.  
  
 Les applications génériques, en particulier celles qui prennent en charge les requêtes ad hoc, ne connaissent presque jamais les métadonnées des ensembles de résultats qu’elles créent. Par conséquent, ils doivent découvrir les métadonnées à l’heure de course en utilisant les fonctions **SQLNumResultCols**, **SQLDescribeCol**, et **SQLColAttribute**, qui sont décrits dans la section suivante, [SQLDescribeCol et SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md).  
  
 Toutes les applications, quel que soit leur type, peuvent des métadonnées à code dur pour les ensembles de résultats retournés par les fonctions du catalogue. Ces ensembles de résultats sont définis dans la section de référence de ce manuel.
