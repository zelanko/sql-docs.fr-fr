---
title: Fonction SQLDriverToDataSource (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 89e7db7e4b20a35e047dca94cb72d8a6888fb670
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302750"
---
# <a name="sqldrivertodatasource-function"></a>SQLDriverToDataSource, fonction
**SQLDriverToDataSource** prend en charge les traductions pour les conducteurs d’ODBC. Cette fonction n’est pas appelée par les applications compatibles ODBC; les applications demandent la traduction par **SQLSetConnectAttr**. Le conducteur associé au *ConnectionHandle* spécifié dans **SQLSetConnectAttr** appelle le DLL spécifié pour effectuer des traductions de toutes les données qui circulent du conducteur à la source de données. Une traduction par défaut DLL peut être spécifiée dans le fichier de initialisation ODBC.  
  
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
 [Entrée] Le type de données SQL ODBC. Cet argument indique au conducteur comment convertir *rgbValueIn* dans un formulaire acceptable par la source de données. Pour une liste des types de données SQL valides, consultez [LES types de données SQL](../../../odbc/reference/appendixes/sql-data-types.md).  
  
 *rgbValueIn*  
 [Entrée] Valeur à traduire.  
  
 *cbValueIn*  
 [Entrée] Longueur de *rgbValueIn*.  
  
 *rgbValueOut (en)*  
 [Sortie] Résultat de la traduction.  
  
> [!NOTE]  
>  La traduction DLL ne met pas fin à cette valeur.  
  
 *cbValueOutMax (en)*  
 [Entrée] Longueur de *rgbValueOut*.  
  
 *pcbValueOut (en anglais)*  
 [Sortie] Le nombre total d’octets (à l’exclusion du octet de cessation d’emploi nul) disponible pour revenir en *rgbValueOut*.  
  
 Pour les données de caractère ou binaires, si cela est supérieur ou égal à *cbValueOutMax*, les données dans *rgbValueOut* est tronquée aux octets *cbValueOutMax.*  
  
 Pour tous les autres types de données, la valeur de *cbValueOutMax* est ignorée et la traduction DLL suppose que la taille de *rgbValueOut* est la taille du type de données C par défaut du type de données SQL spécifié avec *fSqlType*.  
  
 *L’argument pcbValueOut* peut être un pointeur nul.  
  
 *szErrorMsg*  
 [Sortie] Pointeur au stockage pour un message d’erreur. Il s’agit d’une chaîne vide à moins que la traduction n’ait échoué.  
  
 *cbErrorMsgMax*  
 [Entrée] Longueur de *szErrorMsg*.  
  
 *pcbErrorMsg*  
 [Sortie] Pointeur sur le nombre total d’octets (à l’exclusion du octet de cessation d’emploi nul) disponible pour revenir en *szErrorMsg*. Si cela est supérieur ou égal à *cbErrorMsg*, les données dans *szErrorMsg* est tronqué à *cbErrorMsgMax* moins le caractère de non-termination. *L’argument pcbErrorMsg* peut être un pointeur nul.  
  
## <a name="returns"></a>Retours  
 VRAI si la traduction a été réussie, FALSE si la traduction a échoué.  
  
## <a name="comments"></a>Commentaires  
 Le conducteur appelle **SQLDriverToDataSource** pour traduire toutes les données (déclarations SQL, paramètres, etc.) passant du conducteur à la source de données. La traduction DLL peut ne pas traduire certaines données, selon le type de données et le but de la traduction DLL. Par exemple, un DLL qui traduit les données de caractère d’une page de code à une autre ignore toutes les données numériques et binaires.  
  
 La valeur de *fOption* est définie à la valeur de *vParam* spécifiée en appelant **SQLSetConnectAttr** avec l’attribut SQL_ATTR_TRANSLATE_OPTION. Il s’agit d’une valeur 32 bits qui a une signification spécifique pour une traduction donnée DLL. Par exemple, il peut spécifier une certaine traduction de l’ensemble de caractères.  
  
 Si le même tampon est spécifié pour *rgbValueIn* et *rgbValueOut*, la traduction des données dans le tampon sera effectuée en place.  
  
 Bien que *cbValueIn*, *cbValueOutMax*, et *pcbValueOut* sont du type SDWORD, **SQLDriverToDataSource** ne prend pas nécessairement en charge d’énormes pointeurs.  
  
 Si **SQLDriverToDataSource** renvoie FALSE, la troncation de données aurait pu se produire pendant la traduction. Si *pcbValueOut* (le nombre d’octets disponibles pour revenir dans le tampon de sortie) est supérieur à *cbValueOutMax* (la longueur du tampon de sortie), alors la troncation s’est produite. Le conducteur doit déterminer si la troncation était acceptable ou non. Si la troncation n’a pas eu lieu, le **SQLDriverToDataSource** a retourné FALSE en raison d’une autre erreur. Dans les deux cas, un message d’erreur spécifique est retourné dans *szErrorMsg*.  
  
 Pour plus d’informations sur la traduction des données, voir [Traduction DLLs](../../../odbc/reference/develop-app/translation-dlls.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Traduire les données issues de la source de données|[SQLDataSourceToDriver](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|  
|Retour du paramètre d’un attribut de connexion|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Définir un attribut de connexion|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
