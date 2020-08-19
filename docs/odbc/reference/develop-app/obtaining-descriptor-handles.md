---
description: Obtention des handles de descripteur
title: Obtention des handles de descripteur | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c46ce0bff7240c121c6c56a5c3cd1b19769afb04
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429201"
---
# <a name="obtaining-descriptor-handles"></a>Obtention des handles de descripteur
Une application obtient le descripteur d’un descripteur explicitement alloué comme argument de sortie de l’appel à **SQLAllocHandle**. Le handle d’un descripteur alloué implicitement est obtenu en appelant **SQLGetStmtAttr**.
