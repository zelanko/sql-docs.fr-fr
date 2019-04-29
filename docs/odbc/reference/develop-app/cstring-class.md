---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f5752602de4848b35298fb4c4a6a1efdf6519dd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63042485"
---
# <a name="cstring-class"></a>CString, classe
Étant donné que les objets de la **CString** classe dans Microsoft® Visual C++® sont signées et les arguments de chaîne dans les fonctions ODBC sont non signés, les applications qui passent **CString** objets aux fonctions ODBC sans conversion les recevra les avertissements du compilateur.
