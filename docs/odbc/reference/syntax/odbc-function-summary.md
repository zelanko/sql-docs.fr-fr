---
title: Résumé de la fonction ODBC (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], listed by task
ms.assetid: 7aa635da-e6b7-439f-8e9b-c3860e24de5e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c10cc7880cf941a1490f963e21e8b44bc91db215
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298920"
---
# <a name="odbc-function-summary"></a>Récapitulatif des fonctions ODBC
Le tableau suivant énumère les fonctions de l’ODBC, regroupées par type de tâche, et comprend la désignation de conformité et une brève description de l’objet de chaque fonction. Pour plus d’informations sur les désignations de conformité, voir [ODBC et le CLI standard](../../../odbc/reference/odbc-and-the-standard-cli.md). Pour plus d’informations sur la syntaxe et la sémantique pour chaque fonction, voir [ODBC API Référence](../../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Une application peut appeler la fonction **SQLGetInfo** pour obtenir des informations de conformité sur un conducteur. Pour obtenir des informations sur la prise en charge d’une fonction spécifique chez un conducteur, une application peut appeler **SQLGetFunctions**.  
  
|Tâche|Nom de la fonction|Conformité|Objectif|  
|----------|-------------------|-----------------|-------------|  
|Connexion à une source de données|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|ISO 92|Obtient un environnement, une connexion, une déclaration ou une poignée descripteur.|  
||[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|ISO 92|Connexion à un pilote spécifique par nom de source de données, identifiant d’utilisateur et mot de passe.|  
||[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|ODBC|Se connecte à un pilote spécifique par chaîne de connexion ou demande que le Gestionnaire de conducteur et le conducteur affichent des boîtes de dialogue pour l’utilisateur.|  
||[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|ODBC|Retourne les niveaux successifs d’attributs de connexion et les valeurs d’attribut valides. Lorsqu’une valeur a été spécifiée pour chaque attribut de connexion, se connecte à la source de données.|  
|Obtenir des informations sur un conducteur et une source de données|[SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)<br /><br /> [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|ISO 92<br /><br /> ODBC|Retourne la liste des sources de données disponibles.<br /><br /> Retourne la liste des pilotes installés et leurs attributs.|  
||[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|ISO 92|Renvoie des informations sur un conducteur et une source de données spécifiques.|  
||[SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)|ISO 92|Retours pris en charge fonctions du conducteur.|  
||[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|ISO 92|Renvoie des informations sur les types de données pris en charge.|  
|Définir et récupérer les attributs du conducteur|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)<br /><br /> [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|ISO 92<br /><br /> ISO 92|Définit un attribut de connexion.<br /><br /> Retourne la valeur d’un attribut de connexion.|  
||[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|ISO 92|Définit un attribut d’environnement.|  
||[SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|ISO 92|Retourne la valeur d’un attribut de l’environnement.|  
||[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|ISO 92|Définit un attribut de déclaration.|  
||[SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|ISO 92|Retourne la valeur d’un attribut de déclaration.|  
|Réglage et récupération des champs descripteurs|[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)<br /><br /> [SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|ISO 92<br /><br /> ISO 92|Retourne la valeur d’un champ descripteur unique.<br /><br /> Retourne les valeurs de plusieurs champs descripteur.|  
||[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|ISO 92|Définit un champ descripteur unique.|  
||[SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|ISO 92|Définit plusieurs champs descripteur.|  
||[SQLCopyDesc (SQLCopyDesc)](../../../odbc/reference/syntax/sqlcopydesc-function.md)|ISO 92|Copies des informations descripteur d’une poignée descripteur à une autre.|  
|Préparation des demandes SQL|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|ISO 92|Prépare une déclaration SQL pour une exécution ultérieure.|  
||[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|ODBC|Assigne le stockage pour un paramètre dans un relevé SQL.|  
||[SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|ISO 92|Retourne le nom du curseur associé à une poignée de relevé.|  
||[SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|ISO 92|Spécifie un nom de curseur.|  
||[SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|ODBC|Définit les options qui contrôlent le comportement des curseurs.|  
|Soumettre des demandes|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)<br /><br /> [SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|ISO 92<br /><br /> ISO 92|Exécute une instruction préparée.<br /><br /> Exécute une instruction.|  
||[SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)|ODBC|Retourne le texte d’une déclaration SQL tel que traduit par le conducteur.|  
||[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|ODBC|Retourne la description pour un paramètre spécifique dans une instruction.|  
||[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|ISO 92|Retourne le nombre de paramètres dans une déclaration.|  
||[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|ISO 92|Utilisé en conjonction avec **SQLPutData** pour fournir des données de paramètres au moment de l’exécution. (Utile pour les valeurs de données longues.)|  
||[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|ISO 92|Envoie une partie ou la totalité d’une valeur de données pour un paramètre. (Utile pour les valeurs de données longues.)|  
|Récupération des résultats et informations sur les résultats|[SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md)<br /><br /> [SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|ISO 92<br /><br /> ISO 92|Retourne le nombre de lignes affectées par un encart, une mise à jour ou une demande de suppression.<br /><br /> Retourne le nombre de colonnes dans le jeu de résultats.|  
||[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|ISO 92|Décrit une colonne dans l’ensemble de résultats.|  
||[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|ISO 92|Décrit les attributs d’une colonne dans l’ensemble de résultats.|  
||[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|ISO 92|Assigne le stockage pour une colonne de résultat et spécifie le type de données.|  
||[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|ISO 92|Retourne plusieurs lignes de résultats.|  
||[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|ISO 92|Retourne les lignes de résultats défilementables.|  
||[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|ISO 92|Renvoie une partie ou la totalité d’une colonne d’une rangée d’un ensemble de résultats. (Utile pour les valeurs de données longues.)|  
||[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|ODBC|Positionne un curseur dans un bloc de données récupéré et permet à une application de actualiser les données dans le jeu de ligne ou de mettre à jour ou de supprimer des données dans l’ensemble de résultats.|  
||[SQLBulkOperations (SQLBulkOperations)](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|ODBC|Effectue des insertions en vrac et des opérations de signets en vrac, y compris mettre à jour, supprimer et aller chercher par signet.|  
||[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|ODBC|Détermine s’il y a plus d’ensembles de résultats disponibles et, dans l’affirmative, paramélise le traitement pour l’ensemble de résultats suivant.|  
||[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|ISO 92|Renvoie des informations diagnostiques supplémentaires (un seul domaine de la structure de données diagnostiques).|  
||[SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|ISO 92|Renvoie des informations diagnostiques supplémentaires (plusieurs domaines de la structure de données diagnostiques).|  
|Obtenir des informations sur les tables système de la source de données (fonctions de catalogue)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)<br /><br /> [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|ODBC<br /><br /> Ouvrir le groupe|Retourne une liste de colonnes et de privilèges associés pour une ou plusieurs tables.<br /><br /> Retourne la liste des noms de colonnes dans des tableaux spécifiés.|  
||[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|ODBC|Renvoie une liste de noms de colonnes qui composent les clés étrangères, si elles existent pour une table spécifiée.|  
||[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|ODBC|Retourne la liste des noms de colonnes qui constituent la clé principale pour une table.|  
||[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|ODBC|Retourne la liste des paramètres d’entrée et de sortie, ainsi que les colonnes qui composent le résultat défini pour les procédures spécifiées.|  
||[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|ODBC|Renvoie la liste des noms de procédures stockés dans une source de données spécifique.|  
||[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|Ouvrir le groupe|Retourne des informations sur l’ensemble optimal de colonnes qui identifie uniquement une ligne dans un tableau spécifié, ou les colonnes qui sont automatiquement mises à jour lorsque toute valeur de la ligne est mise à jour par une transaction.|  
||[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|ISO 92|Retourne les statistiques sur un tableau unique et la liste des indices associés au tableau.|  
||[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|ODBC|Retourne une liste de tables et les privilèges associés à chaque table.|  
||[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|Ouvrir le groupe|Renvoie la liste des noms de table stockés dans une source de données spécifique.|  
|Mettre fin à une déclaration|[SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|ISO 92|Termine le traitement des relevés, rejette les résultats en attente et, en option, libère toutes les ressources associées à la poignée de déclaration.|  
||[SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|ISO 92|Ferme un curseur qui a été ouvert sur une poignée de déclaration.|  
||[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|ISO 92|Annule le traitement sur une déclaration.|  
||[SQLCancelHandle (en anglais)](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|ODBC|Annule le traitement sur une déclaration ou une connexion.|  
||[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|ISO 92|Engage ou annule une transaction.|  
|Mettre fin à une connexion|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|ISO 92<br /><br /> ISO 92|Ferme la connexion.<br /><br /> Libère une poignée d’environnement, de connexion, de relevé ou descripteur.|
