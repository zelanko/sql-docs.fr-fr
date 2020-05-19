---
title: Allocation d’un handle d’environnement | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 173211cfa6c1e70d979f908c88433857fccd0201
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705751"
---
# <a name="allocating-an-environment-handle"></a>Allocation d'un handle d'environnement
  Avant qu'une application puisse appeler toute fonction ODBC, elle doit initialiser l'environnement ODBC et allouer un handle d'environnement. Il s'agit du handle de contexte global et de l'espace réservé pour les autres handles dans ODBC. Pour ce faire, appelez **SQLAllocHandle** avec le paramètre *comme handletype* défini sur SQL_HANDLE_ENV et *InputHandle* défini sur SQL_NULL_HANDLE.  
  
 Après avoir alloué le handle d'environnement, l'application doit définir des attributs d'environnement afin d'indiquer la version des appels de fonction ODBC qu'elle utilisera. Pour utiliser ODBC 3. *x* , appelez [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) avec le paramètre d' *attribut* défini sur SQL_ATTR_ODBC_VERSION et *ValuePtr* défini sur SQL_OV_ODBC3.  
  
## <a name="see-also"></a>Voir aussi  
 [Communication avec SQL Server &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  
