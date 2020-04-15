---
title: Applications génériques (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], generic applications
- interoperability [ODBC], levels
- generic applications [ODBC]
ms.assetid: dda2a3c4-76ef-40a6-b3a1-9e95bed61618
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 607676d5370f02ee1d39196bff9261bc897521ee
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305550"
---
# <a name="generic-applications"></a>Applications génériques
Les applications génériques effectuent parfois une tâche codée en dur, comme une feuille de calcul récupérant des données à partir d’une base de données. Ils peuvent également effectuer une variété de tâches définies par l’utilisateur, comme une application de requête générique permettant à l’utilisateur d’entrer et d’exécuter une déclaration SQL. Ce que les applications génériques ont en commun, c’est qu’ils doivent travailler avec une variété de différents DBMS et que le développeur ne sait pas à l’avance ce que ces DBMS seront.  
  
 Par conséquent, les applications génériques doivent être hautement interopérables. Le développeur doit faire de nombreux choix, en échangeant l’interopérabilité pour les fonctionnalités, et doit écrire du code qui s’attend à ce que les pilotes prennent en charge un large éventail de fonctionnalités. Bien que les applications génériques puissent être réglées pour fonctionner avec des DBMS populaires, elles contiennent rarement du code spécifique au conducteur ou DBMS.
