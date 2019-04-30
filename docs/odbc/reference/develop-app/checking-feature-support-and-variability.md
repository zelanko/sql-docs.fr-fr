---
title: Vérification de la prise en charge de fonctionnalité et de variabilité | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b9af2cfd73556baca4870428cdcdfcee3e07191d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63217610"
---
# <a name="checking-feature-support-and-variability"></a>Vérification de la prise en charge et de la variabilité des fonctionnalités
Pour vérifier la prise en charge de la fonctionnalité et de variabilité, les applications appellent généralement **SQLGetInfo**, **SQLGetFunctions**, et **SQLGetTypeInfo**. Un bon point de départ est de niveaux de conformité grammaire SQL et les API du pilote. Il s’agit des grands niveaux de prise en charge de la fonctionnalité. L’application peut ensuite appeler **SQLGetInfo** avec d’autres options pour déterminer la prise en charge ou la variabilité des fonctionnalités dont il a besoin, **SQLGetFunctions** pour déterminer si le fonctions besoins au-delà retourné niveau de conformité sont pris en charge, et **SQLGetTypeInfo** pour déterminer quels types de données SQL sont prises en charge.  
  
 Une application peut déterminer si un attribut d’instruction ou de la connexion est prise en charge en appelant **SQLSetStmtAttr** ou **SQLSetConnectAttr** avec cet attribut. Si la fonction retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, l’attribut est pris en charge ; Si elle retourne SQL_ERROR et SQLSTATE HYC00 (fonctionnalité facultative non implémentée), l’attribut n’est pas pris en charge.  
  
 Les applications peuvent déterminer également une quantité limitée d’informations avant de vous connecter au pilote en appelant **SQLDrivers**.
