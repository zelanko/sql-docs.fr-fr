---
title: SQLDriverToDataSource, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDriverToDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDriverToDataSource
helpviewer_keywords:
- SQLDriverToDataSource function [ODBC]
ms.assetid: 0de28eb5-8aa9-43e4-a87f-7dbcafe800dc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 844e11e72bb46b69229a9a4747ac7e64f013f14e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537169"
---
# <a name="sqldrivertodatasource-function"></a>SQLDriverToDataSource, fonction
**SQLDriverToDataSource** prend en charge des traductions pour les pilotes ODBC. Cette fonction n’est pas appelée par les applications prenant en charge ODBC ; applications demandent une traduction via **SQLSetConnectAttr**. Le pilote associé le *ConnectionHandle* spécifié dans **SQLSetConnectAttr** appelle la DLL spécifiée pour effectuer des traductions de tous les flux de données à partir du pilote vers la source de données. Une DLL de traduction par défaut peut être spécifié dans le fichier d’initialisation ODBC.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLDriverToDataSource(  
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
 [Entrée] Le type de données ODBC SQL. Cet argument indique au pilote de la conversion *rgbValueIn* dans un format acceptable par la source de données. Pour obtenir la liste des types de données SQL valides, consultez [les Types de données SQL](../../../odbc/reference/appendixes/sql-data-types.md).  
  
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
 Le pilote appelle **SQLDriverToDataSource** pour convertir toutes les données (instructions SQL, paramètres et ainsi de suite) en passant à partir du pilote à la source de données. La DLL de traduction ne peut pas convertir certaines données, selon le type et l’objectif de la DLL de traduction. Par exemple, une DLL qui se traduit par des données de caractères à partir d’une page de codes à l’autre ignore toutes les données numériques et binaire.  
  
 La valeur de *fOption* est défini sur la valeur de *vParam* spécifiée en appelant **SQLSetConnectAttr** avec l’attribut SQL_ATTR_TRANSLATE_OPTION. C’est une valeur de 32 bits qui a une signification spécifique pour une DLL de traduction donnée. Par exemple, il peut spécifier qu'un certain jeu de caractères traduction.  
  
 Si la même mémoire tampon est spécifiée pour *rgbValueIn* et *rgbValueOut*, la conversion des données dans la mémoire tampon sera effectuée en place.  
  
 Bien que *cbValueIn*, *cbValueOutMax*, et *pcbValueOut* sont du type SDWORD, **SQLDriverToDataSource** ne prend pas nécessairement prend en charge les pointeurs énormes.  
  
 Si **SQLDriverToDataSource** retourne FALSE, une troncation de données se sont produites lors de la traduction. Si *pcbValueOut* (le nombre d’octets à retourner dans le tampon de sortie) est supérieur à *cbValueOutMax* (la longueur de la mémoire tampon de sortie), puis de la troncation s’est produite. Le pilote doit déterminer si la troncation a été ou non acceptable. Si une troncation s’est pas produite, le **SQLDriverToDataSource** a retourné FALSE en raison d’une autre erreur. Dans les deux cas, un message d’erreur spécifique est retourné dans *szErrorMsg*.  
  
 Pour plus d’informations sur la conversion de données, consultez [DLL de traduction](../../../odbc/reference/develop-app/translation-dlls.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Traduire les données retournées par la source de données|[SQLDataSourceToDriver](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|  
|Retourner le paramètre d’un attribut de connexion|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Définition d’un attribut de connexion|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
