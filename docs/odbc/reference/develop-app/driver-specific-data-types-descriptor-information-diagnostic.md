---
title: Diagnostic de descripteur, d’informations, de Types spécifiques au pilote - Data, | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30c310e6c6b2833da6e1d9167faee2e979bb4616
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47855317"
---
# <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>Types de données spécifique du pilote, types de descripteurs, types d’informations, types de diagnostics et attributs
Pilotes peuvent allouer des valeurs spécifiques au pilote pour les éléments suivants :  
  
-   **Indicateurs de Type de données SQL** ils sont utilisés dans *ParameterType* dans **SQLBindParameter** et dans *DataType* dans **SQLGetTypeInfo** et retournée par **SQLColAttribute**, **SQLColumns**, **SQLDescribeCol**, **SQLGetTypeInfo**,  **SQLDescribeParam**, **SQLProcedureColumns**, et **SQLSpecialColumns**.  
  
-   **Champs de descripteur** ils sont utilisés dans *FieldIdentifier* dans **SQLColAttribute**, **SQLGetDescField**, et **SQLSetDescField**.  
  
-   **Champs de diagnostic** ils sont utilisés dans *DiagIdentifier* dans **SQLGetDiagField** et **SQLGetDiagRec**.  
  
-   **Types d’informations** ils sont utilisés dans *InfoType* dans **SQLGetInfo**.  
  
-   **Connexion et les attributs d’instruction** ils sont utilisés dans *attribut* dans **SQLGetConnectAttr**, **SQLGetStmtAttr**,  **SQLSetConnectAttr**, et **SQLSetStmtAttr**.  
  
 Pour chacun de ces éléments, il existe deux ensembles de valeurs : valeurs réservées pour une utilisation par ODBC et réservée pour une utilisation par les pilotes. Avant d’implémenter les valeurs spécifiques au pilote, un writer de pilote doit demander une valeur pour chaque type spécifique au pilote, le champ ou l’attribut à partir d’Open Group. Pour le développement de nouveau pilote, utilisez la plage décrite dans le tableau ci-dessous. Le Gestionnaire de pilote de ODBC 3.8 pas génère une erreur si une valeur inconnue est utilisée qui n’est pas dans la plage décrite ci-dessous. Toutefois, les versions ultérieures du Gestionnaire de pilotes peuvent générer une erreur si les valeurs inconnues sont reçus qui ne sont pas dans la plage.  
  
 Lorsqu’une de ces valeurs est passé à une fonction ODBC, le pilote doit vérifier si la valeur est valide. Pilotes retournent SQLSTATE HYC00 (fonctionnalité facultative non implémentée) pour les valeurs spécifiques au pilote qui s’appliquent à d’autres pilotes.  
  
 À compter d’ODBC 3.8, enregistreurs de pilote peuvent allouer des attributs spécifiques au pilote dans une plage réservée.  
  
> [!NOTE]  
>  Le Gestionnaire de pilote de ODBC 3.8 valide ni n’applique ces plages pour la compatibilité descendante. Une future version du Gestionnaire de pilotes peut appliquer les, toutefois.  
  
|Type d'attribut|Type de données ODBC|Plage spécifiques au pilote de base|Limite de plage de spécifiques au pilote|Constante ODBC pour la plage de valeur spécifique au pilote de base|  
|--------------------|--------------------|---------------------------------|----------------------------------|---------------------------------------------------------|  
|Indicateurs de type de données SQL|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_SQL_TYPE_BASE|  
|Champs de descripteur|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DESCRIPTOR_BASE|  
|Champs de diagnostic|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DIAGNOSTIC_BASE|  
|Types d’informations|SQLUSMALLINT|0x4000|0x7FFF|SQL_DRIVER_INFO_TYPE_BASE|  
|Attributs de connexion|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_CONNECT_ATTR_BASE|  
|Attributs d’instruction|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_STATEMENT_ATTR_BASE|  
  
> [!NOTE]  
>  Types de données spécifique au pilote, champs de descripteur, champs de diagnostic, types d’informations, les attributs d’instruction et les attributs de connexion doivent être décrits dans la documentation du pilote. Lorsqu’une de ces valeurs est passé à une fonction ODBC, le pilote doit vérifier si la valeur est valide. Pilotes retournent SQLSTATE HYC00 (fonctionnalité facultative non implémentée) pour les valeurs spécifiques au pilote qui s’appliquent à d’autres pilotes.  
  
 Les valeurs de base sont définis pour faciliter le développement de pilotes. Par exemple, les attributs de diagnostic spécifique de pilote peuvent être définis dans le format suivant :  
  
```  
SQL_DRIVER_DIAGNOSTIC_BASE+0, SQL_DRIVER_DIAGNOSTIC_BASE +1  
```
