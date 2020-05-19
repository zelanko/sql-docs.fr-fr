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
manager: craigg
ms.openlocfilehash: 3017f74b12eb18624f8a34e8a1289da18b70c93a
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82712695"
---
# <a name="retrieve-result-set-information-odbc"></a>Récupérer des informations du jeu de résultats (ODBC)
    
### <a name="to-get-information-about-a-result-set"></a>Pour obtenir des informations sur un jeu de résultats  
  
1.  Appelez [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) pour obtenir le nombre de colonnes dans le jeu de résultats.  
  
2.  Pour chaque colonne de l'ensemble de résultats :  
  
    -   Appelez [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) pour obtenir des informations sur la colonne de résultats.  
  
     Ou  
  
    -   Appelez [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) pour obtenir des informations de descripteur spécifiques sur la colonne de résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures relatives au traitement des résultats &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)   
 [Détermination des caractéristiques d’un jeu de résultats &#40;ODBC&#41;](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
