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
ms.openlocfilehash: 5808265a9ab70b9947cea64fef790497c7229da8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68069929"
---
# <a name="explicitly-allocated-descriptors"></a>Descripteurs alloués explicitement
Une application peut allouer explicitement un descripteur d’application sur une connexion à tout moment, qu'il est connecté à la base de données. En spécifiant ce handle de descripteur comme un attribut d’une instruction gérer à l’aide de **SQLSetStmtAttr**, l’application dirige le pilote à utiliser ce descripteur à la place le correspondantes alloués implicitement application descripteurs. L’application ne peut pas spécifier de descripteurs d’implémentation alternative.  
  
 Une application peut associer un descripteur alloué explicitement à plusieurs instructions. Un descripteur peut être un descripteur alloué explicitement uniquement quand une application est réellement connectée à la base de données. L’application peut libérer un descripteur de ce type explicitement ou implicitement, en libérant de sa connexion.
