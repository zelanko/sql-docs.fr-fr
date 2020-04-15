---
title: Fonctions API de niveau 2 (ODBC Driver pour Oracle) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC level 2 API functions [ODBC]
- functions [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], functions
- ODBC API functions [ODBC]
- API functions [ODBC]
- level 2 API functions [ODBC]
ms.assetid: d9f49520-72d7-4234-8635-260d0ce4199c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b1e181c5863d6b906eaf9a3ba499728c595f0449
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284179"
---
# <a name="level-2-api-functions-odbc-driver-for-oracle"></a>Fonctions de l’API du niveau 2 (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Les fonctions à ce niveau fournissent la conformation d’interface de niveau 1 ainsi que des fonctionnalités supplémentaires telles que le support pour les signets, les paramètres dynamiques, et l’exécution asynchrone des fonctions d’ODBC.  
  
|Fonction API|Notes|  
|------------------|-----------|  
|**SQLBindParameter**|Associe un tampon à un marqueur de paramètres dans une déclaration SQL.|  
|**SQLBrowseConnect**|Retourne les niveaux successifs d’attributs et de valeurs d’attribut.|  
|**SQLDataSources**|Répertorie les noms de source de données. Mise en œuvre par le Driver Manager.|  
|**SQLDescribeParam**|Retourne la description d’un marqueur de paramètres associé à une déclaration SQL préparée.<br /><br /> Retourne une meilleure estimation de ce que le paramètre est, basé sur l’analyse de l’instruction. Si le type de paramètre ne peut pas être déterminé, SQL_VARCHAR revient avec la longueur 2000.|  
|**SQLDrivers**|Mise en œuvre par le Driver Manager.|  
|**SQLExtendedFetch**|Semblable à **SQLFetch,** mais retourne plusieurs lignes à l’aide d’un tableau pour chaque colonne. L’ensemble de résultat est défilement vers l’avant et peut être rendu défilement vers l’arrière si le curseur est défini comme statique, et non vers l’avant seulement. Pour les curseurs avant-seulement avec la liaison de colonne par défaut, les données de colonne des ensembles de données plus grandes que l’attribut de connexion BUFFERSIZE sont récupérées directement dans des tampons de données. Ne prend pas en charge les signets à longueur variable et ne prend pas en charge la récupération d’un acart à un décalage (autre que 0) à partir d’un signet.|  
|**SQLForeignKeys**|Retourne une liste de clés étrangères dans une seule table, ou une liste de clés étrangères dans d’autres tableaux qui se réfèrent à une seule table.|  
|**SQLMoreResults**|Détermine si d’autres résultats sont en attente sur une poignée de déclaration, hstmt, contenant DES instructions SELECT, UPDATE, INSERT ou DELETE et, dans l’affirmative, initialise le traitement de ces résultats.<br /><br /> Oracle prend en charge plusieurs ensembles de résultats uniquement à partir de procédures stockées, lors de l’utilisation de séquences d’évasion .|  
|**SQLNativeSql**|Pour plus d’informations sur l’utilisation, voir [Paramètres de tableau de retour à partir de procédures stockées](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md).|  
|**SQLNumParams**|Retourne le nombre de paramètres dans un communiqué de SQL. Le nombre de paramètres devrait égaler le nombre de points d’interrogation dans la déclaration SQL transmise à **SQLPrepare**.|  
|**SQLPrimaryKeys**|Retourne les noms de colonne qui composent la clé principale pour une table.|  
|**SQLProcedureColumns**|Retourne une liste des paramètres d’entrée et de sortie, la valeur de retour, les colonnes dans l’ensemble de résultat d’une seule procédure, et deux colonnes supplémentaires, OVERLOAD et ORDINAL_POSITION. OVERLOAD est la colonne OVERLOAD du tableau ALL_ARGUMENTS de l’Oracle Data Dictionary View. ORDINAL_POSITION est la colonne SÉQUENCE de la table ALL_ARGUMENTS de l’Oracle Data Dictionary View. Pour les procédures emballées, la colonne PROCEDURE NAME est en format *packagename.procedurename.* Ne renvoie pas les colonnes de procédure d’un synonyme créé qui se réfère à une procédure ou une fonction.|  
|**SQLProcedures**|Renvoie une liste de procédures dans la source de données. Pour les procédures emballées, la colonne PROCEDURE NAME est en format *packagename.procedurename.*<br /><br /> Parce qu’Oracle ne fournit pas un moyen de distinguer les procédures emballées des fonctions emballées, le pilote retourne SQL_PT_UNKNOWN pour la colonne PROCEDURE_TYPE.|  
|**SQLSetPos**|Définit la position du curseur dans un aviron. Vous pouvez utiliser **SQLSetPos** avec **SQLGetData** pour récupérer les rangées des colonnes non liées après avoir placé le curseur à une rangée spécifique dans le rame. Des lignes ajoutées à l’ensemble de résultats à l’aide de *fOption* SQL_ADD sont ajoutées après la dernière ligne dans l’ensemble de résultats.|  
|**SQLSetScrollOptions**|Définit les options qui contrôlent le comportement des curseurs associés à une poignée de déclaration, hstmt. Pour plus de détails, voir [Cursor Type and Concurrency Combinations](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|
