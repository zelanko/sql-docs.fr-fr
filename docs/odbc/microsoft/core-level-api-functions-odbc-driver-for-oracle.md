---
description: Fonctions de l’API du niveau principal (pilote ODBC pour Oracle)
title: Fonctions d’API de niveau principal (pilote ODBC pour Oracle) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], functions
- core level API functions [ODBC]
- ODBC core level API functions [ODBC]
ms.assetid: 8596eed7-bda6-4cac-ae1f-efde1aab785f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c0940dd9fbabc02a5fd384208b2dcd4803f4f24a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471651"
---
# <a name="core-level-api-functions-odbc-driver-for-oracle"></a>Fonctions de l’API du niveau principal (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Les fonctions à ce niveau comprennent le niveau minimal de conformité de l’interface pour les pilotes ODBC.  
  
|Fonction API|Notes|  
|------------------|-----------|  
|**SQLAllocConnect**|Alloue de la mémoire pour un handle de connexion, *hdbc*, dans l’environnement identifié par *henv*. Le gestionnaire de pilotes traite cet appel et appelle la fonction **SQLAllocConnect** du pilote à chaque appel de **SQLConnect**, **SQLBrowseConnect**ou **SQLDriverConnect** .|  
|**SQLAllocEnv**|Affiche une boîte de dialogue qui spécifie la condition requise pour le logiciel client Oracle, puis retourne SQL_NULL_HANDLE. Si le logiciel client Oracle n’est pas installé, cette fonction alloue de la mémoire pour un handle d’environnement, *henv*, et initialise l’interface de niveau appel ODBC pour une utilisation par une application.|  
|**SQLAllocStmt,**|Alloue de la mémoire pour un descripteur d’instruction et associe le descripteur d’instruction à la connexion spécifiée par hdbc. Le gestionnaire de pilotes passe cet appel au pilote, qui alloue la mémoire pour la structure HSTMT.|  
|**SQLBindCol**|Affecte l’espace de stockage pour une colonne de résultats et spécifie le type du résultat.|  
|**SQLCancel**|Annule le traitement sur un descripteur d’instruction, hstmt. Dans certains cas, Oracle n’autorise pas l’annulation d’une instruction en cours d’exécution. Cela signifie qu’une instruction en cours de exécution continue jusqu’à ce que Oracle termine le processus, auquel cas les résultats des instructions sont annulés par le pilote ODBC pour Oracle.|  
|**SQLColAttributes**|Retourne les informations de descripteur pour une colonne dans un jeu de résultats. Les informations de descripteur sont retournées sous la forme d’une chaîne de caractères, d’une valeur dépendante du descripteur 32 bits ou d’une valeur entière.|  
|**SQLConnect**|Établit une connexion à une source de données. Pour utiliser l’authentification du système d’exploitation Oracle, spécifiez « / » comme paramètre *szUID* et «» comme paramètre *szAuthStr* .|  
|**SQLDescribeCol**|Retourne le nom, le type, la précision, l’échelle et la possibilité de valeur null de la colonne de résultat donnée. **Remarque : SQLDescribeCol** signale des colonnes calculées comme SQL_VARCHAR.|  
|**SQLDisconnect**|Ferme une connexion. Si le regroupement de connexions est activé pour un environnement partagé et qu’une application appelle **SQLDisconnect** sur une connexion dans cet environnement, la connexion est retournée au pool de connexions et est toujours disponible pour d’autres composants utilisant le même environnement partagé.|  
|**SQLError**|Retourne des informations d’erreur ou d’État sur la dernière erreur. Le pilote gère une pile ou une liste d’erreurs qui peuvent être retournées pour les arguments *HSTMT*, *hdbc*et *henv* , en fonction de la façon dont l’appel à **SQLError** est effectué. La file d’attente d’erreurs est vidée après chaque instruction. Récupère généralement un message d’erreur Oracle et est vide.|  
|**SQLExecDirect**|Exécute une nouvelle instruction SQL qui n’est pas préparée. Le pilote utilise les valeurs actuelles des variables de marqueur de paramètre si des paramètres existent dans l’instruction. Si vos noms de table, de vue ou de champ contiennent des espaces, mettez les noms entre guillemets. Par exemple, si votre base de données contient une table nommée *My table* et le champ *My*Field, placez chaque élément de l’identificateur comme suit :<br /><br /> Sélectionnez \` ma table \` . \`Mon champ1 \` ,; \` Ma table \` . \` Mon champ2 \` de \` ma table\`|  
|**SQLExecute**|Exécute une instruction SQL préparée (une instruction déjà préparée par **SQLPrepare**). Le pilote utilise les valeurs actuelles des variables de marqueur de paramètre si des paramètres existent dans l’instruction.|  
|**SQLFetch**|Récupère une ligne d’un jeu de résultats dans les emplacements spécifiés par les appels précédents à **SQLBindCol**. Prépare le pilote pour un appel à **SQLGetData** pour les colonnes indépendantes.|  
|**Sqlfreeconnect,**|Libère un handle de connexion et libère toute la mémoire allouée pour le descripteur.|  
|**Sqlfreeenv,**|Ferme le pilote ODBC pour Oracle et libère toute la mémoire associée au pilote.|  
|**SQLFreeStmt**|Arrête le traitement associé à un HSTMT spécifique, ferme tous les curseurs ouverts associés à hstmt, ignore les résultats en attente et libère éventuellement toutes les ressources associées au descripteur d’instruction.|  
|**SQLGetCursorName**|Retourne le nom du curseur associé au HSTMT donné.|  
|**SQLNumResultCols**|Retourne le nombre de colonnes dans un curseur de jeu de résultats.|  
|**SQLPrepare**|Prépare une instruction SQL en planifiant l’optimisation et l’exécution de l’instruction. L’instruction SQL est compilée pour être exécutée par **SQLExecDirect**.<br /><br /> Si vos noms de table, de vue ou de champ contiennent des espaces, mettez les noms entre guillemets. Par exemple, si votre base de données contient une table nommée *My table* et le champ *My*Field, placez chaque élément de l’identificateur comme suit :<br /><br /> Sélectionnez \` ma table \` . \` Mon champ \` de \` ma table\`<br /><br /> Pour plus d’informations sur l’utilisation de jeux de résultats contenant des tableaux en tant que paramètres formels, consultez [renvoi de paramètres de tableau à partir de procédures stockées](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md).|  
|**SQLRowCount**|Oracle ne permet pas de déterminer le nombre de lignes dans un jeu de résultats tant que vous n’avez pas récupéré la dernière ligne, de sorte qu’elle retourne-1.|  
|**SQLSetCursorName**|Associe un nom de curseur à un descripteur d’instruction actif, *HSTMT*.|  
|**SQLSetParam,**|Remplacé par SQLBindParameter dans ODBC 2. *x*.|  
|**SQLTransact**|Demande une opération de validation ou de restauration pour toutes les opérations actives sur tous les descripteurs d’instructions (hstmts) associés à une connexion, ou pour toutes les connexions associées au handle d’environnement, *henv*. Si une validation échoue en mode manuel, la transaction reste active ; vous pouvez choisir de restaurer la transaction ou de réessayer l’opération de validation. Si une opération de validation échoue en mode de transaction automatique, la transaction est restaurée automatiquement ; la transaction ne peut pas être inactive.|
