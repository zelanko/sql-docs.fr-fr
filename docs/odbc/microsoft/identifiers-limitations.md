---
title: Limitations des identificateurs | Documents Microsoft
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
ms.assetid: b3466382-71cb-4f82-8318-092a8fcef3df
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e7f8863dbe5f2c8c765caad093237957b25c46c7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="identifiers-limitations"></a>Limitations des identificateurs
Si un identificateur contient un espace ou un symbole spécial, l’identificateur doit figurer entre guillemets précédent. Un nom valide est une chaîne, pas plus de 64 caractères, dont le premier caractère ne doit pas être un espace. Les noms valides ne peuvent pas inclure les caractères de contrôle ou les caractères spéciaux suivants : ' &#124; # * ? [ ] . ! $ .  
  
 N’utilisez pas les mots réservés répertoriés dans la grammaire SQL dans l’annexe C de la *de référence du programmeur ODBC* (ou la forme abrégée de ces mots réservés) en tant qu’identificateurs (autrement dit, table ou colonne de noms), sauf si vous devez placer le mot à l’arrière apostrophes (').
