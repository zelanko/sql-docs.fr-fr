---
title: Applications personnalisées (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305280"
---
# <a name="custom-applications"></a>Applications personnalisées
Les applications personnalisées effectuent généralement une tâche spécifique pour quelques DBMS. Par exemple, une application peut récupérer des données d’un seul DBMS et générer un rapport, ou transférer des données entre plusieurs DBMS. Ce que ces applications ont en commun, c’est que ces DBMS sont connus avant que la demande est écrite et sont peu susceptibles de changer au cours de la durée de l’application.  
  
 L’application personnalisée nécessite donc peu ou pas d’interopérabilité. Le développeur d’applications peut choisir un seul pilote pour chaque DBMS et coder directement à ces pilotes. L’application peut contenir en toute sécurité du code spécifique au conducteur pour exploiter les capacités de ces pilotes et pourrait même passer des appels à la base de données native API pour utiliser des fonctionnalités non prises en charge par ODBC.  
  
 La principale préoccupation d’interopérabilité de la plupart des applications personnalisées est de savoir si les DBMS cibles changeront à l’avenir. Si c’est le cas, ce processus peut être simplifié en écrivant du code plus interopérable pour commencer. Cependant, un tel changement de DBMS est rare et implique généralement une grande quantité de travail. Pour cette raison, les développeurs d’applications personnalisées choisissent rarement d’augmenter l’interopérabilité au détriment de la fonctionnalité; ils choisissent généralement de recoder cette fonctionnalité lorsqu’ils changent DBMS.
