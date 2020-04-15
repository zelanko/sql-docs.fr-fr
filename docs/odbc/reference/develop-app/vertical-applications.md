---
title: Applications verticales Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], vertical applications
- vertical applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: d50ea3e6-7a9e-4fb6-8cd8-1d429d2f7b3c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cc88f38fd1ffe8b2ee0033ad0a2abc4f15fd5cf3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300374"
---
# <a name="vertical-applications"></a>Applications verticales
Les applications verticales effectuent généralement une tâche bien définie contre un seul DBMS. Par exemple, une demande d’entrée de commande suit les commandes d’une entreprise. Ce que ces types d’applications ont en commun, c’est que le schéma de base de données est généralement conçu par le développeur d’applications et, tandis que l’application peut fonctionner avec un certain nombre de DBMS différents, il fonctionne avec un seul DBMS pour un seul client.  
  
 Étant donné que les applications verticales nécessitent généralement certaines fonctionnalités, telles que les curseurs défilementables ou les transactions, elles prennent rarement en charge tous les DBMS. Au lieu de cela, ils ont tendance à être très interopérables parmi un ensemble limité de DBMS. Typiquement, les développeurs d’applications verticales choisissent de prendre en charge les DBMS qui représentent une grande fraction du marché et d’ignorer le reste. Ils pourraient même choisir d’appuyer des facteurs spécifiques pour ces DBMS afin de réduire leurs coûts d’essai et de soutien des produits.  
  
 Étant donné que les applications verticales peuvent prendre en charge un ensemble connu de DBMS, elles contiennent parfois un code spécifique au conducteur ou DBMS. Cependant, ce code est mieux conservé à un minimum parce qu’il nécessite plus de temps pour maintenir.
