---
description: SQLDescribeCol et SQLColAttribute
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2de375ea207e8e393fa36c9795ebf0e3ca5f428b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424501"
---
# <a name="sqldescribecol-and-sqlcolattribute"></a>SQLDescribeCol et SQLColAttribute
**SQLDescribeCol** et **SQLColAttribute** sont utilisés pour récupérer les métadonnées du jeu de résultats. La différence entre ces deux fonctions est que **SQLDescribeCol** retourne toujours les cinq mêmes informations (le nom d’une colonne, le type de données, la précision, l’échelle et la possibilité de valeur null), tandis que **SQLColAttribute** retourne une seule information demandée par l’application. Toutefois, **SQLColAttribute** peut retourner une sélection beaucoup plus riche de métadonnées, notamment le respect de la casse, la taille d’affichage, la mise à jour et la recherche d’une colonne.  
  
 De nombreuses applications, en particulier celles qui affichent uniquement des données, requièrent uniquement les métadonnées retournées par **SQLDescribeCol**. Pour ces applications, il est plus rapide d’utiliser **SQLDescribeCol** que **SQLColAttribute** , car les informations sont retournées en un seul appel. D’autres applications, en particulier celles qui mettent à jour des données, requièrent les métadonnées supplémentaires retournées par **SQLColAttribute** et utilisent donc les deux fonctions. En outre, **SQLColAttribute** prend en charge les métadonnées spécifiques au pilote. Pour plus d’informations, consultez [types de données spécifiques au pilote, types de descripteurs, types d’informations, types de diagnostics et attributs](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Une application peut récupérer des métadonnées de jeu de résultats à tout moment après la préparation ou l’exécution d’une instruction et avant la fermeture du curseur sur le jeu de résultats. Très peu d’applications requièrent des métadonnées de jeu de résultats après la préparation de l’instruction et avant son exécution. Si possible, les applications doivent attendre la récupération des métadonnées jusqu’à ce que l’instruction soit exécutée, car certaines sources de données ne peuvent pas retourner de métadonnées pour les instructions préparées et l’émulation de cette fonctionnalité dans le pilote est souvent un processus lent. Par exemple, le pilote peut générer un jeu de résultats de ligne zéro en remplaçant la clause **Where** d’une instruction **Select** par la clause **Where 1 = 2** et en exécutant l’instruction résultante.  
  
 Les métadonnées sont souvent coûteuses à récupérer à partir de la source de données. C’est la raison pour laquelle les pilotes doivent mettre en cache les métadonnées qu’ils récupèrent à partir du serveur et les conserver tant que le curseur sur le jeu de résultats est ouvert. En outre, les applications doivent uniquement demander les métadonnées dont elles ont absolument besoin.
