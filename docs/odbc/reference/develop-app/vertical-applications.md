---
title: Les Applications verticales | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [ODBC], vertical applications
- vertical applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: d50ea3e6-7a9e-4fb6-8cd8-1d429d2f7b3c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a3f4f8eca8309cb40b6ef9d2a7f9baac77c05f84
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="vertical-applications"></a>Applications verticales
Généralement, les applications verticales effectuent une tâche bien définie par rapport à un système SGBD unique. Par exemple, une application d’entrée de commande suit les commandes dans une société. Ce que ces types d’applications ont en commun est que le schéma de base de données est généralement conçu par le développeur d’applications et l’application pourrait fonctionner avec un nombre de SGBD différents, il fonctionne avec un SGBD unique pour un seul client.  
  
 Les applications verticales nécessitent généralement certaines fonctionnalités, telles que les curseurs de défilement ou les transactions, ils rarement prend en charge tous les SGBD. Au lieu de cela, ils ont tendance à être très interopérables entre un ensemble limité de SGBD. En règle générale, les développeurs d’applications verticales choisissent prendre en charge les SGBD qui représente une grande partie du marché et ignore le reste. Ils peuvent même choisir prendre en charge des pilotes spécifiques pour les SGBD pour réduire leurs tests et les coûts de support produit.  
  
 Étant donné que les applications verticales peuvent prendre en charge un jeu connu de SGBD, ils contiennent parfois des code spécifique au pilote ou propres au SGBD. Toutefois, ce code est préférable de conserver au minimum, car elle nécessite plus de temps pour mettre à jour.

