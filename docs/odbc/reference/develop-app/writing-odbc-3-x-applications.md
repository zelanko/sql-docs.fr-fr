---
title: Écriture d’applications ODBC 3. x | Microsoft Docs
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
ms.openlocfilehash: 9939d11e3a779cc25d7faeb4950783353947f140
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081456"
---
# <a name="writing-odbc-3x-applications"></a>Écriture d’applications ODBC 3.x
Quand une application ODBC *2. x* est mise à niveau vers ODBC *3. x*, elle doit être écrite de telle sorte qu’elle fonctionne avec les pilotes ODBC *2. x* et *3. x* . L’application doit incorporer du code conditionnel pour tirer pleinement parti des fonctionnalités ODBC *3. x* .  
  
 L’attribut d’environnement SQL_ATTR_ODBC_VERSION doit avoir la valeur SQL_OV_ODBC2. Cela permet de s’assurer que le pilote se comporte comme un pilote ODBC *2. x* en ce qui concerne les modifications décrites dans la section [changements de comportement](../../../odbc/reference/develop-app/behavioral-changes.md).  
  
 Si l’application utilise l’une des fonctionnalités décrites dans la section [nouvelles fonctionnalités](../../../odbc/reference/develop-app/new-features.md), vous devez utiliser le code conditionnel pour déterminer si le pilote est un pilote ODBC *3. x* ou ODBC *2. x* . L’application utilise **SQLGetDiagField** et **SQLGetDiagRec** pour obtenir les SQLSTATE ODBC *3. x* lors du traitement des erreurs sur ces fragments de code conditionnel. Les points suivants sur la nouvelle fonctionnalité doivent être pris en compte :  
  
-   Une application affectée par la modification du comportement de la taille de l’ensemble de lignes doit veiller à ne pas appeler **SQLFetch** lorsque la taille du tableau est supérieure à 1. Ces applications doivent remplacer les appels à **SQLExtendedFetch** par des appels à **SQLSetStmtAttr** pour définir l’attribut d’instruction SQL_ATTR_ARRAY_STATUS_PTR et à **SQLFetchScroll**, afin qu’ils aient un code commun qui fonctionne avec les pilotes ODBC *3. x* et ODBC *2. x* . Étant donné que la valeur **SQLSetStmtAttr** avec SQL_ATTR_ROW_ARRAY_SIZE sera mappée à **SQLSetStmtAttr** avec SQL_ROWSET_SIZE pour les pilotes ODBC *2. x* , les applications peuvent simplement définir des SQL_ATTR_ROW_ARRAY_SIZE pour leurs opérations d’extraction multiligne.  
  
-   La plupart des applications qui effectuent la mise à niveau ne sont pas réellement affectées par les modifications apportées aux codes SQLSTATE. Pour les applications qui sont affectées, elles peuvent effectuer une recherche mécanique et remplacer dans la plupart des cas à l’aide du tableau de conversion des erreurs de la section « mappage SQLSTATE » pour convertir les codes d’erreur ODBC *3. x* en codes ODBC *2. x* . Étant donné que le gestionnaire de pilotes ODBC *3. x* effectue le mappage des SQLSTATE ODBC *2. x* à ODBC *3. x* sqlstates, ces Writers d’application n’ont besoin que de vérifier les SQLSTATE ODBC *3* . x et ne se soucient pas d’inclure les SQLSTATE ODBC *2. x* dans le code conditionnel.  
  
-   Si une application utilise des types de données de date, d’heure et d’horodatage, elle peut être déclarée comme étant une application ODBC *2. x* et utiliser son code existant au lieu d’utiliser le code de conditionnement.  
  
 La mise à niveau doit également inclure les étapes suivantes :  
  
-   Appelez **SQLSetEnvAttr** avant d’allouer une connexion pour affecter à l’attribut d’environnement SQL_ATTR_ODBC_VERSION la valeur SQL_OV_ODBC2.  
  
-   Remplacez tous les appels à **SQLAllocEnv**, **SQLAllocConnect**ou **SQLAllocStmt,** par des appels à **SQLAllocHandle** avec l’argument *comme HandleType* approprié de SQL_HANDLE_ENV, SQL_HANDLE_DBC ou SQL_HANDLE_STMT.  
  
-   Remplacez tous les appels à **sqlfreeenv,** ou **sqlfreeconnect,** par les appels à **SQLFreeHandle** avec l’argument *comme HandleType* approprié de SQL_HANDLE_DBC ou SQL_HANDLE_STMT.  
  
-   Remplacez tous les appels à **SQLSetConnectOption** par des appels à **SQLSetConnectAttr**. Si vous définissez un attribut dont la valeur est une chaîne, définissez l’argument *StringLength* de manière appropriée. Remplacez l’argument d' *attribut* SQL_XXXX par SQL_ATTR_XXXX.  
  
