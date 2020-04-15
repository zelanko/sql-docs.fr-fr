---
title: Types spécifiques au conducteur - Données, Descripteur, Informations, Diagnostic Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver-specific diagnostic values [ODBC]
- diagnostic information [ODBC], driver-specific values
- ODBC drivers [ODBC], driver-specific diagnostic values
ms.assetid: ad4c76d3-5191-4262-b47c-5dd1d19d1154
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19bb2dd113fbeae871892ea510713c638c886e5a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305763"
---
# <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>Types de données spécifique du pilote, types de descripteurs, types d’informations, types de diagnostics et attributs
Les conducteurs peuvent attribuer des valeurs spécifiques au conducteur pour les éléments suivants :  
  
-   **Indicateurs de type de données SQL** Ceux-ci sont utilisés dans *ParameterType* dans **SQLBindParameter** et dans *DataType* dans **SQLGetTypeInfo** et retournés par **SQLColAttribute**, **SQLColumns**, **SQLDescribeCol**, **SQLGetTypeInfo**, **SQLDescribeParam**, **SQLProcedureColumns**, et **SQLSpecialColumns**.  
  
-   **Champs descripteur** Ceux-ci sont utilisés dans *FieldIdentifier* dans **SQLColAttribute**, **SQLGetDescField**, et **SQLSetDescField**.  
  
-   **Champs de diagnostic** Ceux-ci sont utilisés dans *DiagIdentifier* dans **SQLGetDiagField** et **SQLGetDiagRec**.  
  
-   **Types d’information** Ceux-ci sont utilisés dans *InfoType* dans **SQLGetInfo**.  
  
-   **Attributs de connexion et d’énoncé** Ceux-ci sont utilisés dans *Attribut* dans **SQLGetConnectAttr**, **SQLGetStmtAttr**, **SQLSetConnectAttr**, et **SQLSetStmtAttr**.  
  
 Pour chacun de ces éléments, il existe deux ensembles de valeurs : les valeurs réservées à l’utilisation par ODBC, et les valeurs réservées aux conducteurs. Avant de mettre en œuvre des valeurs spécifiques au conducteur, un auteur pilote doit demander une valeur pour chaque type, champ ou attribut spécifique au conducteur auprès d’Open Group. Pour le développement de nouveaux pilotes, utilisez la plage décrite dans le tableau ci-dessous. Le gestionnaire de conducteur ODBC 3.8 ne générera pas d’erreur si une valeur inconnue est utilisée qui n’est pas dans la plage décrite ci-dessous. Toutefois, les versions ultérieures du Gestionnaire de pilote peuvent générer une erreur si des valeurs inconnues sont reçues qui ne sont pas dans la plage.  
  
 Lorsque l’une de ces valeurs est transmise à une fonction ODBC, le conducteur doit vérifier si la valeur est valide. Les conducteurs retournent SQLSTATE HYC00 (fonction facultative non mise en œuvre) pour les valeurs spécifiques au conducteur qui s’appliquent aux autres conducteurs.  
  
 En commençant par ODBC 3.8, les auteurs de pilotes peuvent attribuer des attributs spécifiques au conducteur dans une plage réservée.  
  
> [!NOTE]  
>  L’ODBC 3.8 Driver Manager ne valide ni n’applique ces plages pour la compatibilité vers l’arrière. Une future version du Driver Manager pourrait toutefois les appliquer.  
  
|Type d'attribut|Type de données ODBC|Base de portée spécifique au conducteur|Limite de portée spécifique au conducteur|ODBC constante pour la base de gamme de valeur spécifique au conducteur|  
|--------------------|--------------------|---------------------------------|----------------------------------|---------------------------------------------------------|  
|Indicateurs de type de données SQL|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_SQL_TYPE_BASE|  
|Champs descripteur|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DESCRIPTOR_BASE|  
|Domaines diagnostiques|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DIAGNOSTIC_BASE|  
|Types d’information|SQLUSMALLINT|0x4000|0x7FFF|SQL_DRIVER_INFO_TYPE_BASE|  
|Attributs de connexion|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_CONNECT_ATTR_BASE|  
|Attributs de déclaration|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_STATEMENT_ATTR_BASE|  
  
> [!NOTE]  
>  Les types de données spécifiques au conducteur, les champs descripteurs, les champs de diagnostic, les types d’information, les attributs de déclaration et les attributs de connexion doivent être décrits dans la documentation du conducteur. Lorsque l’une de ces valeurs est transmise à une fonction ODBC, le conducteur doit vérifier si la valeur est valide. Les conducteurs retournent SQLSTATE HYC00 (fonction facultative non mise en œuvre) pour les valeurs spécifiques au conducteur qui s’appliquent aux autres conducteurs.  
  
 Les valeurs de base sont définies pour faciliter le développement du conducteur. Par exemple, les attributs diagnostiques spécifiques au conducteur peuvent être définis dans le format suivant :  
  
```  
SQL_DRIVER_DIAGNOSTIC_BASE+0, SQL_DRIVER_DIAGNOSTIC_BASE +1  
```
