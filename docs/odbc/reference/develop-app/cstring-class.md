---
title: Classe CString | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CString class [ODBC]
ms.assetid: 18630642-76fa-43c4-a154-3f0969ec9b50
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 734bb703c5182e9825b9e60c6405d177b420c4d8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="cstring-class"></a>Classe CString
Étant donné que les objets de la **CString** classe dans Microsoft® Visual C++® sont signées et les arguments de chaîne dans les fonctions ODBC sont non signés, applications qui transmettent **CString** objets aux fonctions ODBC sans conversion les recevez des avertissements du compilateur.
