---
title: Applications verticales | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: df7a2d036692cefcd1b2ea2338d51938a11ea85a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610477"
---
# <a name="vertical-applications"></a>Applications verticales
Applications verticales effectuent généralement une tâche bien définie par rapport à un système SGBD unique. Par exemple, une application de saisie de commandes suit les commandes dans une société. Ce que ces types d’applications ont en commun est que le schéma de base de données est généralement conçu par le développeur d’applications et l’application pourrait fonctionner avec un nombre de SGBD différents, il fonctionne avec un système SGBD unique pour un seul client.  
  
 Étant donné que les applications verticales nécessitent généralement certaines fonctionnalités, telles que les transactions, ou les curseurs avec défilement rarement prennent en charge tous les SGBD. Au lieu de cela, ils ont tendance à être hautement interopérable parmi un ensemble limité de SGBD. En règle générale, les développeurs d’applications verticales choisissent prendre en charge ces SGBD qui représente une grande partie du marché et ignore le reste. Il peuvent même choisir de prendre en charge des pilotes spécifiques pour les SGBD pour réduire leurs tests et les coûts de support produit.  
  
 Étant donné que les applications verticales peuvent prendre en charge un ensemble connu de SGBD, ils contiennent parfois des code spécifiques au pilote ou propres au SGBD. Toutefois, ce code est préférable de conserver au minimum, car elle nécessite plus de temps pour mettre à jour.
