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
ms.openlocfilehash: 90c92476337bb1059b7272830e33094edc58dbd9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68002072"
---
# <a name="cstring-class"></a>CString, classe
Étant donné que les objets de la classe **CString** dans Microsoft® Visual C++® sont signés et que les arguments de chaîne dans les fonctions ODBC ne sont pas signés, les applications qui passent des objets **CString** à des fonctions ODBC sans effectuer de casts reçoivent des avertissements du compilateur.
