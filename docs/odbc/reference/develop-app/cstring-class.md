---
title: Classe CString | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CString class [ODBC]
ms.assetid: 18630642-76fa-43c4-a154-3f0969ec9b50
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5e3d3f3719fbc16a72f692b809eb646e7bbcf24d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cstring-class"></a>Classe CString
Étant donné que les objets de la **CString** classe dans Microsoft® Visual C++® sont signées et les arguments de chaîne dans les fonctions ODBC sont non signés, applications qui transmettent **CString** objets aux fonctions ODBC sans conversion les recevez des avertissements du compilateur.
