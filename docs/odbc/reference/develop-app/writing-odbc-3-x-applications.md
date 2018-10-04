---
title: Écriture d’Applications ODBC 3.x | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], about upgrading
- ODBC drivers [ODBC], backward compatibility
- upgrading applications [ODBC]
- compatibility [ODBC], upgrading applications
- application upgrades [ODBC]
- upgrading applications [ODBC], about upgrading
- backward compatibility [ODBC], upgrading applications
ms.assetid: 19c54fc5-9dd6-49b6-8c9f-a38961b40a65
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 93c8510bb23bb57244590a472073fc882f9fe64f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47769147"
---
# <a name="writing-odbc-3x-applications"></a>Écriture d’applications ODBC 3.x
Lorsqu’une application ODBC 2. *x* application est mis à niveau vers ODBC 3. *x*, elle doit être écrite de sorte qu’il fonctionne avec ODBC 2. *x* et 3. *x* pilotes. L’application doit incorporer le code conditionnel pour tirer pleinement parti de ODBC 3. *x* fonctionnalités.  
  
 L’attribut d’environnement SQL_ATTR_ODBC_VERSION doit être définie à SQL_OV_ODBC2. Cela garantit que le pilote se comporte comme un ODBC 2 *.x* pilote en ce qui concerne les modifications décrites dans la section [des changements de comportement](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 Si l’application utilise les fonctionnalités décrites dans la section [nouvelles fonctionnalités](../../../odbc/reference/develop-app/new-features.md), code conditionnel doit être utilisé pour déterminer si le pilote est un ODBC 3. *x* ou ODBC 2 *.x* pilote. L’application utilise **SQLGetDiagField** et **SQLGetDiagRec** obtenir ODBC 3. *x* SQLSTATE tout en erreur lors du traitement sur ces fragments de code conditionnel. Prenez en compte les points suivants concernant les nouvelles fonctionnalités :  
  
-   Une application affectée par le changement de comportement de taille d’ensemble de lignes doit être veiller à ne pas appeler **SQLFetch** lorsque la taille du tableau est supérieure à 1. Ces applications doivent remplacer les appels aux **SQLExtendedFetch** avec les appels à **SQLSetStmtAttr** pour définir l’attribut d’instruction SQL_ATTR_ARRAY_STATUS_PTR et **SQLFetchScroll**, afin qu’ils aient un code commun qui fonctionne avec les deux ODBC 3. *x* et ODBC 2. *x* pilotes. Étant donné que **SQLSetStmtAttr** avec SQL_ATTR_ROW_ARRAY_SIZE sera mappé à **SQLSetStmtAttr** avec SQL_ROWSET_SIZE pour ODBC 2. *x* pilotes, les applications peuvent définir simplement SQL_ATTR_ROW_ARRAY_SIZE pour leurs opérations d’extraction de plusieurs lignes.  
  
-   La plupart des applications qui sont la mise à niveau ne sont pas réellement affectés par des modifications dans les codes SQLSTATE. Pour les applications qui sont affectées, ils peuvent effectuer une recherche mécanique et remplacer dans la plupart des cas à l’aide de la table de conversion d’erreur dans la section « Mappage SQLSTATE » pour convertir ODBC 3. *x* codes d’erreur à ODBC 2 *.x* codes. Depuis le 3 ODBC *.x* Gestionnaire de pilotes effectuera le mappage à partir d’ODBC 2. *x* SQLSTATE pour ODBC 3. *x* SQLSTATE, ces créateurs d’applications a besoin uniquement de vérification pour ODBC 3. *x* SQLSTATE et sans vous soucier, y compris ODBC 2. *x* SQLSTATE dans le code conditionnel.  
  
-   Si une application utilise superbement date, heure et types de données timestamp, l’application peut se déclarer à être un ODBC 2. *x* application et utiliser ses code au lieu d’utiliser le code de climatisation.  
  
 La mise à niveau doit également inclure les étapes suivantes :  
  
-   Appelez **SQLSetEnvAttr** avant d’allouer une connexion pour la valeur de l’attribut d’environnement SQL_ATTR_ODBC_VERSION SQL_OV_ODBC2.  
  
-   Remplacez tous les appels à **SQLAllocEnv**, **SQLAllocConnect**, ou **SQLAllocStmt** avec les appels à **SQLAllocHandle** avec le bon *HandleType* argument de SQL_HANDLE_ENV, SQL_HANDLE_DBC ou SQL_HANDLE_STMT.  
  
-   Remplacez tous les appels à **SQLFreeEnv** ou **SQLFreeConnect** avec les appels à **SQLFreeHandle** avec le bon *HandleType* argument de SQL_HANDLE_DBC ou SQL_HANDLE_STMT.  
  
-   Remplacez tous les appels à **SQLSetConnectOption** avec les appels à **SQLSetConnectAttr**. Si la définition d’un attribut dont la valeur est une chaîne, définissez le *StringLength* argument en conséquence. Modification *attribut* argument à partir de SQL_XXXX à SQL_ATTR_XXXX.  
  
-   Remplacez tous les appels à **SQLGetConnectOption** avec les appels à **SQLGetConnectAttr**. Si vous obtenez une chaîne ou un attribut binaire, définissez *BufferLength* à la valeur appropriée et passez un *StringLength* argument. Modification *attribut* argument à partir de SQL_XXXX à SQL_ATTR_XXXX.  
  
-   Remplacez tous les appels à **SQLSetStmtOption** avec les appels à **SQLSetStmtAttr**. Si la définition d’un attribut dont la valeur est une chaîne, définissez le *StringLength* argument en conséquence. Modification *attribut* argument à partir de SQL_XXXX à SQL_ATTR_XXXX.  
  
-   Remplacez tous les appels à **SQLGetStmtOption** avec les appels à **SQLGetStmtAttr**. Si vous obtenez une chaîne ou un attribut binaire, définissez *BufferLength* à la valeur appropriée et passez un *StringLength* argument. Modification *attribut* argument à partir de SQL_XXXX à SQL_ATTR_XXXX.  
  
-   Remplacez tous les appels à **SQLTransact** avec les appels à **SQLEndTran**. Si le handle valid plus à droite dans le **SQLTransact** appel est un handle d’environnement, un *HandleType* argument de SQL_HANDLE_ENV doit être utilisé dans le **SQLEndTran** appeler avec approprié *gérer* argument. Si le handle valid plus à droite dans votre **SQLTransact** appel est un handle de connexion, un *HandleType* argument de SQL_HANDLE_DBC doit être utilisé dans le **SQLEndTran** appeler avec approprié *gérer* argument.  
  
-   Remplacez tous les appels à **SQLColAttributes** avec les appels à **SQLColAttribute**. Si le *FieldIdentifier* argument est SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE ou SQL_COLUMN_LENGTH, ne modifiez rien d’autre que le nom de la fonction. Dans le cas contraire, modifiez *FieldIdentifier* de SQL_COLUMN_XXXX à SQL_DESC_XXXX. Si *FieldIdentifier* est SQL_DESC_CONCISE_TYPE et le type de données est un type de données datetime, remplacez le correspondantes ODBC 3 *.x* type de données.  
  
-   Si vous utilisez les curseurs de bloc, curseurs avec défilement ou les deux, l’application effectue les opérations suivantes :  
  
    -   Définit la taille de l’ensemble de lignes, d’un type de curseur et d’une concurrence de curseur à l’aide **SQLSetStmtAttr**.  
  
    -   Appels **SQLSetStmtAttr** définir SQL_ATTR_ROW_STATUS_PTR pour pointer vers un tableau d’enregistrements d’état.  
  
    -   Appels **SQLSetStmtAttr** définir SQL_ATTR_ROWS_FETCHED_PTR pour pointer vers un SQLINTEGER.  
  
    -   Effectue les liaisons requises et exécute l’instruction SQL.  
  
    -   Appels **SQLFetchScroll** dans une boucle pour extraire les lignes et les déplacer dans le résultat défini.  
  
    -   S’il souhaite extraire par signet, l’application appelle **SQLSetStmtAttr** pour définir SQL_ATTR_FETCH_BOOKMARK_PTR à une variable qui contiendra le signet pour la ligne qu’il souhaite extraire et appelle **SQLFetchScroll** avec un *FetchOrientation* argument de SQL_FETCH_BOOKMARK.  
  
-   Si vous utilisez des tableaux de paramètres, l’application effectue les opérations suivantes :  
  
    -   Appels **SQLSetStmtAttr** pour définir l’attribut SQL_ATTR_PARAMSET_SIZE à la taille du tableau de paramètres.  
  
    -   Appels **SQLSetStmtAttr** définir SQL_ATTR_ROWS_PROCESSED_PTR pour pointer vers une variable UDWORD interne.  
  
    -   Effectue préparer, lier et exécuter des opérations comme il convient.  
  
    -   Si l’exécution s’arrête pour une raison quelconque (par exemple, SQL_NEED_DATA), il peut trouver la ligne « actuelle » des paramètres en examinant l’emplacement désigné par SQL_ATTR_ROWS_PROCESSED_PTR.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Mappage des fonctions de remplacement pour la compatibilité descendante des applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
-   [Appel de SQLCloseCursor](../../../odbc/reference/develop-app/calling-sqlclosecursor.md)  
  
-   [Appel de SQLGetDiagField](../../../odbc/reference/develop-app/calling-sqlgetdiagfield.md)  
  
-   [Appel de SQLSetPos](../../../odbc/reference/develop-app/calling-sqlsetpos.md)  
  
-   [Opérations de bibliothèque de curseurs](../../../odbc/reference/develop-app/cursor-library-operations.md)  
  
-   [Mappage des types d’informations Attributes1 du curseur](../../../odbc/reference/develop-app/mapping-the-cursor-attributes1-information-types.md)  
  
-   [SQL_NO_DATA](../../../odbc/reference/develop-app/sql-no-data.md)
