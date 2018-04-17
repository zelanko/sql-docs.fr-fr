---
title: Limitations de chaîne | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8a8e90ace4e237b7945da4a43ad869b79c657ab2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="string-limitations"></a>Limitations de la chaîne
La longueur maximale d’une chaîne d’instruction SQL est de 65 000 caractères.  
  
 Lorsque le pilote Microsoft Access est utilisé, seuls les constantes de chaîne SQL-92 (avec des guillemets simples, pas des guillemets doubles) sont pris en charge.  
  
 La barre verticale (&#124;) ne peut pas être utilisé dans une chaîne, si le caractère est entouré de guillemets précédent ou non.  
  
 Pour une interopérabilité maximale, les applications doivent passer des chaînes dans les paramètres, plutôt que passer des chaînes entre guillemets.
