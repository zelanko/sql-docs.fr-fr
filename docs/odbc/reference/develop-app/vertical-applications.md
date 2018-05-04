---
title: Les Applications verticales | Documents Microsoft
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
- interoperability [ODBC], vertical applications
- vertical applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: d50ea3e6-7a9e-4fb6-8cd8-1d429d2f7b3c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c89d0080f4cc29296d9e6dcd43911ee920af6683
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="vertical-applications"></a>Applications verticales
Généralement, les applications verticales effectuent une tâche bien définie par rapport à un système SGBD unique. Par exemple, une application d’entrée de commande suit les commandes dans une société. Ce que ces types d’applications ont en commun est que le schéma de base de données est généralement conçu par le développeur d’applications et l’application pourrait fonctionner avec un nombre de SGBD différents, il fonctionne avec un SGBD unique pour un seul client.  
  
 Les applications verticales nécessitent généralement certaines fonctionnalités, telles que les curseurs de défilement ou les transactions, ils rarement prend en charge tous les SGBD. Au lieu de cela, ils ont tendance à être très interopérables entre un ensemble limité de SGBD. En règle générale, les développeurs d’applications verticales choisissent prendre en charge les SGBD qui représente une grande partie du marché et ignore le reste. Ils peuvent même choisir prendre en charge des pilotes spécifiques pour les SGBD pour réduire leurs tests et les coûts de support produit.  
  
 Étant donné que les applications verticales peuvent prendre en charge un jeu connu de SGBD, ils contiennent parfois des code spécifique au pilote ou propres au SGBD. Toutefois, ce code est préférable de conserver au minimum, car elle nécessite plus de temps pour mettre à jour.
