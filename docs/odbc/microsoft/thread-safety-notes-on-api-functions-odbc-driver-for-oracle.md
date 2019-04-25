---
title: Notes de sécurité des threads sur les fonctions d’API (pilote ODBC pour Oracle) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], threading
- threading options [ODBC]
- multiple concurrent statements [ODBC]
ms.assetid: f0c9bdfd-f79d-4088-9ecb-afcd8ca7fb73
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d1faa7dfd8873b8c11cda5cb3e67d5408c35474
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62633214"
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Remarques sur la cohérence des threads dans les fonctions de l’API (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Le pilote Microsoft ODBC pour Oracle est thread-safe ; Toutefois, Oracle n’autorise pas plusieurs instructions simultanées sur une seule connexion. Le pilote applique cette restriction. En d’autres termes, dans les applications multithread, bien que le pilote ODBC pour Oracle n’importe quel thread peut appeler à tout moment, le pilote bloque n’importe quel autre thread à partir du pilote sur la même connexion jusqu'à ce que le thread d’origine quitte le pilote.  
  
 Le pilote ne bloque pas s’il existe deux instructions sur les deux connexions différentes. Toutefois, s’il existe une connexion unique avec deux instructions, il est potentiel de blocage.
