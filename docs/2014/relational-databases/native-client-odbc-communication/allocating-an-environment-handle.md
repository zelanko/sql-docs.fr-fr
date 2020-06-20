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
ms.openlocfilehash: 1c655b5e9a406c3e1881c9dd199a92666377918f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021121"
---
# <a name="allocating-an-environment-handle"></a>Allocation d'un handle d'environnement
  Avant qu'une application puisse appeler toute fonction ODBC, elle doit initialiser l'environnement ODBC et allouer un handle d'environnement. Il s'agit du handle de contexte global et de l'espace réservé pour les autres handles dans ODBC. Pour ce faire, appelez **SQLAllocHandle** avec le paramètre *comme handletype* défini sur SQL_HANDLE_ENV et *InputHandle* défini sur SQL_NULL_HANDLE.  
  
 Après avoir alloué le handle d'environnement, l'application doit définir des attributs d'environnement afin d'indiquer la version des appels de fonction ODBC qu'elle utilisera. Pour utiliser ODBC 3. *x* , appelez [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) avec le paramètre d' *attribut* défini sur SQL_ATTR_ODBC_VERSION et *ValuePtr* défini sur SQL_OV_ODBC3.  
  
## <a name="see-also"></a>Voir aussi  
 [Communication avec SQL Server &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  
