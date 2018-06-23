---
title: Utiliser une instruction (ODBC) | Documents Microsoft
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
- statements [ODBC]
ms.assetid: f7573f8f-6f21-4e03-8dd5-a5f2ea4878cc
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 50a4f012b556bb6f54a0b9e672c2f9ff16a44fd2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038127"
---
# <a name="use-a-statement-odbc"></a>Utiliser une instruction (ODBC)
    
### <a name="to-use-a-statement"></a>Pour utiliser une instruction  
  
1.  Appelez [SQLAllocHandle](http://go.microsoft.com/fwlink/?LinkId=58396) avec SQL_HANDLE_STMT comme *HandleType* de manière à allouer un descripteur d’instruction.  
  
2.  Si vous le souhaitez, appelez [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) pour définir des options d’instruction ou [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) pour obtenir des attributs d’instruction.  
  
     Pour utiliser des curseurs côté serveur, vous devez affecter aux attributs de curseur des valeurs autres que leurs valeurs par défaut.  
  
3.  Si vous le souhaitez et si l'instruction doit être exécutée plusieurs fois, préparez son exécution avec la fonction [SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360).  
  
4.  Si vous le souhaitez et si l'instruction a des marqueurs de paramètres liés, liez ces marqueurs de paramètres à des variables de programme à l'aide de [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md). Si l'instruction a été préparée, vous pouvez appeler [SQLNumParams](http://go.microsoft.com/fwlink/?LinkId=58404) et [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) to find the number et characteristics of the parameters.  
  
5.  Exécutez une instruction directement en utilisant SQLExecDirect.  
  
     \- ou -  
  
     Si l'instruction a été préparée, exécutez-la plusieurs fois à l'aide de [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400).  
  
     \- ou -  
  
     Appelez une fonction de catalogue qui retourne des résultats.  
  
6.  Traitez les résultats en liant les colonnes du jeu de résultats aux variables de programme, en déplaçant des données des colonnes de jeu de résultats vers des variables de programme à l'aide de [SQLGetData](../../native-client-odbc-api/sqlgetdata.md), ou une combinaison des deux méthodes.  
  
     Extrayez une ligne à la fois dans le jeu de résultats d'une instruction.  
  
     \- ou -  
  
     Extrayez plusieurs lignes à la fois dans le jeu de résultats en utilisant un curseur de bloc.  
  
     \- ou -  
  
     Appelez [SQLRowCount](../../native-client-odbc-api/sqlrowcount.md) pour déterminer le nombre de lignes affectées par une instruction INSERT, UPDATE ou DELETE.  
  
     Si l'instruction SQL peut avoir plusieurs jeux de résultats, appelez [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) à la fin de chaque jeu de résultats pour savoir si des jeux de résultats supplémentaires doivent être traités.  
  
7.  Une fois les résultats traités, les actions suivantes peuvent être nécessaires pour rendre le descripteur d'instruction disponible pour exécuter une nouvelle instruction :  
  
    -   Si vous n'avez pas appelé [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) jusqu'à ce qu'il ait retourné SQL_NO_DATA, appelez [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) pour fermer le curseur.  
  
    -   Si vous avez lié des marqueurs de paramètres à des variables de programme, appelez [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) avec *Option* ayant la valeur SQL_RESET_PARAMS pour libérer les paramètres liés.  
  
    -   Si vous avez lié des colonnes de jeu de résultats à des variables de programme, appelez [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) avec *Option* ayant la valeur SQL_UNBIND pour libérer les colonnes liées.  
  
    -   Pour réutiliser le descripteur d'instruction, allez à l'Étape 2.  
  
8.  Appelez [SQLFreeHandle](../../native-client-odbc-api/sqlfreehandle.md) avec SQL_HANDLE_STMT comme *HandleType* pour libérer le descripteur d’instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures relatives à l’exécution de requêtes &#40;ODBC&#41;](executing-queries-how-to-topics-odbc.md)  
  
  