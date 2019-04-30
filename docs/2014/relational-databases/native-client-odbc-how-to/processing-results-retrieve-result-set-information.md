---
title: Récupérer des informations sur le jeu de résultats (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a39a6715a9ba8ab08d846aabb96e5b0665a2aa43
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63200293"
---
# <a name="retrieve-result-set-information-odbc"></a>Récupérer des informations du jeu de résultats (ODBC)
    
### <a name="to-get-information-about-a-result-set"></a>Pour obtenir des informations sur un jeu de résultats  
  
1.  Appelez [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) pour obtenir le nombre de colonnes dans le jeu de résultats.  
  
2.  Pour chaque colonne de l'ensemble de résultats :  
  
    -   Appelez [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) pour obtenir des informations sur la colonne de résultats.  
  
     ou  
  
    -   Appelez [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) pour obtenir des informations spécifiques sur la colonne de résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des rubriques de procédures de résultats &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)   
 [Détermination des caractéristiques d’un jeu de résultats &#40;ODBC&#41;](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
