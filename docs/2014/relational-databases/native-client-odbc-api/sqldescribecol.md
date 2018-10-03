---
title: SQLDescribeCol | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDescribeCol function
ms.assetid: ffbf34c6-8268-434f-829a-82009a6cda59
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4def24dac95db8cf86d0a23bd1e0f7a951d4e9e0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054989"
---
# <a name="sqldescribecol"></a>SQLDescribeCol
  Pour les instructions exécutées, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client n’a pas besoin d’interroger le serveur pour décrire les colonnes dans un jeu de résultats. Dans ce cas, `SQLDescribeCol` n’entraîne pas un aller-retour sur le serveur. Comme [SQLColAttribute](sqlnumresultcols.md), l’appel `SQLDescribeCol` sur préparées mais les instructions non exécutées génère un aller-retour sur le serveur.  
  
 Lorsqu'une instruction ou un lot d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] retourne plusieurs ensembles de lignes de résultats, il est possible qu'une colonne, référencée par un ordinal, ait pour origine une table distincte ou référence une colonne entièrement différente dans le jeu de résultats. `SQLDescribeCol` doit être appelée pour chaque ensemble. Lorsque le jeu de résultats change, l'application doit de nouveau lier les valeurs de données avant d'extraire les résultats de ligne. Pour plus d’informations sur la gestion des résultats de plusieurs retours de jeux, consultez [SQLMoreResults](sqlmoreresults.md).  
  
 Les attributs de colonnes sont signalés uniquement pour le premier jeu de résultats lorsque plusieurs jeux de résultats sont générés par un lot préparé d'instructions SQL.  
  
 Pour les types de données de valeur élevée, la valeur retournée dans *DataTypePtr* est SQL_VARCHAR, SQL_VARBINARY ou SQL_NVARCHAR. Une valeur sql_ss_length_unlimited dans *ColumnSizePtr* indique que la taille est « illimitée ».  
  
 Améliorations du moteur de base de données en commençant par [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] autoriser SQLDescribeCol obtenir des descriptions plus exactes des résultats attendus. Ces résultats plus exacts peuvent différer des valeurs retournées par SQLDescribeCol dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Découverte des métadonnées](../native-client/features/metadata-discovery.md).  
  
## <a name="sqldescribecol-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLDescribeCol des fonctionnalités de date et heure améliorées  
 Les valeurs retournées pour les types date/heure sont les suivantes :  
  
||*DataTypePtr*|*ColumnSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|---------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|Date|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Pour plus d’informations, consultez [améliorations Date / heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>Prise en charge par SQLDescribeCol des grands types CLR définis par l'utilisateur  
 `SQLDescribeCol` prend en charge les grands types CLR définis par l'utilisateur. Pour plus d’informations, consultez [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLDescribeCol, fonction](http://go.microsoft.com/fwlink/?LinkID=59338)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