-   Remplacez tous les appels à **sqlgetconnectoption,** par des appels à **SQLGetConnectAttr**. Si vous obtenez un attribut de chaîne ou binaire, affectez à *BufferLength* la valeur appropriée et transmettez un argument *StringLength* . Remplacez l’argument d' *attribut* SQL_XXXX par SQL_ATTR_XXXX.  
  
-   Remplacez tous les appels à **SQLSetStmtOption** par des appels à **SQLSetStmtAttr**. Si vous définissez un attribut dont la valeur est une chaîne, définissez l’argument *StringLength* de manière appropriée. Remplacez l’argument d' *attribut* SQL_XXXX par SQL_ATTR_XXXX.  
  
-   Remplacez tous les appels à **SQLGetStmtOption** par des appels à **SQLGetStmtAttr**. Si vous obtenez un attribut de chaîne ou binaire, affectez à *BufferLength* la valeur appropriée et transmettez un argument *StringLength* . Remplacez l’argument d' *attribut* SQL_XXXX par SQL_ATTR_XXXX.  
  
-   Remplacez tous les appels à **SQLTransact** par des appels à **SQLEndTran**. Si le handle valide le plus à droite dans l’appel **SQLTransact** est un handle d’environnement, un argument *comme HandleType* de SQL_HANDLE_ENV doit être utilisé dans l’appel **SQLEndTran** avec l’argument de *handle* approprié. Si le handle valide le plus à droite dans votre appel **SQLTransact** est un handle de connexion, un argument *comme HandleType* de SQL_HANDLE_DBC doit être utilisé dans l’appel **SQLEndTran** avec l’argument de *handle* approprié.  
  
-   Remplacez tous les appels à **SQLColAttributes** par des appels à **SQLColAttribute**. Si l’argument *FieldIdentifier* est SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE ou SQL_COLUMN_LENGTH, ne modifiez rien autre que le nom de la fonction. Si ce n’est pas le cas, remplacez *FieldIdentifier* SQL_COLUMN_XXXX par SQL_DESC_XXXX. Si *FieldIdentifier* est SQL_DESC_CONCISE_TYPE et que le type de données est un type de données DateTime, remplacez-le par le type de données ODBC *3. x* correspondant.  
  
-   Si vous utilisez des curseurs de bloc, des curseurs de défilement, ou les deux, l’application effectue les opérations suivantes :  
  
    -   Définit la taille de l’ensemble de lignes, le type de curseur et l’accès concurrentiel du curseur à l’aide de **SQLSetStmtAttr**.  
  
    -   Appelle **SQLSetStmtAttr** pour définir SQL_ATTR_ROW_STATUS_PTR pour qu’il pointe vers un tableau d’enregistrements d’État.  
  
    -   Appelle **SQLSetStmtAttr** pour définir SQL_ATTR_ROWS_FETCHED_PTR pour pointer vers un SQLINTEGER destinée.  
  
    -   Exécute les liaisons requises et exécute l’instruction SQL.  
  
    -   Appelle **SQLFetchScroll** dans une boucle pour extraire des lignes et se déplacer dans le jeu de résultats.  
  
    -   S’il souhaite effectuer une extraction par signet, l’application appelle **SQLSetStmtAttr** pour définir SQL_ATTR_FETCH_BOOKMARK_PTR sur une variable qui contiendra le signet de la ligne qu’il souhaite extraire, et appelle **SQLFetchScroll** avec un argument *FetchOrientation* de SQL_FETCH_BOOKMARK.  
  
-   Si vous utilisez des tableaux de paramètres, l’application effectue les opérations suivantes :  
  
    -   Appelle **SQLSetStmtAttr** pour affecter à l’attribut SQL_ATTR_PARAMSET_SIZE la taille du tableau de paramètres.  
  
    -   Appelle **SQLSetStmtAttr** pour définir SQL_ATTR_ROWS_PROCESSED_PTR de manière à pointer vers une variable interne UDWORD.  
  
    -   Effectue les opérations prepare, bind et Execute, le cas échéant.  
  
    -   Si l’exécution s’arrête pour une raison quelconque (par exemple SQL_NEED_DATA), elle peut trouver la ligne « actuelle » de paramètres en inspectant l’emplacement désigné par SQL_ATTR_ROWS_PROCESSED_PTR.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Mappage des fonctions de remplacement pour la compatibilité descendante des applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
-   [Appel de SQLCloseCursor](../../../odbc/reference/develop-app/calling-sqlclosecursor.md)  
  
-   [Appel de SQLGetDiagField](../../../odbc/reference/develop-app/calling-sqlgetdiagfield.md)  
  
-   [Appel de SQLSetPos](../../../odbc/reference/develop-app/calling-sqlsetpos.md)  
  
-   [Opérations de bibliothèque de curseurs](../../../odbc/reference/develop-app/cursor-library-operations.md)  
  
-   [Mappage des types d’informations Attributes1 du curseur](../../../odbc/reference/develop-app/mapping-the-cursor-attributes1-information-types.md)  
  
-   [SQL_NO_DATA](../../../odbc/reference/develop-app/sql-no-data.md)
