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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300169"
---
# <a name="how-is-metadata-used"></a>Comment les métadonnées sont-elles utilisées ?
Les applications requièrent des métadonnées pour la plupart des opérations de jeu de résultats. Par exemple, l'application utilise le type de données d'une colonne pour déterminer le type de variable à lier à cette colonne. Elle utilise la longueur d’octet d’une colonne de caractères pour déterminer l’espace dont elle a besoin pour afficher les données de cette colonne. La façon dont une application détermine les métadonnées d'une colonne dépend du type de l'application.  
  
 Les applications verticales fonctionnent avec des tables prédéfinies et effectuent des opérations prédéfinies sur ces tables. Étant donné que les métadonnées du jeu de résultats pour ces applications sont définies avant même que l’application soit écrite et contrôlées par le développeur de l’application, elles peuvent être codées en dur dans l’application. Par exemple, si une colonne d'ID d'ordre est définie en tant qu'entier de 4 octets dans la source de données, l'application peut toujours lier un entier de 4 octets à cette colonne. Lorsque les métadonnées sont codées de manière irréversible dans l'application, une modification des tables utilisées par l'application implique en général une modification du code de l'application. Ce problème est rarement dû au fait que ces modifications sont généralement effectuées dans le cadre d’une nouvelle version de l’application.  
  
 À l’instar des applications verticales, les applications personnalisées fonctionnent généralement avec des tables prédéfinies et effectuent des opérations prédéfinies sur ces tables. Par exemple, une application peut être écrite pour transférer des données entre trois sources de données différentes ; les données à transférer sont généralement connues lors de l’écriture de l’application. Ainsi, les applications personnalisées ont également tendance à avoir des métadonnées codées en dur.  
  
 Les applications génériques, en particulier celles qui prennent en charge les requêtes ad hoc, ne savent presque jamais les métadonnées des jeux de résultats qu’elles créent. Par conséquent, ils doivent découvrir les métadonnées au moment de l’exécution à l’aide des fonctions **SQLNumResultCols**, **SQLDescribeCol**et **SQLColAttribute**, qui sont décrites dans la section suivante, [SQLDescribeCol et SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md).  
  
 Toutes les applications, quel que soit leur type, peuvent coder en dur les métadonnées des jeux de résultats retournés par les fonctions de catalogue. Ces jeux de résultats sont définis dans la section Référence de ce manuel.
