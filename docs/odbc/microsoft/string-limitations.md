---
title: Limitations de cordes (en anglais) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61f81ff3da882095a0a6c41bb5061addd497a5d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306060"
---
# <a name="string-limitations"></a>Limitations des chaînes
La longueur maximale d’une chaîne de déclaration SQL est de 65 000 caractères.  
  
 Lorsque le pilote Microsoft Access est utilisé, seules les constantes de cordes SQL-92 (avec des guillemets uniques, et non des doubles guillemets) sont prises en charge.  
  
 Le caractère de pipe (&#124;) ne peut pas être utilisé dans une chaîne, que le personnage soit enfermé dans des citations de dos ou non.  
  
 Pour une interopérabilité maximale, les applications doivent passer des chaînes dans les paramètres, plutôt que de passer des chaînes citées.
