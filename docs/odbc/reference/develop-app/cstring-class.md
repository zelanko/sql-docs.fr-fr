---
description: CString, classe
title: CString, classe | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CString class [ODBC]
ms.assetid: 18630642-76fa-43c4-a154-3f0969ec9b50
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cfe8809fed17e4e787c9965f175c4b97238868bf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499932"
---
# <a name="cstring-class"></a>CString, classe
Étant donné que les objets de la classe **CString** dans Microsoft® Visual C++® sont signés et que les arguments de chaîne dans les fonctions ODBC ne sont pas signés, les applications qui passent des objets **CString** à des fonctions ODBC sans effectuer de casts reçoivent des avertissements du compilateur.
