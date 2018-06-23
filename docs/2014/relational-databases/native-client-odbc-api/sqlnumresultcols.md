---
title: SQLNumResultCols | Documents Microsoft
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
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 73ac3425eab1a4c19130352ef566153eb6c34e53
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040626"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
  Pour les instructions exécutées, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client n’accède pas au serveur pour indiquer le nombre de colonnes dans un jeu de résultats. Dans ce cas, `SQLNumResultCols` n’entraîne pas un aller-retour sur le serveur. Comme [SQLDescribeCol](sqldescribecol.md) et [SQLColAttribute](sqlcolattribute.md), l’appel `SQLNumResultCols` sur préparées mais instructions non exécutées génère un aller-retour sur le serveur.  
  
 Lorsqu'une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] ou un lot d'instructions retourne plusieurs ensembles de lignes de résultat, il est possible que le nombre de colonnes de jeu de résultats soit différent d'un ensemble de lignes à un autre. `SQLNumResultCols` doit être appelée pour chaque ensemble. Lorsque le nombre de colonnes change, l'application doit réassocier les valeurs de données avant d'extraire les résultats de ligne. Pour plus d’informations sur la gestion des résultats multiples ensemble, consultez [SQLMoreResults](sqlmoreresults.md).  
  
 Améliorations dans le moteur de base de données en commençant par [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] autoriser SQLNumResultCols obtenir des descriptions plus exactes des résultats attendus. Ces résultats plus précis peuvent différer des valeurs retournées par SQLNumResultCols dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [de découverte des métadonnées](../native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLNumResultCols](http://go.microsoft.com/fwlink/?LinkId=59359)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  