---
title: Architectures d’accès standard à la base de données (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a9d41800-9068-4b76-895a-32b2853692dd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6e78202eff69e6b30dc1e97d80f464dad75bb201
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280032"
---
# <a name="standard-database-access-architectures"></a>Architectures de l’accès aux bases de données standard
En examinant les composants d’accès à la base de données décrits dans la section précédente, il s’avère que deux d’entre eux - les interfaces de programmation et les protocoles de flux de données - sont de bons candidats à la normalisation. Les deux autres composantes - le mécanisme IPC et les protocoles de réseau - résident non seulement à un niveau trop bas, mais ils sont tous deux très dépendants du réseau et du système d’exploitation. Il existe également une troisième approche - les passerelles - qui offre des possibilités de normalisation.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Interface de programmation standard](../../odbc/reference/standard-programming-interface.md)  
  
-   [Protocole de flux de données standard](../../odbc/reference/standard-data-stream-protocol.md)  
  
-   [Passerelle standard](../../odbc/reference/standard-gateway.md)
