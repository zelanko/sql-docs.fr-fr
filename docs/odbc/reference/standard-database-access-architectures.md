---
title: "Architectures d’accès de base de données standard | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9d41800-9068-4b76-895a-32b2853692dd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ff9ebb61d8a0446f4c6015dd5c0ae56c22ebfc45
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="standard-database-access-architectures"></a>Architectures d’accès de base de données standard
En analysant les composants d’accès de base de données décrites dans la section précédente, il s’avère que deux d'entre eux : protocoles de flux de données et des interfaces de programmation — sont de bons candidats pour la normalisation. Les deux composants, les protocoles réseau et le mécanisme IPC, non seulement se trouvent au plus un niveau trop faible, mais qu’ils sont fortement dépendants sur le réseau et le système d’exploitation. Il existe également une troisième approche, passerelles, qui offre des possibilités de normalisation.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Interface de programmation standard](../../odbc/reference/standard-programming-interface.md)  
  
-   [Protocole de flux de données standard](../../odbc/reference/standard-data-stream-protocol.md)  
  
-   [Passerelle standard](../../odbc/reference/standard-gateway.md)
