---
description: Descripteurs alloués explicitement
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
ms.openlocfilehash: 7215d17a7156419f08bbd73528c468d7b6355b94
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461481"
---
# <a name="explicitly-allocated-descriptors"></a>Descripteurs alloués explicitement
Une application peut allouer explicitement un descripteur d’application sur une connexion à tout moment qu’elle est connectée à la base de données. En spécifiant ce handle de descripteur comme attribut d’un descripteur d’instruction à l’aide de **SQLSetStmtAttr**, l’application indique au pilote d’utiliser ce descripteur à la place des descripteurs d’application alloués implicitement correspondants. L’application ne peut pas spécifier d’autres descripteurs d’implémentation.  
  
 Une application peut associer un descripteur explicitement alloué à plusieurs instructions. Uniquement lorsqu’une application est réellement connectée à la base de données, un descripteur peut être un descripteur explicitement alloué. L’application peut libérer explicitement ce descripteur, ou implicitement en libérant sa connexion.
