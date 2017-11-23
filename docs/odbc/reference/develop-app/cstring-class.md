---
title: Classe CString | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CString class [ODBC]
ms.assetid: 18630642-76fa-43c4-a154-3f0969ec9b50
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eb78f8d90a62eb25810596053e04f55442a96487
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="cstring-class"></a>Classe CString
Étant donné que les objets de la **CString** classe dans Microsoft® Visual C++® sont signées et les arguments de chaîne dans les fonctions ODBC sont non signés, applications qui transmettent **CString** objets aux fonctions ODBC sans conversion les recevez des avertissements du compilateur.
