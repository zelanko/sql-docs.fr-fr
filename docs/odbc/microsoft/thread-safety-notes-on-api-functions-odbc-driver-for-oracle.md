---
title: "Notes de sécurité des threads sur les fonctions d’API (le pilote ODBC pour Oracle) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], threading
- threading options [ODBC]
- multiple concurrent statements [ODBC]
ms.assetid: f0c9bdfd-f79d-4088-9ecb-afcd8ca7fb73
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6037a11f71d5fc6af4d9f173974fc91c80833fc0
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Notes de sécurité des threads sur les fonctions d’API (le pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Le pilote Microsoft ODBC pour Oracle est thread-safe ; Cependant, Oracle n’autorise pas plusieurs instructions simultanées sur une seule connexion. Le pilote applique cette restriction. En d’autres termes, dans les applications multithread, bien que le pilote ODBC pour Oracle n’importe quel thread peut appeler à tout moment, le pilote bloque tout autre thread du pilote sur la même connexion jusqu'à ce que le thread d’origine quitte le pilote.  
  
 Le pilote ne bloque pas s’il existe deux instructions sur les deux connexions différentes. Toutefois, s’il existe une seule connexion avec les deux instructions, il est potentiel de blocage.
