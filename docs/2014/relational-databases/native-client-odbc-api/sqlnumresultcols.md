---
title: SQLNumResultCols | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 88edec63a97ff6c463f07add895ff8399fc4268a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046754"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
  Pour les instructions exécutées, le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client n'accède pas au serveur pour indiquer le nombre de colonnes d'un jeu de résultats. Dans ce cas, `SQLNumResultCols` n’entraîne pas l’aller-retour du serveur. À [SQLDescribeCol](sqldescribecol.md) l’instar de SQLDescribeCol `SQLNumResultCols` et [SQLColAttribute](sqlcolattribute.md), l’appel de sur des instructions préparées mais non exécutées génère un aller-retour sur le serveur.  
  
 Lorsqu'une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] ou un lot d'instructions retourne plusieurs ensembles de lignes de résultat, il est possible que le nombre de colonnes de jeu de résultats soit différent d'un ensemble de lignes à un autre. `SQLNumResultCols`doit être appelé pour chaque ensemble. Lorsque le nombre de colonnes change, l'application doit réassocier les valeurs de données avant d'extraire les résultats de ligne. Pour plus d'informations sur la gestion de plusieurs retours de jeux de résultats, consultez [SQLMoreResults](sqlmoreresults.md).  
  
 Les améliorations apportées au moteur [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] de base de données à partir de permettent à SQLNumResultCols d’obtenir des descriptions plus précises des résultats attendus. Ces résultats plus précis peuvent différer des valeurs retournées par SQLNumResultCols dans les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]versions précédentes de. Pour plus d’informations, consultez [Découverte des métadonnées](../native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLNumResultCols fonction)](https://go.microsoft.com/fwlink/?LinkId=59359)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
