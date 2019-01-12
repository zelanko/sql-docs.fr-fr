---
title: Fonctions de niveau API (pilote ODBC pour Oracle) de base | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f2ada1011096eb8275f9059e531cfc0fcc1af58c
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54126169"
---
# <a name="core-level-api-functions-odbc-driver-for-oracle"></a>Fonctions de l’API du niveau principal (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Fonctions à ce niveau comprennent le niveau minimal de conformité de l’interface pour les pilotes ODBC.  
  
|Fonction d’API|Remarques|  
|------------------|-----------|  
|**SQLAllocConnect**|Alloue la mémoire pour un handle de connexion, *pas*, au sein de l’environnement identifié par *henv*. Le Gestionnaire de pilotes traite cet appel et appelle le pilote **SQLAllocConnect** fonction chaque fois que **SQLConnect**, **SQLBrowseConnect**, ou  **SQLDriverConnect** est appelée.|  
|**SQLAllocEnv**|Affiche une boîte de dialogue spécifier la configuration requise pour le logiciel Client Oracle, puis retourne SQL_NULL_HANDLE. Si le logiciel Client Oracle n’est pas installé, cette fonction alloue de la mémoire pour un handle d’environnement, *henv*et initialise l’interface de niveau d’appel ODBC pour une utilisation par une application.|  
|**SQLAllocStmt**|Alloue la mémoire pour un descripteur d’instruction et associe le handle d’instruction à la connexion spécifiée par pas. Le Gestionnaire de pilotes passe cet appel au pilote, qui alloue la mémoire pour la structure hstmt.|  
|**SQLBindCol**|Affecte l’espace de stockage pour une colonne de résultats et spécifie le type du résultat.|  
|**SQLCancel**|Annule le traitement sur un descripteur d’instruction, hstmt. Dans certains cas, Oracle n’autorise pas l’annulation d’une instruction en cours d’exécution. Cela signifie qu’une instruction en cours d’exécution continue jusqu'à ce que Oracle termine le processus, moment auquel les résultats des instructions sont annulées par le pilote ODBC pour Oracle.|  
|**SQLColAttributes**|Retourne des informations de descripteur pour une colonne dans un jeu de résultats. Informations de descripteur sont retournées comme une chaîne de caractères, une valeur de descripteur dépendant de 32 bits ou une valeur entière.|  
|**SQLConnect**|Se connecte à une source de données. Pour utiliser l’authentification du système d’exploitation Oracle, spécifiez « / » comme le *szUID* paramètre et « » en tant que le *szAuthStr* paramètre.|  
|**SQLDescribeCol**|Retourne le nom de type, précision, échelle et possibilité de valeur null de la colonne de résultat donné. **Remarque :  SQLDescribeCol** signale les colonnes calculées en tant que SQL_VARCHAR.|  
|**SQLDisconnect**|Ferme une connexion. Si le regroupement de connexions est activé pour un environnement partagé et une application appelle **SQLDisconnect** sur une connexion dans cet environnement, la connexion est retournée au pool de connexions et est toujours disponible à d’autres composants à l’aide de le même environnement partagé.|  
|**SQLError**|Retourne des informations d’erreur ou d’état sur la dernière erreur. Le pilote gère une pile ou une liste d’erreurs qui peuvent être retournées pour le *hstmt*, *pas*, et *henv* arguments, en fonction de la l’appel à **SQLError**  est effectuée. La file d’attente de l’erreur est vidé après chaque instruction. Généralement extrait un message d’erreur Oracle cas contraire elle est vide.|  
|**SQLExecDirect**|Exécute une instruction SQL de nouvelle, non préparée. Le pilote utilise les valeurs actuelles des variables de marqueur de paramètre si tous les paramètres existent dans l’instruction. Si votre table, vue ou noms de champs contiennent des espaces, placez les noms à l’arrière guillemet marques. Par exemple, si votre base de données contient une table nommée *My Table* et le champ *mon champ*, placez chaque élément de l’identificateur comme suit :<br /><br /> Sélectionnez \`ma Table\`. \`Mon Field1\`, \`Ma Table\`.\` Mon Field2\` FROM \`ma Table »|  
|**SQLExecute**|Exécute une instruction SQL préparée (une instruction déjà préparée par **SQLPrepare**). Le pilote utilise les valeurs actuelles des variables de marqueur de paramètre si tous les paramètres existent dans l’instruction.|  
|**SQLFetch**|Récupère une ligne à partir d’un jeu de résultats dans les emplacements spécifiés par les appels précédents à **SQLBindCol**. Prépare le pilote pour un appel à **SQLGetData** pour les colonnes indépendantes.|  
|**SQLFreeConnect**|Libère un handle de connexion et libère toute la mémoire allouée pour le handle.|  
|**SQLFreeEnv**|Ferme le pilote ODBC pour Oracle et libère toute la mémoire associée au pilote.|  
|**SQLFreeStmt**|Arrête le traitement associé à un hstmt spécifique, ferme tous les curseurs ouverts, associés à la hstmt, ignore les résultats en attente et éventuellement libère toutes les ressources associées au descripteur d’instruction.|  
|**SQLGetCursorName**|Retourne le nom du curseur associé à la hstmt donné.|  
|**SQLNumResultCols**|Retourne le nombre de colonnes dans un curseur de jeu de résultats.|  
|**SQLPrepare**|Prépare une instruction SQL par la planification de l’optimiser et exécutez l’instruction. L’instruction SQL est compilée pour l’exécution par **SQLExecDirect**.<br /><br /> Si votre table, vue ou noms de champs contiennent des espaces, placez les noms à l’arrière guillemet marques. Par exemple, si votre base de données contient une table nommée *My Table* et le champ *mon champ*, placez chaque élément de l’identificateur comme suit :<br /><br /> Sélectionnez \`ma Table\`.\` Mon champ\` FROM \`ma Table »<br /><br /> Pour plus d’informations sur l’utilisation de jeux de résultats contenant des tableaux en tant que paramètres formels, consultez [retournant des paramètres de tableau à partir de procédures stockées](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md).|  
|**SQLRowCount**|Oracle ne fournit pas un moyen de déterminer le nombre de lignes un jeu de résultats jusqu'à ce qu’une fois que vous lisez la dernière ligne, par conséquent, elle retourne -1.|  
|**SQLSetCursorName**|Associe un nom de curseur avec un descripteur d’instruction active, *hstmt*.|  
|**SQLSetParam**|Remplacé par SQLBindParameter dans ODBC 2. *x*.|  
|**SQLTransact**|Demande une opération commit ou rollback pour toutes les opérations actives sur tous les descripteurs d’instruction (hstmts) associés à une connexion, ou pour toutes les connexions associées le handle d’environnement, *henv*. Si une validation échoue en mode manuel, la transaction reste active ; Vous pouvez choisir de restaurer la transaction ou recommencez l’opération de validation. Si une opération de validation échoue en mode de transaction automatique, la transaction est restaurée automatiquement ; la transaction ne peut pas être inactive.|
