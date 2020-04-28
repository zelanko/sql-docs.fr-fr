---
title: Applications personnalisées | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], custom applications
- custom applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: f28178d9-ecd6-4e8c-9644-9bb624999dcb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df00a748ee4d5e3a63b32c95449417a1057b58e1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305280"
---
# <a name="custom-applications"></a>Applications personnalisées
Les applications personnalisées effectuent généralement une tâche spécifique pour quelques SGBD. Par exemple, une application peut récupérer des données à partir d’un seul SGBD et générer un rapport, ou elle peut transférer des données entre plusieurs SGBD. Ce que ces applications ont en commun, c’est que ces SGBD sont connus avant l’écriture de l’application et sont peu susceptibles de changer pendant la durée de vie de l’application.  
  
 L’application personnalisée nécessite donc peu ou pas d’interopérabilité. Le développeur de l’application peut choisir un seul pilote pour chaque SGBD et coder directement ces pilotes. L’application peut contenir en toute sécurité du code propre au pilote afin d’exploiter les fonctionnalités de ces pilotes et peut même effectuer des appels à l’API de base de données native pour utiliser des fonctionnalités non prises en charge par ODBC.  
  
 Le principal problème d’interopérabilité de la plupart des applications personnalisées est que les SGBD cibles seront modifiés à l’avenir. Dans ce cas, vous pouvez simplifier ce processus en écrivant davantage de code interopérable pour commencer. Toutefois, ce changement de SGBD est rare et implique généralement une grande quantité de travail. Pour cette raison, les développeurs d’applications personnalisées choisissent rarement d’accroître l’interopérabilité au détriment des fonctionnalités. ils choisissent généralement de coder cette fonctionnalité lorsqu’ils changent de SGBD.
