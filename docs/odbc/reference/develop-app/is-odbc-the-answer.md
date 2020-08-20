---
description: ODBC est-il la réponse ?
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
ms.openlocfilehash: 7a51c4248a041d65f00ec1846f60788cded68f7b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476601"
---
# <a name="is-odbc-the-answer"></a>ODBC est-il la réponse ?
Avant d’aborder la question de l’interopérabilité, tenez compte de la question suivante : l’application doit-elle utiliser ODBC ? Cela peut sembler une question étrange de demander un guide à ODBC, mais il s’agit en fait d’un problème légitime. ODBC n’a pas été conçu pour remplacer complètement les API de base de données natives et n’a pas été conçu pour fournir un accès à la base de données dans toutes les circonstances. Il a été conçu pour fournir une interface commune aux bases de données et a été conçu pour permettre aux programmeurs d’applications de ne pas avoir à découvrir et à gérer des liens vers plusieurs bases de données.  
  
 Les applications personnalisées sont des candidats privilégiés pour les API de base de données natives. La raison principale est que les applications personnalisées fonctionnent souvent avec un SGBD unique et n’ont pas besoin d’être interopérables. Les API de base de données natives peuvent être plus performantes que ODBC d’exposer les fonctionnalités d’un SGBD particulier et peuvent exposer des fonctionnalités qui ne sont pas exposées par ODBC. En outre, étant donné que les développeurs d’applications personnalisées sont généralement familiarisés avec l’API de base de données native pour leur SGBD, il y a peu de raisons d’apprendre ODBC. Toutefois, il est intéressant de noter que pour certains SGBD, ODBC est l’API de base de données native.  
  
 Quelles sont les applications qui sont candidates à ODBC ? Les meilleurs candidats sont des applications qui fonctionnent avec plusieurs SGBD. Cela comprend pratiquement toutes les applications génériques et verticales. Il comprend également un certain nombre d’applications personnalisées. Par exemple, les applications personnalisées qui utilisent différents SGBD sont beaucoup plus simples et plus faciles à écrire avec ODBC qu’avec plusieurs API natives. Les applications personnalisées écrites avec ODBC sont beaucoup plus faciles à migrer au fur et à mesure que les entreprises passent d’un SGBD à un autre ou déploient la même application sur différents SGBD.
