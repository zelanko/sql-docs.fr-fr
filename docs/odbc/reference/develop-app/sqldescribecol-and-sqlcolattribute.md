---
title: SQLDescribeCol et SQLColAttribute | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e569e51540cbaa5612b158abdacac5faae77f940
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149029"
---
# <a name="sqldescribecol-and-sqlcolattribute"></a>SQLDescribeCol et SQLColAttribute
**SQLDescribeCol** et **SQLColAttribute** sont utilisées pour récupérer les métadonnées du jeu de résultats. La différence entre ces deux fonctions est que **SQLDescribeCol** retourne toujours les mêmes cinq éléments d’information (d’une colonne nom, type de données, précision, échelle et possibilité de valeur null), tout en **SQLColAttribute** retourne un élément unique d’information demandé par l’application. Toutefois, **SQLColAttribute** peut retourner une sélection beaucoup plus riche de métadonnées, y compris la casse d’une colonne, afficher la taille, les mises à jour et les possibilités de recherche.  
  
 De nombreuses applications, en particulier celles qui affichent uniquement les données, nécessitent uniquement les métadonnées retournées par **SQLDescribeCol**. Pour ces applications, il est plus rapide d’utiliser **SQLDescribeCol** à **SQLColAttribute** , car les informations sont retournées dans un seul appel. Autres applications, en particulier celles qui mettent à jour des données, nécessitent des métadonnées supplémentaires retournées par **SQLColAttribute** et par conséquent utiliser les deux fonctions. En outre, **SQLColAttribute** prend en charge les métadonnées spécifiques au pilote ; pour plus d’informations, consultez [les Types de données spécifiques au pilote, Types de descripteurs, Types d’informations, Types de diagnostics et attributs](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Une application peut récupérer les métadonnées du jeu de résultats à tout moment après une instruction a été préparée ou exécutée et avant le curseur sur le résultat de jeu est fermé. Très peu d’applications requièrent des métadonnées d’ensemble de résultats une fois que l’instruction est préparée et avant son exécution. Si possible, les applications doivent attendre de récupérer des métadonnées jusqu'à une fois que l’instruction est exécutée, étant donné que certaines sources de données ne peut pas retourner des métadonnées pour les instructions préparées et émulation de cette fonctionnalité dans le pilote est souvent un processus assez lent. Par exemple, le pilote peut générer un résultat zéro ligne défini en remplaçant le **où** clause d’un **sélectionnez** instruction avec la clause **où 1 = 2** et l’exécution de la instruction.  
  
 Les métadonnées sont souvent coûteuses à récupérer à partir de la source de données. Pour cette raison, les pilotes doivent mettre en cache des métadonnées à récupérer à partir du serveur et de conservation pour tant que le curseur sur le résultat défini est ouvert. En outre, les applications doivent demander uniquement les métadonnées que dont ils ont absolument besoin.
