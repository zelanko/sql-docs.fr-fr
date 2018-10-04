---
title: SQLSetConnectOption, mappage | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0351a6fa4621acb09d18a72b32ec2010a605ed9b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47769567"
---
# <a name="sqlsetconnectoption-mapping"></a>SQLSetConnectOption, mappage
Lorsqu’une application ODBC 2. *x* application appelle **SQLSetConnectOption** via un ODBC 3 *.x* pilote, l’appel à  
  
```  
SQLSetConnectOption(hdbc, fOption, vParam)  
```  
  
 entraîne comme suit :  
  
-   Si *fOption* indique un attribut de connexion définie par ODBC qui nécessite une chaîne, les appels du Gestionnaire de pilotes  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, SQL_NTS)  
    ```  
  
-   Si *fOption* indique un attribut de connexion définie par ODBC qui retourne une valeur d’entier 32 bits, les appels du Gestionnaire de pilotes  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0)  
    ```  
  
-   Si *fOption* indique un attribut de connexion définies par le pilote, les appels du Gestionnaire de pilotes  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength)  
    ```  
  
 Dans les trois cas précédents, le *ConnectionHandle* argument est défini à la valeur de *pas*, le *attribut* argument est défini à la valeur de *fOption* et le *ValuePtr* argument est défini sur la même valeur que *vParam*.  
  
 Étant donné que le Gestionnaire de pilotes ne sait pas si l’attribut de connexion définies par le pilote a besoin d’une chaîne ou une valeur entière 32 bits, il doit passer une valeur valide pour le *BufferLength* argument de **SQLSetConnectAttr**. Si le pilote a défini une sémantique spéciale pour définies par le pilote se connecter les attributs et doit être appelée à l’aide **SQLSetConnectOption**, il doit prendre en charge **SQLSetConnectOption**.  
  
 If un ODBC 2. *x* application appelle **SQLSetConnectOption** pour définir une option d’instruction spécifiques au pilote dans un ODBC 3 *.x* pilote et l’option a été défini dans un ODBC 2. *x* version du pilote, une nouvelle constante de manifeste doit être définie pour l’option dans ODBC 3 *.x* pilote. Si la constante de manifeste ancien est utilisée dans l’appel à **SQLSetConnectOption**, appelle le Gestionnaire de pilotes **SQLSetConnectAttr** avec la **StringLength** argument la valeur 0.  
  
 Pour un ODBC 3 *.x* pilote, le Gestionnaire de pilotes ne sont plus vérifie si *fOption* est comprise entre SQL_CONN_OPT_MIN et SQL_CONN_OPT_MAX, ou est supérieure à SQL_CONNECT_OPT_DRVR_START.  
  
## <a name="setting-statement-options-on-the-connection-level"></a>Définition des Options d’instruction sur le niveau de connexion  
 Dans ODBC 2. *x*, une application peut appeler **SQLSetConnectOption** pour définir une option d’instruction. Lorsque cette opération effectuée, le pilote établit l’option d’instruction comme une valeur par défaut pour toutes les instructions ultérieurement allouées pour cette connexion. Il est définies par le pilote si le pilote définit l’option d’instruction pour toutes les instructions existantes associé à la connexion spécifiée.  
  
 Cette possibilité a été déconseillée dans ODBC 3 *.x*. ODBC 3 *.x* pilotes doivent prennent uniquement en charge la définition d’ODBC 2. *x* les attributs d’instruction au niveau de connexion s’ils veulent pouvoir travailler avec ODBC 2. *x* applications que cela. ODBC 3 *.x* applications ne doivent jamais définir les attributs d’instruction au niveau de la connexion. ODBC 3 *.x* attributs d’instruction ne peut pas être définis au niveau de la connexion, à l’exception des attributs SQL_ATTR_METADATA_ID et SQL_ATTR_ASYNC_ENABLE, qui sont des attributs de connexion et les attributs d’instruction et peut être Définissez au niveau de la connexion ou niveau de l’instruction.
