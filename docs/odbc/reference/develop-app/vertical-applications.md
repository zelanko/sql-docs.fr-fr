---
description: Applications verticales
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a12be9247af3f273526dd08ee99ff7cc301af822
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421403"
---
# <a name="vertical-applications"></a>Applications verticales
En général, les applications verticales exécutent une tâche bien définie sur un seul SGBD. Par exemple, une application d’entrée de commande effectue le suivi des commandes d’une société. Ce que ces types d’applications ont en commun, c’est que le schéma de la base de données est généralement conçu par le développeur de l’application et, tandis que l’application peut fonctionner avec plusieurs SGBD différents, il fonctionne avec un seul SGBD pour un seul client.  
  
 Étant donné que les applications verticales nécessitent généralement certaines fonctionnalités, telles que les curseurs ou les transactions à défilement, elles prennent rarement en charge tous les SGBD. Au lieu de cela, ils ont tendance à être très interopérables entre un ensemble limité de SGBD. En règle générale, les développeurs d’applications verticales choisissent de prendre en charge les SGBD qui représentent une grande partie du marché et d’ignorer le reste. Ils peuvent même choisir de prendre en charge des pilotes spécifiques pour ces SGBD afin de réduire leurs coûts de test et de support produit.  
  
 Étant donné que les applications verticales peuvent prendre en charge un ensemble connu de SGBD, ils contiennent parfois du code spécifique au pilote ou au SGBD. Toutefois, ce type de code est mieux adapté au minimum, car il nécessite du temps supplémentaire pour assurer la maintenance.
