---
title: Récupérer les informations du jeu de résultats (ODBC) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ae6d8f1c5640ee0dc8f63b54a2117057b8f334e2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044936"
---
# <a name="retrieve-result-set-information-odbc"></a>Récupérer des informations du jeu de résultats (ODBC)
    
### <a name="to-get-information-about-a-result-set"></a>Pour obtenir des informations sur un jeu de résultats  
  
1.  Appelez [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) pour obtenir le nombre de colonnes dans le jeu de résultats.  
  
2.  Pour chaque colonne de l'ensemble de résultats :  
  
    -   Appelez [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) pour obtenir plus d’informations sur la colonne de résultats.  
  
     ou  
  
    -   Appelez [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) pour obtenir des informations spécifiques sur la colonne de résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures relatives aux résultats de traitement &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)   
 [Détermination des caractéristiques d’un jeu de résultats &#40;ODBC&#41;](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  