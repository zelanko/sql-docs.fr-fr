---
title: Architectures d’accès de base de données standard | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a9d41800-9068-4b76-895a-32b2853692dd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ff5ee3c22a01b0b1963f1ca6021e72502aa377b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47724117"
---
# <a name="standard-database-access-architectures"></a>Architectures de l’accès aux bases de données standard
En analysant les composants d’accès de base de données décrites dans la section précédente, il s’avère que deux d'entre elles : protocoles de flux de données et des interfaces de programmation — sont de bons candidats pour la normalisation. Les deux autres composants, les protocoles réseau et le mécanisme IPC — non seulement résident sur un niveau trop bas, mais qu’ils sont fortement dépendants sur le réseau et le système d’exploitation. Il existe également une troisième approche, passerelles, qui offre des possibilités de normalisation.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Interface de programmation standard](../../odbc/reference/standard-programming-interface.md)  
  
-   [Protocole de flux de données standard](../../odbc/reference/standard-data-stream-protocol.md)  
  
-   [Passerelle standard](../../odbc/reference/standard-gateway.md)
