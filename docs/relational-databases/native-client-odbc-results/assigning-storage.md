---
title: Affectation du stockage | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- column-wise binding [ODBC]
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLBindCol function
- storing data [ODBC]
- result sets [ODBC], storage
- SQL Server Native Client ODBC driver, data storage
- row-wise binding
- binding result sets [SQL Server Native Client]
- array binding
ms.assetid: 11c81955-5300-495f-925f-9256f2587b58
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 322c6b7f9ae296ca59186af8a5eb865d28ff41de
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775917"
---
# <a name="assigning-storage"></a>Assignation du stockage
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Une application peut assigner le stockage pour les résultats avant ou après avoir exécuté une instruction SQL. Si une application prépare ou exécute en premier l'instruction SQL, elle peut se renseigner à propos du jeu de résultats avant d'assigner le stockage pour les résultats. Par exemple, si le jeu de résultats est inconnu, l'application doit extraire le nombre de colonnes avant de pouvoir lui assigner du stockage.  
  
 Pour associer le stockage pour une colonne de données, une application appelle [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)et la transmet :  
  
-   Le type de données vers lequel les données doivent être converties.  
  
-   L'adresse d'un tampon de sortie pour les données.  
  
     L'application doit allouer cette mémoire tampon, qui doit être suffisamment grande pour contenir les données au format dans lequel elles sont converties.  
  
-   La longueur du tampon de sortie.  
  
     Cette valeur est ignorée si les données retournées ont une largeur fixe dans C, tel qu'un entier, un nombre réel ou une structure de date.  
  
-   L'adresse d'un tampon mémoire dans lequel retourner le nombre d'octets de données disponibles.  
  
 Une application peut également lier des colonnes de jeu de résultats à des tableaux de variables de programme afin de prendre en charge l'extraction de lignes de jeu de résultats en blocs. Il existe deux types différents de liaison de tableau :  
  
-   La liaison basée sur les colonnes est finie lorsque chaque colonne est liée à son propre tableau de variables.  
  
     La liaison selon les colonnes est spécifiée en appelant [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) avec l' *attribut* défini sur SQL_ATTR_ROW_BIND_TYPE et *ValuePtr* défini sur SQL_BIND_BY_COLUMN. Tous les tableaux doivent contenir le même nombre d'éléments.  
  
-   La liaison basée sur les lignes est finie lorsque tous les paramètres dans l'instruction SQL sont liés en tant qu'unité à un tableau de structures qui contiennent les variables individuelles pour les paramètres.  
  
     La liaison selon les lignes est spécifiée en appelant **SQLSetStmtAttr** avec l' *attribut* défini sur SQL_ATTR_ROW_BIND_TYPE et *ValuePtr* défini sur la taille de la structure contenant les variables qui recevront les colonnes du jeu de résultats.  
  
 L'application définit également SQL_ATTR_ROW_ARRAY_SIZE au nombre d'éléments dans les tableaux de colonnes ou de lignes et définit SQL_ATTR_ROW_STATUS_PTR et SQL_ATTR_ROWS_FETCHED_PTR.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des résultats &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
