---
title: Vérification de l’assistance et de la variabilité des fonctionnalités . Microsoft Docs
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
ms.openlocfilehash: 47f16160c05d1c410e3889f0bb857befe88df5b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299169"
---
# <a name="checking-feature-support-and-variability"></a>Vérification de la prise en charge et de la variabilité des fonctionnalités
Pour vérifier le support et la variabilité des fonctionnalités, les applications appellent généralement **SQLGetInfo**, **SQLGetFunctions**, et **SQLGetTypeInfo**. Un bon point de départ est l’API du conducteur et les niveaux de conformité de grammaire SQL. Ceux-ci décrivent de larges niveaux de support de fonctionnalité. L’application peut ensuite appeler **SQLGetInfo** avec d’autres options pour déterminer le support ou la variabilité des fonctionnalités dont elle a besoin, **SQLGetFunctions** pour déterminer si les fonctions dont elle a besoin au-delà du niveau de conformité retourné sont prises en charge, et **SQLGetTypeInfo** pour déterminer quels types de données SQL sont pris en charge.  
  
 Une application peut déterminer si un relevé ou un attribut de connexion est pris en charge en appelant **SQLSetStmtAttr** ou **SQLSetConnectAttr** avec cet attribut. Si la fonction renvoie SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, l’attribut est pris en charge; s’il retourne SQL_ERROR et SQLSTATE HYC00 (fonction facultative non implémentée), l’attribut n’est pas pris en charge.  
  
 Les demandes peuvent également déterminer une quantité limitée d’informations avant de se connecter au conducteur en appelant **SQLDrivers**.
