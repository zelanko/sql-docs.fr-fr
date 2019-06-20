---
title: Explicitement alloué descripteurs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- explicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: f590251d-56a6-4d58-a405-9e85e68fbc47
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fbec69e0d984d843abc2b8754e111a1199c79a5a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63049788"
---
# <a name="explicitly-allocated-descriptors"></a>Descripteurs alloués explicitement
Une application peut allouer explicitement un descripteur d’application sur une connexion à tout moment, qu'il est connecté à la base de données. En spécifiant ce handle de descripteur comme un attribut d’une instruction gérer à l’aide de **SQLSetStmtAttr**, l’application dirige le pilote à utiliser ce descripteur à la place le correspondantes alloués implicitement application descripteurs. L’application ne peut pas spécifier de descripteurs d’implémentation alternative.  
  
 Une application peut associer un descripteur alloué explicitement à plusieurs instructions. Un descripteur peut être un descripteur alloué explicitement uniquement quand une application est réellement connectée à la base de données. L’application peut libérer un descripteur de ce type explicitement ou implicitement, en libérant de sa connexion.
