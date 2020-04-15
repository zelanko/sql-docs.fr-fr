---
title: SQLDescribeCol et SQLColAttribute (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], and SQLDescribeCol
- SQLDescribeCol function [ODBC], and SQLColAttribute
- result sets [ODBC], metadata
- retrieving result set meta data [ODBC]
- metadata [ODBC], result set
ms.assetid: c2ca442c-03a8-4e0f-9e67-b300bb15962f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8bd21010908473e4216a02a504b2de25578d5c84
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299759"
---
# <a name="sqldescribecol-and-sqlcolattribute"></a>SQLDescribeCol et SQLColAttribute
**SQLDescribeCol** et **SQLColAttribute** sont utilisés pour récupérer les métadonnées définies de résultats. La différence entre ces deux fonctions est que **SQLDescribeCol** renvoie toujours les mêmes cinq informations (nom d’une colonne, type de données, précision, échelle et nullabilité), tandis que **SQLColAttribute** renvoie toujours un seul élément d’information demandé par l’application. Cependant, **SQLColAttribute** peut retourner une sélection beaucoup plus riche de métadonnées, y compris la sensibilité aux cas d’une colonne, la taille de l’affichage, la redatabilité et la searchabilité.  
  
 De nombreuses applications, en particulier ceux qui n’affichent que des données, ne nécessitent que les métadonnées retournées par **SQLDescribeCol**. Pour ces applications, il est plus rapide d’utiliser **SQLDescribeCol** que **SQLColAttribute** parce que l’information est retournée en un seul appel. D’autres applications, en particulier ceux qui mettent à jour les données, nécessitent les métadonnées supplémentaires retournées par **SQLColAttribute** et donc utiliser les deux fonctions. De plus, **SQLColAttribute** prend en charge les métadonnées spécifiques au conducteur; pour plus d’informations, voir [Types de données spécifiques au conducteur, Types descripteurs, Types d’information, Types de diagnostic et Attributs](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Une application peut récupérer les métadonnées définies de résultat à tout moment après qu’une déclaration a été préparée ou exécutée et avant que le curseur sur l’ensemble de résultat soit fermé. Très peu d’applications nécessitent des métadonnées définies de résultat après la préparation de la déclaration et avant qu’elle ne soit exécutée. Si possible, les applications doivent attendre pour récupérer les métadonnées jusqu’à ce que la déclaration soit exécutée, parce que certaines sources de données ne peuvent pas retourner les métadonnées pour les instructions préparées et l’imitation de cette capacité dans le conducteur est souvent un processus lent. Par exemple, le conducteur peut générer un résultat à ligne zéro défini en remplaçant la clause **WHERE** d’une déclaration **SELECT** par la clause **WHERE 1 et 2** et en exécutant l’instruction résultante.  
  
 Les métadonnées sont souvent coûteuses à récupérer à partir de la source de données. Pour cette raison, les pilotes doivent mettre en cache toutes les métadonnées qu’ils récupèrent sur le serveur et le tenir aussi longtemps que le curseur sur l’ensemble de résultat est ouvert. En outre, les demandes ne devraient demander que les métadonnées dont elles ont absolument besoin.
