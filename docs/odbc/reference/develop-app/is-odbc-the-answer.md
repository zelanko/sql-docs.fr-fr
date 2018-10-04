---
title: ODBC est-il la réponse ? | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f90f2395eac5dce76848d7bc309f1a3d5ce289f9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600557"
---
# <a name="is-odbc-the-answer"></a>ODBC est-il la réponse ?
Avant d’aborder la question de l’interopérabilité, envisagez la question suivante : l’application doit-elle utiliser ODBC du tout ? Cela peut sembler une étrange question à poser dans un guide pour ODBC, mais il est en fait, un message légitime. ODBC n’a pas été conçu pour remplacer complètement les API de base de données natif, ni a été conçu pour fournir un accès de base de données dans toutes les circonstances. Il a été conçu pour fournir une interface commune pour les bases de données et a été conçue pour libérer les programmeurs d’applications d’avoir à en savoir plus sur et maintenir des liens vers plusieurs bases de données.  
  
 Les applications personnalisées sont des candidats idéaux pour l’API de base de données natif. La principale raison est que des applications personnalisées souvent travailler avec un système SGBD unique et n’ont pas besoin pour fonctionner. Base de données native API peut effectuer une meilleure que ODBC d’exposer les fonctionnalités de SGBD particulier et peut exposer des fonctionnalités ne pas exposées par ODBC. En outre, étant donné que les développeurs d’applications personnalisées sont généralement familiarisés avec la base de données native API pour leurs SGBD, il y a peu de raisons pour en savoir plus de ODBC. Toutefois, il est intéressant de noter que, pour certains SGBD, ODBC est la base de données API native.  
  
 Par conséquent, les applications qui sont candidats pour ODBC ? Les meilleurs candidats sont les applications qui fonctionnent avec plus d’un SGBD. Cela inclut pratiquement toutes les applications génériques et verticales. Il inclut également un nombre d’applications personnalisées. Par exemple, les applications personnalisées qui utilisent plusieurs SGBD différents sont beaucoup plus facile et plus clair à écrire avec ODBC qu’avec plusieurs API natives. Et les applications personnalisées écrites avec ODBC sont beaucoup plus faciles de migrer une société déplace d’un SGBD à l’autre ou déploie la même application sur différents SGBD.
