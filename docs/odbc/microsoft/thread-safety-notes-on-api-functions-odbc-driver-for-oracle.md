---
description: Remarques sur la cohérence des threads dans les fonctions de l’API (pilote ODBC pour Oracle)
title: Remarques sur la sécurité des threads sur les fonctions d’API (pilote ODBC pour Oracle) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c7da346832e2682caa02bdbdae91a1133a9cbaa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449081"
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Remarques sur la cohérence des threads dans les fonctions de l’API (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le pilote Microsoft ODBC pour Oracle est thread-safe ; Toutefois, Oracle n’autorise pas plusieurs instructions simultanées sur une seule connexion. Le pilote applique cette restriction. En d’autres termes, dans les applications multithread, bien que n’importe quel thread puisse appeler le pilote ODBC pour Oracle à tout moment, le pilote bloque tout autre thread du pilote sur la même connexion jusqu’à ce que le thread d’origine quitte le pilote.  
  
 Le pilote n’est pas bloqué s’il y a deux instructions sur deux connexions différentes. Toutefois, s’il existe une seule connexion avec deux instructions, il existe un risque de blocage.
