---
description: Vérification de la prise en charge et de la variabilité des fonctionnalités
title: Vérification de la prise en charge et de la variabilité des fonctionnalités | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: ff45f220-9b8b-4c44-82f8-a8e9913fffea
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 60fb6b39d7b2326a925aea40303ce52165cca8a9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465911"
---
# <a name="checking-feature-support-and-variability"></a>Vérification de la prise en charge et de la variabilité des fonctionnalités
Pour vérifier la prise en charge et la variabilité des fonctionnalités, les applications appellent généralement **SQLGetInfo**, **SQLGetFunctions**et **SQLGetTypeInfo**. Un bon point de départ est l’API du pilote et les niveaux de conformité de la grammaire SQL. Ils décrivent de larges niveaux de prise en charge des fonctionnalités. L’application peut ensuite appeler **SQLGetInfo** avec d’autres options pour déterminer la prise en charge ou la variabilité des fonctionnalités dont elle a besoin, **SQLGetFunctions** pour déterminer si les fonctions dont elle a besoin au-delà du niveau de conformité retourné sont prises en charge, et **SQLGetTypeInfo** pour déterminer quels types de données SQL sont pris en charge.  
  
 Une application peut déterminer si une instruction ou un attribut de connexion est pris en charge en appelant **SQLSetStmtAttr** ou **SQLSetConnectAttr** avec cet attribut. Si la fonction retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, l’attribut est pris en charge ; Si elle retourne SQL_ERROR et SQLSTATE HYC00 (fonctionnalité facultative non implémentée), l’attribut n’est pas pris en charge.  
  
 Les applications peuvent également déterminer une quantité limitée d’informations avant de se connecter au pilote en appelant **SQLDrivers**.
