---
title: Obtention de descripteur gère | Documents Microsoft
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
- descriptors [ODBC], retrieving or setting field values
ms.assetid: 936f983f-c7e9-43f3-97ea-dd4b1bbf4654
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eefe0ed5b32c2c6b3f815a239f52cc82a947735a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="obtaining-descriptor-handles"></a>Obtention de descripteur gère
Une application obtient le handle du descripteur de n’importe quel explicitement alloué comme un argument de sortie de l’appel à **SQLAllocHandle**. Le handle d’un descripteur implicitement alloué est obtenu en appelant **SQLGetStmtAttr**.
