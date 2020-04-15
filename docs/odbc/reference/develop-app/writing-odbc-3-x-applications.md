---
title: Rédaction d’applications ODBC 3.x (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3ba48d76babcaa5fcc49a541088f7c4cc349b569
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288987"
---
# <a name="writing-odbc-3x-applications"></a>Écriture d’applications ODBC 3.x
Lorsqu’une application ODBC *2.x* est mise à niveau vers ODBC *3.x*, il devrait être écrit de telle sorte qu’il fonctionne avec les deux pilotes ODBC *2.x* et *3.x.* L’application doit incorporer le code conditionnel pour tirer pleinement parti des caractéristiques ODBC *3.x.*  
  
 L’attribut SQL_ATTR_ODBC_VERSION environnement doit être réglé pour SQL_OV_ODBC2. Cela permettra de s’assurer que le conducteur se comporte comme un pilote ODBC *2.x* en ce qui concerne les changements décrits dans la section [Changements comportementaux](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 Si l’application utilisera l’une des fonctionnalités décrites dans la section [Nouvelles Fonctionnalités](../../../odbc/reference/develop-app/new-features.md), le code conditionnel doit être utilisé pour déterminer si le conducteur est un pilote ODBC *3.x* ou ODBC *2.x.* L’application utilise **SQLGetDiagField** et **SQLGetDiagRec** pour obtenir ODBC *3.x* SQLSTATEs tout en effectuant un traitement d’erreur sur ces fragments de code conditionnel. Les points suivants sur la nouvelle fonctionnalité doivent être pris en considération :  
  
-   Une application affectée par le changement de comportement de taille de ramset doit être prudent de ne pas appeler **SQLFetch** lorsque la taille du tableau est supérieure à 1. Ces applications devraient remplacer les appels à **SQLExtendedFetch** par des appels à **SQLSetStmtAttr** pour définir l’attribut SQL_ATTR_ARRAY_STATUS_PTR déclaration et à **SQLFetchScroll**, de sorte qu’ils ont un code commun qui fonctionne avec les deux ODBC *3.x* et ODBC *2.x* pilotes. Étant donné que **SQLSetStmtAttr** avec SQL_ATTR_ROW_ARRAY_SIZE sera cartographié à **SQLSetStmtAttr** avec SQL_ROWSET_SIZE pour les conducteurs ODBC *2.x,* les applications peuvent simplement régler SQL_ATTR_ROW_ARRAY_SIZE pour leurs opérations de récupération multirow.  
  
-   La plupart des applications qui sont mises à niveau ne sont pas réellement affectées par les changements dans les codes SQLSTATE. Pour les applications qui sont touchées, ils peuvent effectuer une recherche mécanique et remplacer dans la plupart des cas en utilisant le tableau de conversion d’erreurs dans la section « Cartographie SQLSTATE » pour convertir les codes d’erreur ODBC *3.x* en codes ODBC *2.x.* Étant donné que l’ODBC *3.x* Driver Manager effectuera la cartographie de ODBC *2.x* SQLSTATEs à ODBC *3.x* SQLSTATEs, ces auteurs d’applications n’ont besoin que de vérifier les SQLSTATEs ODBC *3.x* et ne pas s’inquiéter d’inclure ODBC *2.x* SQLSTATEs en code conditionnel.  
  
-   Si une application utilise de grands types de données de date, d’heure et de timetamp, l’application peut se déclarer être une application ODBC *2.x* et utiliser son code existant au lieu d’utiliser le code de conditionnement.  
  
 La mise à niveau devrait également inclure les étapes suivantes :  
  
-   Appelez **SQLSetEnvAttr** avant d’allouer une connexion pour définir l’attribut SQL_ATTR_ODBC_VERSION environnement à SQL_OV_ODBC2.  
  
-   Remplacez tous les appels à **SQLAllocEnv**, **SQLAllocConnect**, ou **SQLAllocStmt** par des appels à **SQLAllocHandle** par l’argument *manipuleur* approprié de SQL_HANDLE_ENV, SQL_HANDLE_DBC ou SQL_HANDLE_STMT.  
  
-   Remplacez tous les appels à **SQLFreeEnv** ou **SQLFreeConnect** par des appels à **SQLFreeHandle** par l’argument *maniant* approprié de SQL_HANDLE_DBC ou SQL_HANDLE_STMT.  
  
-   Remplacez tous les appels vers **SQLSetConnectOption** par des appels vers **SQLSetConnectAttr**. Si vous définissez un attribut dont la valeur est une chaîne, définissez *l’argument StringLength* de manière appropriée. Changement *Argument d’attribut* de SQL_XXXX à SQL_ATTR_XXXX.  
  
-   Remplacez tous les appels vers **SQLGetConnectOption** par des appels vers **SQLGetConnectAttr**. Si vous obtenez une chaîne ou un attribut binaire, *définissez BufferLength* à la valeur appropriée et passez dans un argument *StringLength.* Changement *Argument d’attribut* de SQL_XXXX à SQL_ATTR_XXXX.  
  
-   Remplacez tous les appels à **SQLSetStmtOption** par des appels à **SQLSetStmtAttr**. Si vous définissez un attribut dont la valeur est une chaîne, définissez *l’argument StringLength* de manière appropriée. Changement *Argument d’attribut* de SQL_XXXX à SQL_ATTR_XXXX.  
  
-   Remplacez tous les appels à **SQLGetStmtOption** par des appels à **SQLGetStmtAttr**. Si vous obtenez une chaîne ou un attribut binaire, *définissez BufferLength* à la valeur appropriée et passez dans un argument *StringLength.* Changement *Argument d’attribut* de SQL_XXXX à SQL_ATTR_XXXX.  
  
-   Remplacez tous les appels à **SQLTransact** par des appels à **SQLEndTran**. Si la poignée la plus valide dans **l’appel SQLTransact** est une poignée d’environnement, un argument *HandleType* de SQL_HANDLE_ENV doit être utilisé dans **l’appel SQLEndTran** avec l’argument *de poignée* approprié. Si la poignée valide la plus droite dans votre appel **SQLTransact** est une poignée de connexion, un argument *HandleType* de SQL_HANDLE_DBC doit être utilisé dans **l’appel SQLEndTran** avec l’argument *de poignée* approprié.  
  
-   Remplacez tous les appels à **SQLColAttributes** par des appels à **SQLColAttribute**. Si l’argument *de FieldIdentifier* est soit SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE, ou SQL_COLUMN_LENGTH, ne changez rien d’autre que le nom de la fonction. Si ce n’est pas le cas, changez *FieldIdentifier* de SQL_COLUMN_XXXX à SQL_DESC_XXXX. Si *FieldIdentifier* est SQL_DESC_CONCISE_TYPE et que le type de données est un type de données date, modifiez-les pour le type de données ODBC *3.x* correspondant.  
  
-   Si vous utilisez des curseurs de blocs, des curseurs défilementables, ou les deux, l’application fait ce qui suit :  
  
    -   Définit la taille de l’aviron, le type de curseur et la concordance du curseur à l’aide **de SQLSetStmtAttr**.  
  
    -   Appelle **SQLSetStmtAttr** pour définir SQL_ATTR_ROW_STATUS_PTR pour indiquer un éventail d’enregistrements de statut.  
  
    -   Appelle **SQLSetStmtAttr** à mettre SQL_ATTR_ROWS_FETCHED_PTR pour pointer vers un SQLINTEGER.  
  
    -   Exécute les fixations requises et exécute la déclaration SQL.  
  
    -   Appelle **SQLFetchScroll** en boucle pour aller chercher des rangées et se déplacer dans l’ensemble de résultats.  
  
    -   S’il veut aller chercher par signet, l’application appelle **SQLSetStmtAttr** pour définir SQL_ATTR_FETCH_BOOKMARK_PTR à une variable qui contiendra le signet de la ligne qu’il veut aller chercher, et appelle **SQLFetchScroll** avec un argument *d’orientation de* SQL_FETCH_BOOKMARK.  
  
-   Si vous utilisez des tableaux de paramètres, l’application fait ce qui suit :  
  
    -   Appelle **SQLSetStmtAttr** pour définir l’attribut SQL_ATTR_PARAMSET_SIZE à la taille du tableau de paramètres.  
  
    -   Appelle **SQLSetStmtAttr** à définir SQL_ATTR_ROWS_PROCESSED_PTR pour indiquer une variable interne UDWORD.  
  
    -   Effectue préparer, lier et exécuter les opérations, le cas échéant.  
  
    -   Si l’exécution s’arrête pour une raison quelconque (comme SQL_NEED_DATA), elle peut trouver la ligne de paramètres « actuelle » en inspectant l’emplacement indiqué par SQL_ATTR_ROWS_PROCESSED_PTR.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Mappage des fonctions de remplacement pour la compatibilité descendante des applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
-   [Appel de SQLCloseCursor](../../../odbc/reference/develop-app/calling-sqlclosecursor.md)  
  
-   [Appel de SQLGetDiagField](../../../odbc/reference/develop-app/calling-sqlgetdiagfield.md)  
  
-   [Appel de SQLSetPos](../../../odbc/reference/develop-app/calling-sqlsetpos.md)  
  
-   [Opérations de bibliothèque de curseurs](../../../odbc/reference/develop-app/cursor-library-operations.md)  
  
-   [Mappage des types d’informations Attributes1 du curseur](../../../odbc/reference/develop-app/mapping-the-cursor-attributes1-information-types.md)  
  
-   [SQL_NO_DATA](../../../odbc/reference/develop-app/sql-no-data.md)
