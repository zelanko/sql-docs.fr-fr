---
title: Cartographie SQLSetConnectOption (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLSetConnectOption
ms.assetid: a1b325cf-0c42-41c1-b141-b5a4fee7e708
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 757b50c7e18133e02b4cf6addaa327b2053f5439
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287469"
---
# <a name="sqlsetconnectoption-mapping"></a>SQLSetConnectOption, mappage
Quand un ODBC 2. *x* application appelle **SQLSetConnectOption** par l’intermédiaire d’un pilote ODBC 3 *.x,* l’appel à  
  
```  
SQLSetConnectOption(hdbc, fOption, vParam)  
```  
  
 résultatra comme suit :  
  
-   Si *fOption* indique un attribut de connexion défini par ODBC qui nécessite une chaîne, le Gestionnaire de conducteur appelle  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, SQL_NTS)  
    ```  
  
-   Si *fOption* indique un attribut de connexion défini par ODBC qui renvoie une valeur d’intégration 32 bits, le Gestionnaire de conducteur appelle  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0)  
    ```  
  
-   Si *fOption* indique un attribut de connexion défini par le conducteur, le gestionnaire de conducteur appelle  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength)  
    ```  
  
 Dans les trois cas précédents, l’argument *De ConnectionHandle* est réglé à la valeur dans *hdbc*, *l’argument d’attribut* est réglé à la valeur dans *fOption*, et l’argument *ValuePtr* est réglé à la même valeur que *vParam*.  
  
 Étant donné que le gestionnaire de conducteur ne sait pas si l’attribut de connexion défini par le conducteur a besoin d’une valeur d’intégrateur de chaîne ou de 32 bits, il doit passer en valeur valide pour l’argument *BufferLength* de **SQLSetConnectAttr**. Si le conducteur a défini la sémantique spéciale pour les attributs de connexion définis par le conducteur et doit être appelé à l’aide **de SQLSetConnectOption**, il doit prendre en charge **SQLSetConnectOption**.  
  
 Si un ODBC 2. *x* application appelle **SQLSetConnectOption** pour définir une option de relevé spécifique au conducteur dans un pilote ODBC 3 *.x,* et l’option a été définie dans un ODBC 2. *version x* du pilote, une nouvelle constante manifeste doit être définie pour l’option dans le pilote ODBC 3 *.x.* Si l’ancienne constante manifeste est utilisée dans l’appel à **SQLSetConnectOption**, le gestionnaire de conducteur appellera **SQLSetConnectAttr** avec **l’argument StringLength** réglé 0.  
  
 Pour un conducteur ODBC 3 *.x,* le driver Manager ne vérifie plus si *fOption* se trouve entre SQL_CONN_OPT_MIN et SQL_CONN_OPT_MAX, ou est plus grand que SQL_CONNECT_OPT_DRVR_START.  
  
## <a name="setting-statement-options-on-the-connection-level"></a>Définir les options d’énoncés au niveau de connexion  
 À ODBC 2. *x*, une application pourrait appeler **SQLSetConnectOption** pour définir une option de déclaration. Lorsque cela est fait, le conducteur établit l’option d’instruction comme un défaut pour toutes les déclarations plus tard allouées pour cette connexion. Il est défini par le conducteur si le conducteur définit l’option d’instruction pour les relevés existants associés à la connexion spécifiée.  
  
 Cette capacité a été dépréciée dans ODBC 3 *.x*. Les conducteurs ODBC 3 *.x* n’ont besoin que d’un réglage de support ODBC 2. *x* attributs de déclaration au niveau de connexion s’ils veulent travailler avec ODBC 2. *x* applications qui le font. Les applications ODBC 3 *.x* ne doivent jamais définir les attributs de l’instruction au niveau de connexion. Les attributs de relevés de 3 *.x* D’ODBC ne peuvent pas être définis au niveau de connexion, à l’exception des attributs SQL_ATTR_METADATA_ID et SQL_ATTR_ASYNC_ENABLE, qui sont à la fois des attributs de connexion et des attributs de déclaration, et peuvent être définis au niveau de connexion ou au niveau de l’instruction.
