---
title: Limitations de chaîne | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 003cd318d6db54c7547375219805c63cfc4ce249
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63269859"
---
# <a name="string-limitations"></a>Limitations des chaînes
La longueur maximale d’une chaîne d’instruction SQL est de 65 000 caractères.  
  
 Lorsque le pilote Microsoft Access est utilisé, seules les constantes de chaîne SQL-92 (avec les guillemets simples, pas des guillemets doubles) sont pris en charge.  
  
 Le caractère barre verticale (&#124;) ne peut pas être utilisé dans une chaîne, si le caractère est entouré de guillemets back ou non.  
  
 Pour une interopérabilité maximale, les applications doivent passer des chaînes dans les paramètres, plutôt que passage des chaînes entre guillemets.
