---
title: Notes de sécurité des threads sur les fonctions d’API (le pilote ODBC pour Oracle) | Documents Microsoft
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
- ODBC driver for Oracle [ODBC], threading
- threading options [ODBC]
- multiple concurrent statements [ODBC]
ms.assetid: f0c9bdfd-f79d-4088-9ecb-afcd8ca7fb73
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a99ddfed60ebb9d7d8dcfd4215b7c0a8d57314fb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Notes de sécurité des threads sur les fonctions d’API (le pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Le pilote Microsoft ODBC pour Oracle est thread-safe ; Cependant, Oracle n’autorise pas plusieurs instructions simultanées sur une seule connexion. Le pilote applique cette restriction. En d’autres termes, dans les applications multithread, bien que le pilote ODBC pour Oracle n’importe quel thread peut appeler à tout moment, le pilote bloque tout autre thread du pilote sur la même connexion jusqu'à ce que le thread d’origine quitte le pilote.  
  
 Le pilote ne bloque pas s’il existe deux instructions sur les deux connexions différentes. Toutefois, s’il existe une seule connexion avec les deux instructions, il est potentiel de blocage.
