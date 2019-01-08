---
title: SQLDataSourceToDriver, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDataSourceToDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDataSourceToDriver
helpviewer_keywords:
- SQLDataSourceToDriver function [ODBC]
ms.assetid: 0d87fcac-30a0-4303-ad8f-a5b53f4b428d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a0ad4a98689db00c6dcb484e7a04bb973d2e1761
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53206258"
---
# <a name="sqldatasourcetodriver-function"></a>SQLDataSourceToDriver, fonction
**SQLDataSourceToDriver** supportstranslations pour les pilotes ODBC. Cette fonction n’est pas appelée par les applications prenant en charge ODBC ; applications demandent une traduction via **SQLSetConnectAttr**. Le pilote associé le *ConnectionHandle* spécifié dans **SQLSetConnectAttr** appelle la DLL spécifiée pour effectuer des traductions de tous les flux de données à partir de la source de données vers le pilote. Une DLL de traduction par défaut peut être spécifié dans le fichier d’initialisation ODBC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL SQLDataSourceToDriver(  
     UDWORD     fOption,  
     SWORD      fSqlType,  
     PTR        rgbValueIn,  
     SDWORD     cbValueIn,  
     PTR        rgbValueOut,  
     SDWORD     cbValueOutMax,  
     SDWORD *   pcbValueOut,  
     UCHAR *    szErrorMsg,  
     SWORD      cbErrorMsgMax,  
     SWORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>Arguments  
 *fOption*  
 [Entrée] Valeur de l’option.  
  
 *fSqlType*  
 [Entrée] Le type de données SQL. Cet argument indique au pilote de la conversion *rgbValueIn* dans un format acceptable par l’application. Pour obtenir la liste des types de données SQL valides, consultez la [les Types de données SQL](../../../odbc/reference/appendixes/sql-data-types.md) section dans l’annexe d : Types de données.  
  
 *rgbValueIn*  
 [Entrée] Valeur à convertir.  
  
 *cbValueIn*  
 [Entrée] Longueur de *rgbValueIn*.  
  
 *rgbValueOut*  
 [Sortie] Résultat de la traduction.  
  
> [!NOTE]  
>  La DLL de traduction ne null-termine pas cette valeur.  
  
 *cbValueOutMax*  
 [Entrée] Longueur de *rgbValueOut*.  
  
 *pcbValueOut*  
 [Sortie] Le nombre total d’octets (à l’exception de l’octet de caractère nul de terminaison) disponibles à renvoyer dans *rgbValueOut*.  
  
 Pour des données binaires, si cela est supérieur ou égal à ou caractères *cbValueOutMax*, les données dans *rgbValueOut* est tronqué à *cbValueOutMax* octets.  
  
 Pour tous les autres types de données, la valeur de *cbValueOutMax* est ignorée et la DLL de traduction suppose que la taille de *rgbValueOut* est la taille du type de données C par défaut du type de données SQL spécifié avec *fSqlType*.  
  
 Le *pcbValueOut* argument peut être un pointeur null.  
  
 *szErrorMsg*  
 [Sortie] Pointeur vers le stockage pour un message d’erreur. Il s’agit d’une chaîne vide, sauf si la conversion a échoué.  
  
 *cbErrorMsgMax*  
 [Entrée] Longueur de *szErrorMsg*.  
  
 *pcbErrorMsg*  
 [Sortie] Pointeur vers le nombre total d’octets (à l’exception de l’octet de caractère nul de terminaison) disponibles à renvoyer dans *szErrorMsg*. Si cela est supérieur ou égal à *cbErrorMsg*, les données dans *szErrorMsg* est tronqué à *cbErrorMsgMax* moins le caractère de fin de la valeur null. Le *pcbErrorMsg* argument peut être un pointeur null.  
  
## <a name="returns"></a>Valeur renvoyée  
 TRUE si la conversion a réussi, FALSE en cas d’échec de la traduction.  
  
## <a name="comments"></a>Commentaires  
 Le pilote appelle **SQLDataSourceToDriver** pour traduire alldata (données de jeu de résultats, les noms de tables, des nombres de lignes, les messages d’erreur et ainsi de suite) passant à partir des données source au pilote. La DLL de traduction ne peut pas convertir certaines données, selon le type et l’objectif de la traduction de DLL ; par exemple, une DLL qui se traduit par des données de caractères à partir d’une page de codes à l’autre ignore toutes les données numériques et binaire.  
  
 La valeur de *fOption* est défini sur la valeur de *vParam* spécifiée en appelant **SQLSetConnectAttr** avec l’attribut SQL_ATTR_TRANSLATE_OPTION. C’est une valeur de 32 bits qui a une signification spécifique pour une DLL de traduction donnée. Par exemple, il peut spécifier qu'un certain jeu de caractères traduction.  
  
 Si la même mémoire tampon est spécifiée pour *rgbValueIn* et *rgbValueOut*, la conversion des données dans la mémoire tampon sera effectuée en place.  
  
 Bien que *cbValueIn*, *cbValueOutMax*, et *pcbValueOut* sont du type SDWORD, **SQLDataSourceToDriver** ne prend pas nécessairement prend en charge les pointeurs énormes.  
  
 Si **SQLDataSourceToDriver** retourne FALSE, une troncation de données se sont produites lors de la traduction. Si *pcbValueOut* (le nombre d’octets à retourner dans le tampon de sortie) est supérieur à *cbValueOutMax* (la longueur de la mémoire tampon de sortie), puis de la troncation s’est produite. Le pilote doit déterminer si la troncation a acceptable. Si une troncation s’est pas produite, le **SQLDataSourceToDriver** a retourné FALSE en raison d’une autre erreur. Dans les deux cas, un message d’erreur spécifique est retourné dans *szErrorMsg*.  
  
 Pour plus d’informations sur la conversion de données, consultez [DLL de traduction](../../../odbc/reference/develop-app/translation-dlls.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Traduire les données envoyées à la source de données|[SQLDriverToDataSource](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|  
|Retourner le paramètre d’un attribut de connexion|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Définition d’un attribut de connexion|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
