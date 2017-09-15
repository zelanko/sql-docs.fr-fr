---
title: "Obtention de descripteur gère | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: 936f983f-c7e9-43f3-97ea-dd4b1bbf4654
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: eb3d75a78a5eaa516921e561cb2d34786804d182
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="obtaining-descriptor-handles"></a>Obtention de descripteur gère
Une application obtient le handle du descripteur de n’importe quel explicitement alloué comme un argument de sortie de l’appel à **SQLAllocHandle**. Le handle d’un descripteur implicitement alloué est obtenu en appelant **SQLGetStmtAttr**.
