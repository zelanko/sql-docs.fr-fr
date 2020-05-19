---
title: SQLSpecialColumns | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a6208467b4d6af6b0417727643e190b8702968ea
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82702131"
---
# <a name="sqlspecialcolumns"></a>SQLSpecialColumns
  Lors de la demande d’identificateurs de ligne (*IdentifierType* SQL_BEST_ROWID), **SQLSpecialColumns** retourne un jeu de résultats vide (aucune ligne de données) pour toute étendue demandée autre que SQL_SCOPE_CURROW. Le jeu de résultats généré indique que les colonnes ne sont valides que dans cette étendue.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge les pseudo-colonnes pour les identificateurs. Le jeu de résultats **SQLSpecialColumns** identifie toutes les colonnes comme SQL_PC_NOT_PSEUDO.  
  
 **SQLSpecialColumns** peut être exécuté sur un curseur statique. Une tentative d’exécution de **SQLSpecialColumns** sur un qui peut être mis à jour (KEYSET ou Dynamic) retourne SQL_SUCCESS_WITH_INFO indiquant que le type de curseur a été modifié.  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLSpecialColumns des fonctionnalités de date et heure améliorées  
 Pour plus d’informations sur les valeurs retournées pour les colonnes DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH et DECIMAL_DIGTS pour les types date/heure, consultez [métadonnées de catalogue](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Pour plus d’informations générales, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a>Prise en charge par SQLSpecialColumns des grands types CLR définis par l'utilisateur  
 **SQLSpecialColumns** prend en charge les types CLR volumineux définis par l’utilisateur (UDT). Pour plus d’informations, consultez [types CLR volumineux définis par l’utilisateur &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLSpecialColumns fonction)](https://go.microsoft.com/fwlink/?LinkId=59371)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
