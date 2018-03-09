---
title: "Architectures d’accès de base de données standard | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9d41800-9068-4b76-895a-32b2853692dd
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 749492ebd893234dea574c0fd87e20b45ddd8628
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="standard-database-access-architectures"></a>Architectures d’accès de base de données standard
En analysant les composants d’accès de base de données décrites dans la section précédente, il s’avère que deux d'entre eux : protocoles de flux de données et des interfaces de programmation — sont de bons candidats pour la normalisation. Les deux composants, les protocoles réseau et le mécanisme IPC, non seulement se trouvent au plus un niveau trop faible, mais qu’ils sont fortement dépendants sur le réseau et le système d’exploitation. Il existe également une troisième approche, passerelles, qui offre des possibilités de normalisation.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Interface de programmation standard](../../odbc/reference/standard-programming-interface.md)  
  
-   [Protocole de flux de données standard](../../odbc/reference/standard-data-stream-protocol.md)  
  
-   [Passerelle standard](../../odbc/reference/standard-gateway.md)
