---
title: SQLSpecialColumns | Documents Microsoft
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
topic_type:
- apiref
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3a324381f44a19866ebdeba6dac1c319c0d10224
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051042"
---
# <a name="sqlspecialcolumns"></a>SQLSpecialColumns
  Demande lorsque les identificateurs de ligne (*IdentifierType* SQL_BEST_ROWID), **SQLSpecialColumns** renvoie un jeu de résultats vide (aucune ligne de données) pour toute étendue autre que SQL_SCOPE_CURROW demandée. Le jeu de résultats généré indique que les colonnes ne sont valides que dans cette étendue.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge les pseudo-colonnes pour les identificateurs. Le **SQLSpecialColumns** jeu de résultats identifie toutes les colonnes sous la forme SQL_PC_NOT_PSEUDO.  
  
 **SQLSpecialColumns** peut être exécutée sur un curseur statique. Toute tentative d’exécution **SQLSpecialColumns** sur un être mise à jour (commandé par keyset ou dynamic) retourne SQL_SUCCESS_WITH_INFO, indiquant le type de curseur a été modifié.  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLSpecialColumns des fonctionnalités de date et heure améliorées  
 Pour plus d’informations sur les valeurs retournées pour les colonnes DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH et DECIMAL_DIGTS pour les types date/heure, consultez [métadonnées de catalogue](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Pour plus d’informations, consultez [Date et heure améliorations &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a>Prise en charge par SQLSpecialColumns des grands types CLR définis par l'utilisateur  
 **SQLSpecialColumns** prend en charge les types CLR volumineux définis par l’utilisateur (UDT). Pour plus d’informations, consultez [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLSpecialColumns, fonction](http://go.microsoft.com/fwlink/?LinkId=59371)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  