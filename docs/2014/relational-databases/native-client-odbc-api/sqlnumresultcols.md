---
title: SQLNumResultCols | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c1a4825dc8d73f815f6b399c6e3a51c064d3b9b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424318"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
  Pour les instructions exécutées, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client n’accède pas au serveur pour indiquer le nombre de colonnes dans un jeu de résultats. Dans ce cas, `SQLNumResultCols` n’entraîne pas un aller-retour sur le serveur. Comme [SQLDescribeCol](sqldescribecol.md) et [SQLColAttribute](sqlcolattribute.md), l’appel `SQLNumResultCols` sur préparées mais les instructions non exécutées génère un aller-retour sur le serveur.  
  
 Lorsqu'une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] ou un lot d'instructions retourne plusieurs ensembles de lignes de résultat, il est possible que le nombre de colonnes de jeu de résultats soit différent d'un ensemble de lignes à un autre. `SQLNumResultCols` doit être appelée pour chaque ensemble. Lorsque le nombre de colonnes change, l'application doit réassocier les valeurs de données avant d'extraire les résultats de ligne. Pour plus d’informations sur la gestion des résultats de plusieurs retours de jeux, consultez [SQLMoreResults](sqlmoreresults.md).  
  
 Améliorations du moteur de base de données en commençant par [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] autoriser SQLNumResultCols obtenir des descriptions plus exactes des résultats attendus. Ces résultats plus exacts peuvent différer des valeurs retournées par SQLNumResultCols dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [découverte des métadonnées](../native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLNumResultCols, fonction](http://go.microsoft.com/fwlink/?LinkId=59359)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
