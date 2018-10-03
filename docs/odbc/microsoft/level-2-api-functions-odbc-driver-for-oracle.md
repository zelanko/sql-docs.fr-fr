---
title: Fonctions d’API de niveau 2 (pilote ODBC pour Oracle) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: be472a4a99324927128514fa9f8cbf19d44d49cc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825899"
---
# <a name="level-2-api-functions-odbc-driver-for-oracle"></a>Fonctions de l’API du niveau 2 (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Fonctions à ce niveau fournissent la conformité de l’interface niveau 1 ainsi que des fonctionnalités supplémentaires telles que la prise en charge les signets, les paramètres dynamiques et exécution asynchrone de fonctions ODBC.  
  
|Fonction d’API|Remarques|  
|------------------|-----------|  
|**SQLBindParameter**|Associe une mémoire tampon à un marqueur de paramètre dans une instruction SQL.|  
|**SQLBrowseConnect**|Retourne les niveaux successifs d’attributs et valeurs d’attribut.|  
|**SQLDataSources**|Répertorie les noms de source de données. Implémenté par le Gestionnaire de pilotes.|  
|**SQLDescribeParam**|Retourne la description d’un marqueur de paramètre associé à une instruction SQL préparée.<br /><br /> Retourne une estimation de quel paramètre de l’est, en fonction de l’analyse de l’instruction. Si le type de paramètre ne peut pas être déterminé, SQL_VARCHAR retourne avec la longueur (2000).|  
|**SQLDrivers**|Implémenté par le Gestionnaire de pilotes.|  
|**SQLExtendedFetch**|Semblable à **SQLFetch** mais retourne plusieurs lignes à l’aide d’un tableau pour chaque colonne. Le jeu de résultats est avec défilement avant et peut être effectué descendante déroulable si le curseur est défini comme étant statique, pas avant uniquement. Pour les curseurs avant uniquement avec la liaison de colonne par défaut, les données des colonnes de jeux de données supérieure à l’attribut de connexion BUFFERSIZE sont extraite directement dans les mémoires tampons de données. Ne prend pas en charge les signets de longueur variable et ne prend pas en charge l’extraction d’un ensemble de lignes à un offset (autre que 0) à partir d’un signet.|  
|**SQLForeignKeys**|Retourne une liste de clés étrangères dans une seule table ou une liste de clés étrangères dans d’autres tables qui font référence à une seule table.|  
|**SQLMoreResults**|Détermine si plus de résultats sont en attente sur un descripteur d’instruction, hstmt, qui contient des instructions SELECT, UPDATE, INSERT ou DELETE et si tel est le cas, initialise le traitement de ces résultats.<br /><br /> Oracle prend en charge plusieurs jeux de résultats uniquement à partir de procédures stockées, avec les séquences d’échappement {resultset...}.|  
|**SQLNativeSql**|Pour plus d’informations sur l’utilisation, consultez [retournant des paramètres de tableau à partir de procédures stockées](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md).|  
|**SQLNumParams**|Retourne le nombre de paramètres dans une instruction SQL. Le nombre de paramètres doit égal au nombre de points d’interrogation dans l’instruction SQL transmise au **SQLPrepare**.|  
|**SQLPrimaryKeys**|Retourne les noms de colonnes qui composent la clé primaire pour une table.|  
|**SQLProcedureColumns**|Retourne une liste de paramètres d’entrée et sortie, la valeur de retour, les colonnes du jeu de résultats d’une procédure unique et deux colonnes supplémentaires, la surcharge et la position ordinale. La surcharge est la colonne de la surcharge de la table ALL_ARGUMENTS de la vue de dictionnaire de données Oracle. Position ordinale est la colonne de séquence à partir de la table ALL_ARGUMENTS de la vue de dictionnaire de données Oracle. Pour connaître les procédures empaquetées, la colonne nom de la procédure est dans *packagename.procedurename* format. Ne retourne pas les colonnes de la procédure d’un synonyme créé qui fait référence à une procédure ou fonction.|  
|**SQLProcedures**|Retourne une liste des procédures dans la source de données. Pour connaître les procédures empaquetées, la colonne nom de la procédure est dans *packagename.procedurename* format.<br /><br /> Étant donné que Oracle ne fournit pas de faire la distinction des procédures empaquetées à partir de fonctions empaquetées, le pilote retourne SQL_PT_UNKNOWN pour la colonne PROCEDURE_TYPE.|  
|**SQLSetPos**|Définit la position du curseur dans un ensemble de lignes. Vous pouvez utiliser **SQLSetPos** avec **SQLGetData** pour extraire des lignes à partir des colonnes indépendantes après positionner le curseur sur une ligne spécifique dans l’ensemble de lignes. Lignes ajoutées au jeu à l’aide de résultats *fOption* SQL_ADD sont ajoutés après la dernière ligne du jeu de résultats.|  
|**SQLSetScrollOptions**|Définit les options qui contrôlent le comportement des curseurs associé à un descripteur d’instruction, hstmt. Pour plus d’informations, consultez [Type de curseur et les combinaisons d’accès concurrentiel](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|
