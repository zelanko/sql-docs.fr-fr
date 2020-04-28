---
title: Descripteurs alloués explicitement | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a9950bc23a1e75606316039e6c2d66f3dba59940
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305690"
---
# <a name="explicitly-allocated-descriptors"></a>Descripteurs alloués explicitement
Une application peut allouer explicitement un descripteur d’application sur une connexion à tout moment qu’elle est connectée à la base de données. En spécifiant ce handle de descripteur comme attribut d’un descripteur d’instruction à l’aide de **SQLSetStmtAttr**, l’application indique au pilote d’utiliser ce descripteur à la place des descripteurs d’application alloués implicitement correspondants. L’application ne peut pas spécifier d’autres descripteurs d’implémentation.  
  
 Une application peut associer un descripteur explicitement alloué à plusieurs instructions. Uniquement lorsqu’une application est réellement connectée à la base de données, un descripteur peut être un descripteur explicitement alloué. L’application peut libérer explicitement ce descripteur, ou implicitement en libérant sa connexion.
