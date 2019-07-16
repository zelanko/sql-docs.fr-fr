---
title: Obtention de descripteur gère | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: 936f983f-c7e9-43f3-97ea-dd4b1bbf4654
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8bfa0b36ecca3af655efde84c3ce3f22ab0c1f88
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086309"
---
# <a name="obtaining-descriptor-handles"></a>Obtention des handles de descripteur
Une application obtient le handle de descripteur alloué explicitement comme un argument de sortie de l’appel à **SQLAllocHandle**. Le handle d’un descripteur alloué implicitement est obtenu en appelant **SQLGetStmtAttr**.
