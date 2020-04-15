---
title: Cartographie SQLGetConnectOption (fr) Microsoft Docs
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
ms.openlocfilehash: 8d2905bd6793d032e485183c8f553cef2cdefda3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302000"
---
# <a name="sqlgetconnectoption-mapping"></a>SQLGetConnectOption, mappage
Lorsqu’une application appelle **SQLGetConnectOption** par l’intermédiaire d’un pilote ODBC *3.x,* l’appel à  
  
```  
SQLGetConnectOption(hdbc, fOption, pvParam)   
```  
  
 est cartographié comme suit:  
  
-   Si *fOption* indique une option de connexion définie par ODBC qui renvoie une chaîne, le Gestionnaire de conducteur appelle  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Si *fOption* indique une option de connexion définie par ODBC qui retourne une valeur d’intégration 32 bits, le Gestionnaire de conducteur appelle  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Si *fOption* indique une option d’instruction définie par le conducteur, le gestionnaire de conducteur appelle  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 Dans les trois cas précédents, l’argument *De ConnectionHandle* est réglé à la valeur dans *hdbc*, *l’argument d’attribut* est réglé à la valeur dans *fOption*, et l’argument *ValuePtr* est réglé à la même valeur que *pvParam*.  
  
 Pour les options de connexion à cordes définies par ODBC, le gestionnaire de conducteur définit *l’argument de bufferLength* dans l’appel à **SQLGetConnectAttr** à la longueur maximale prédéfinie (SQL_MAX_OPTION_STRING_LENGTH); pour une option de connexion noncordante, *BufferLength* est réglé à 0.  
  
 Pour un conducteur ODBC *3.x,* le gestionnaire de conducteur ne vérifie plus si *Option* est entre SQL_CONN_OPT_MIN et SQL_CONN_OPT_MAX, ou est plus grande que SQL_CONNECT_OPT_DRVR_START. Le conducteur doit vérifier la validité des valeurs d’option.
