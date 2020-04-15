---
title: ODBC est-il la réponse ? | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], ODBC
ms.assetid: bfa5e6ee-5979-42a9-be6f-a84d1ee7a54c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f3716acbcc1b8ea648b5edc03e277983936da557
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288090"
---
# <a name="is-odbc-the-answer"></a>ODBC est-il la réponse ?
Avant de se pencher sur la question de l’interopérabilité, considérez la question suivante : l’application devrait-elle utiliser ODBC? Cela peut sembler une question étrange à poser dans un guide de l’ODBC, mais il s’agit, en fait, d’une question légitime. ODBC n’a pas été conçu pour remplacer complètement les API de base de données autochtones, ni pour fournir l’accès aux bases de données en toutes circonstances. Il a été conçu pour fournir une interface commune aux bases de données et était destiné à libérer les programmeurs d’applications d’avoir à en apprendre davantage sur et à maintenir des liens vers plusieurs bases de données.  
  
 Les applications personnalisées sont des candidats de choix pour les API de base de données natives. La raison principale est que les applications personnalisées fonctionnent souvent avec un seul DBMS et n’ont pas besoin d’être interopérables. Les API de base de données autochtones pourraient faire un meilleur travail que ODBC d’exposer les capacités d’un DBMS particulier et pourrait exposer les capacités non exposées par ODBC. En outre, parce que les développeurs d’applications personnalisées sont généralement familiers avec la base de données native API pour leur DBMS, il ya peu de raisons d’apprendre ODBC. Cependant, il est intéressant de noter que pour certains DBMS, ODBC est la base de données native API.  
  
 Quelles sont donc les candidatures de l’ODBC? Les meilleurs candidats sont des candidatures qui travaillent avec plus d’un DBMS. Cela comprend pratiquement toutes les applications génériques et verticales. Il comprend également un certain nombre d’applications personnalisées. Par exemple, les applications personnalisées qui utilisent plusieurs DBMS différents sont beaucoup plus faciles et plus propres à écrire avec ODBC qu’avec plusieurs API indigènes. Et les applications personnalisées écrites avec ODBC sont beaucoup plus faciles à migrer à mesure qu’une entreprise passe d’un DBMS à un autre ou déploie la même application contre différents DBMS.
