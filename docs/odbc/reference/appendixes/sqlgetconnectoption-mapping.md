---
description: SQLGetConnectOption, mappage
title: Mappage Sqlgetconnectoption, | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLGetConnectOption
- SQLGetConnectOption function [ODBC], mapping
ms.assetid: e3792fe4-a955-473a-a297-c1b2403660c4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fbb8578b881e8eb04ef3b699fa7030e4670fab4d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421473"
---
# <a name="sqlgetconnectoption-mapping"></a>SQLGetConnectOption, mappage
Quand une application appelle **sqlgetconnectoption,** via un pilote ODBC *3. x* , l’appel à  
  
```  
SQLGetConnectOption(hdbc, fOption, pvParam)   
```  
  
 est mappé comme suit :  
  
-   Si *fOption* indique une option de connexion définie par ODBC qui retourne une chaîne, le gestionnaire de pilotes appelle  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Si *fOption* indique une option de connexion définie par ODBC qui retourne une valeur entière de 32 bits, le gestionnaire de pilotes appelle  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Si *fOption* indique une option d’instruction définie par le pilote, le gestionnaire de pilotes appelle  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 Dans les trois cas précédents, l’argument *ConnectionHandle* est défini sur la valeur de *hdbc*, l’argument d' *attribut* est défini sur la valeur de *fOption*et l’argument *ValuePtr* est défini sur la même valeur que *pvParam*.  
  
 Pour les options de connexion de chaîne définies par ODBC, le gestionnaire de pilotes définit l’argument *BufferLength* dans l’appel à **SQLGetConnectAttr** sur la longueur maximale prédéfinie (SQL_MAX_OPTION_STRING_LENGTH); pour une option de connexion sans chaîne, *BufferLength* a la valeur 0.  
  
 Pour un pilote ODBC *3. x* , le gestionnaire de pilotes ne vérifie plus si l' *option* est comprise entre SQL_CONN_OPT_MIN et SQL_CONN_OPT_MAX, ou est supérieure à SQL_CONNECT_OPT_DRVR_START. Le pilote doit vérifier la validité des valeurs d’option.
