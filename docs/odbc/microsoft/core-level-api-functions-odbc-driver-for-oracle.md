---
title: Fonctions API de niveau de base (ODBC Driver pour Oracle) Microsoft Docs
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
ms.openlocfilehash: 19751bb6d0556b117d0a73967d4db00c408733ac
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281019"
---
# <a name="core-level-api-functions-odbc-driver-for-oracle"></a>Fonctions de l’API du niveau principal (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Les fonctions à ce niveau comprennent le niveau minimum de conformité d’interface pour les pilotes ODBC.  
  
|Fonction API|Notes|  
|------------------|-----------|  
|**SQLAllocConnect (SQLAllocConnect)**|Alloue la mémoire pour une poignée de connexion, *hdbc*, dans l’environnement identifié par *henv*. Le Gestionnaire de pilote traite cet appel et appelle la fonction **SQLAllocConnect** du conducteur chaque fois que **SQLConnect**, **SQLBrowseConnect**, ou **SQLDriverConnect** est appelé.|  
|**SQLAllocEnv**|Affiche une boîte de dialogue spécifiant l’exigence pour le logiciel Client Oracle, puis retourne SQL_NULL_HANDLE. Si le logiciel Oracle Client n’est pas installé, cette fonction alloue la mémoire pour une poignée d’environnement, *henv,* et initialise l’interface de niveau d’appel ODBC pour une utilisation par une application.|  
|**SQLAllocStmt**|Alloue la mémoire pour une poignée de relevé et associe la poignée de déclaration avec la connexion spécifiée par hdbc. Le Driver Manager passe cet appel au conducteur, qui alloue la mémoire pour la structure hstmt.|  
|**SQLBindCol**|Assigne l’espace de stockage pour une colonne de résultat et spécifie le type de résultat.|  
|**SQLCancel**|Annule le traitement sur une poignée de relevé, hstmt. Dans certains cas, Oracle n’autorise pas l’annulation d’une déclaration en cours d’exécution. Cela signifie qu’une déclaration en cours d’exécution se poursuivra jusqu’à ce qu’Oracle termine le processus, date à laquelle les résultats des déclarations sont annulés par le pilote ODBC pour Oracle.|  
|**SQLColAttributes**|Renvoie les informations descripteur pour une colonne dans un ensemble de résultats. Les informations descripteur sont retournées comme une chaîne de caractère, une valeur descripteur-dépendante de 32 bits, ou une valeur d’intégrateur.|  
|**SQLConnect**|Se connecte à une source de données. Pour utiliser l’authentification du système d’exploitation Oracle, spécifiez "/" comme paramètre *szUID* et "" comme paramètre *szAuthStr.*|  
|**SQLDescribeCol**|Renvoie le nom, le type, la précision, l’échelle et la nullabilité de la colonne de résultat donnée. **Remarque : SQLDescribeCol** rapporte des colonnes calculées comme SQL_VARCHAR.|  
|**SQLDisconnect**|Ferme une connexion. Si la mise en commun des connexions est activée pour un environnement partagé et qu’une application appelle **SQLDisconnect** sur une connexion dans cet environnement, la connexion est retournée au pool de connexion et est toujours disponible pour d’autres composants utilisant le même environnement partagé.|  
|**Sqlerror**|Renvoie les informations d’erreur ou de statut sur la dernière erreur. Le conducteur maintient une pile ou une liste d’erreurs qui peuvent être retournées pour le *hstmt*, *hdbc*, et *henv* arguments, en fonction de la façon dont l’appel à **SQLError** est faite. La file d’attente d’erreur est rincée après chaque instruction. Récupère habituellement un message d’erreur Oracle et est par ailleurs vide.|  
|**SQLExecDirect**|Exécute une nouvelle déclaration SQL non préparée. Le conducteur utilise les valeurs actuelles des variables de marqueur de paramètres si des paramètres existent dans l’instruction. Si votre table, vue ou noms de champ contiennent des espaces, enfermez les noms dans les guillemets arrière. Par exemple, si votre base de données contient une table nommée *Ma Table* et le champ *Mon champ,* enfermer chaque élément de l’identifiant comme tel:<br /><br /> SÉLECTIONNEz \`\`Ma table . \`Mon Champ1\`,; \`Ma\`table . \`Mon\` champ2 \`de ma table\`|  
|**SQLExecute**|Exécute une déclaration SQL préparée (une déclaration déjà préparée par **SQLPrepare**). Le conducteur utilise les valeurs actuelles des variables de marqueur de paramètres si des paramètres existent dans l’instruction.|  
|**SQLFetch**|Récupère une rangée à partir d’un résultat défini dans les endroits spécifiés par les appels précédents à **SQLBindCol**. Prépare le conducteur pour un appel à **SQLGetData** pour les colonnes non liées.|  
|**SQLFreeConnect (en anglais)**|Libère une poignée de connexion et libère toute la mémoire allouée à la poignée.|  
|**SQLFreeEnv**|Ferme le pilote ODBC pour Oracle et libère toute mémoire associée au pilote.|  
|**SQLFreeStmt**|Arrête le traitement associé à un hstmt spécifique, ferme tous les curseurs ouverts associés à la hstmt, rejette les résultats en attente et libère par option toutes les ressources associées à la poignée de déclaration.|  
|**SQLGetCursorName**|Retourne le nom du curseur associé à la hstmt donnée.|  
|**SQLNumResultCols**|Retourne le nombre de colonnes dans un curseur défini par résultat.|  
|**SQLPrepare**|Prépare une déclaration SQL en planifiant comment optimiser et exécuter l’instruction. La déclaration SQL est compilée pour exécution par **SQLExecDirect**.<br /><br /> Si votre table, vue ou noms de champ contiennent des espaces, enfermez les noms dans les guillemets arrière. Par exemple, si votre base de données contient une table nommée *Ma Table* et le champ *Mon champ,* regroupez chaque élément de l’identifiant comme suit :<br /><br /> SÉLECTIONNEz \`\`Ma table . \`Mon\` champ \`de ma table\`<br /><br /> Pour plus d’informations sur l’utilisation d’ensembles de résultats contenant des tableaux comme paramètres formels, voir [paramètres de tableau de retour des procédures stockées](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md).|  
|**SQLRowCount**|Oracle ne fournit pas un moyen de déterminer le nombre de lignes dans un résultat réglé jusqu’à ce que vous allez chercher la dernière rangée, de sorte qu’il retourne -1.|  
|**SQLSetCursorName**|Associe un nom de curseur avec une poignée de relevé actif, *hstmt*.|  
|**SQLSetParam (SQLSetParam)**|Remplacé par SQLBindParameter dans ODBC 2. *x*.|  
|**SQLTransacte**|Demande une opération de validation ou de restauration pour toutes les opérations actives sur toutes les poignées de relevé (hstmts) associées à une connexion, ou pour toutes les connexions associées à la poignée de l’environnement, *henv*. Si un commit échoue en mode manuel, la transaction reste active; vous pouvez choisir de annuler la transaction ou de réessayer l’opération de validation. Si une opération de validation échoue en mode transaction automatique, la transaction est annulée automatiquement; la transaction ne peut pas être inactive.|
