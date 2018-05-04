---
title: Explicitement alloué descripteurs | Documents Microsoft
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
- descriptors [ODBC], allocating and freeing
- explicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: f590251d-56a6-4d58-a405-9e85e68fbc47
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1f09c3d7817fdb3d7f992255a7c2242c515e9748
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="explicitly-allocated-descriptors"></a>Descripteurs explicitement alloués
Une application peut allouer explicitement un descripteur de l’application sur une connexion à tout moment, qu'il est connecté à la base de données. En spécifiant ce handle de descripteur comme un attribut d’une instruction à l’aide de **SQLSetStmtAttr**, l’application dirige le pilote à utiliser ce descripteur à la place de correspondant implicitement alloué descripteurs de l’application. L’application ne peut pas spécifier de descripteurs d’implémentation d’un autre.  
  
 Une application peut associer un descripteur explicitement alloué à plusieurs instructions. Un descripteur peut être un descripteur explicitement alloué uniquement quand une application est réellement connectée à la base de données. L’application peut libérer un descripteur de ce type explicitement ou implicitement en libérant de sa connexion.
