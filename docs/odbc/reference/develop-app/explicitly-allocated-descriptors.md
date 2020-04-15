---
title: Descripteurs explicitement attribués (en anglais) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305690"
---
# <a name="explicitly-allocated-descriptors"></a>Descripteurs alloués explicitement
Une application peut affecter explicitement un descripteur d’application sur une connexion à tout moment où elle est connectée à la base de données. En spécifiant cette poignée descripteur comme attribut d’une poignée de déclaration à l’aide de **SQLSetStmtAttr**, l’application ordonne au conducteur d’utiliser ce descripteur à la place des descripteurs d’application implicitement attribués correspondants. L’application ne peut pas spécifier d’autres descripteurs de mise en œuvre.  
  
 Une demande peut associer un descripteur explicitement attribué à plus d’une déclaration. Ce n’est que lorsqu’une application est effectivement connectée à la base de données qu’un descripteur peut être un descripteur explicitement attribué. L’application peut libérer un tel descripteur explicitement, ou implicitement en libérant sa connexion.
