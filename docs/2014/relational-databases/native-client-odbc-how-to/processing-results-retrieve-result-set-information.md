---
title: Récupérer les informations du jeu de résultats (ODBC) | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0f7ed275eb9b6558a77160c3c7fb2fc233c199cc
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048213"
---
# <a name="retrieve-result-set-information-odbc"></a>Récupérer des informations du jeu de résultats (ODBC)
    
### <a name="to-get-information-about-a-result-set"></a>Pour obtenir des informations sur un jeu de résultats  
  
1.  Appelez [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) pour obtenir le nombre de colonnes dans le jeu de résultats.  
  
2.  Pour chaque colonne de l'ensemble de résultats :  
  
    -   Appelez [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) pour obtenir des informations sur la colonne de résultats.  
  
     ou  
  
    -   Appelez [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) pour obtenir des informations de descripteur spécifiques sur la colonne de résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures relatives au traitement des résultats &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)   
 [Détermination des caractéristiques d’un jeu de résultats &#40;ODBC&#41;](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
