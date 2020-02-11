---
title: Fonctions de l’API de niveau 2 (pilote ODBC pour Oracle) | Microsoft Docs
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
ms.openlocfilehash: 7600734fef44071b1f5e35c136a6b9facdb8b390
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67949034"
---
# <a name="level-2-api-functions-odbc-driver-for-oracle"></a>Fonctions de l’API du niveau 2 (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Les fonctions à ce niveau assurent la conformité de l’interface de niveau 1, ainsi que des fonctionnalités supplémentaires telles que la prise en charge des signets, des paramètres dynamiques et l’exécution asynchrone des fonctions ODBC.  
  
|Fonction API|Notes|  
|------------------|-----------|  
|**SQLBindParameter**|Associe une mémoire tampon à un marqueur de paramètre dans une instruction SQL.|  
|**SQLBrowseConnect**|Retourne des niveaux successifs d’attributs et de valeurs d’attribut.|  
|**SQLDataSources**|Répertorie les noms de sources de données. Implémenté par le gestionnaire de pilotes.|  
|**SQLDescribeParam**|Retourne la description d’un marqueur de paramètre associé à une instruction SQL préparée.<br /><br /> Retourne une estimation optimale de ce que le paramètre est, en fonction de l’analyse de l’instruction. Si le type de paramètre ne peut pas être déterminé, SQL_VARCHAR retourne avec une longueur de 2000.|  
|**SQLDrivers**|Implémenté par le gestionnaire de pilotes.|  
|**SQLExtendedFetch**|Semblable à **SQLFetch** , mais retourne plusieurs lignes à l’aide d’un tableau pour chaque colonne. Le jeu de résultats est un défilement vers l’avant et peut être rendu à défilement vers l’arrière si le curseur est défini comme statique, et non en avant uniquement. Pour les curseurs avant uniquement avec une liaison de colonne par défaut, les données de colonne des jeux de données plus grands que l’attribut de connexion BUFFERSIZE sont extraites directement dans les tampons de données. Ne prend pas en charge les signets de longueur variable et ne prend pas en charge l’extraction d’un ensemble de lignes à un décalage (autre que 0) à partir d’un signet.|  
|**SQLForeignKeys**|Retourne une liste de clés étrangères dans une table unique, ou une liste de clés étrangères dans d’autres tables qui font référence à une table unique.|  
|**SQLMoreResults**|Détermine si davantage de résultats sont en attente sur un descripteur d’instruction, hstmt, contenant des instructions SELECT, UPDATE, INSERT ou DELETE et, le cas échéant, initialise le traitement de ces résultats.<br /><br /> Oracle prend en charge plusieurs jeux de résultats uniquement à partir de procédures stockées, lors de l’utilisation de séquences d’échappement {ResultSet...}.|  
|**SQLNativeSql**|Pour plus d’informations sur l’utilisation, consultez [renvoi de paramètres de tableau à partir de procédures stockées](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md).|  
|**SQLNumParams**|Retourne le nombre de paramètres dans une instruction SQL. Le nombre de paramètres doit être égal au nombre de points d’interrogation dans l’instruction SQL passée à **SQLPrepare**.|  
|**SQLPrimaryKeys**|Retourne les noms de colonnes qui composent la clé primaire d’une table.|  
|**SQLProcedureColumns**|Retourne une liste de paramètres d’entrée et de sortie, la valeur de retour, les colonnes du jeu de résultats d’une procédure unique et deux colonnes supplémentaires, OVERLOAD et ORDINAL_POSITION. OVERLOAD est la colonne de surcharge de la table ALL_ARGUMENTS de la vue de dictionnaire de données Oracle. ORDINAL_POSITION est la colonne de séquence de la table ALL_ARGUMENTS de la vue de dictionnaire de données Oracle. Pour les procédures empaquetées, la colonne de nom de la procédure est au format *PackageName. NomProcédure* . Ne retourne pas les colonnes de procédure d’un synonyme créé qui fait référence à une procédure ou une fonction.|  
|**SQLProcedures**|Retourne une liste de procédures dans la source de données. Pour les procédures empaquetées, la colonne de nom de la procédure est au format *PackageName. NomProcédure* .<br /><br /> Oracle n’offrant aucun moyen de distinguer les procédures packagées des fonctions empaquetées, le pilote retourne SQL_PT_UNKNOWN pour la colonne PROCEDURE_TYPE.|  
|**SQLSetPos**|Définit la position du curseur dans un ensemble de lignes. Vous pouvez utiliser **SQLSetPos** avec **SQLGetData** pour récupérer des lignes de colonnes indépendantes après avoir positionner le curseur sur une ligne spécifique de l’ensemble de lignes. Les lignes ajoutées au jeu de résultats à l’aide de *fOption* SQL_ADD sont ajoutées après la dernière ligne du jeu de résultats.|  
|**SQLSetScrollOptions**|Définit des options qui contrôlent le comportement des curseurs associés à un descripteur d’instruction, hstmt. Pour plus d’informations, consultez [types de curseurs et combinaisons d’accès concurrentiel](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|
