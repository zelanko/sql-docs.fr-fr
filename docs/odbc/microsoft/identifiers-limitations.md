---
title: Limitations des identificateurs | Microsoft Docs
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
ms.assetid: b3466382-71cb-4f82-8318-092a8fcef3df
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c781113124d456e1ba866546d6ada7a17371d71f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63208527"
---
# <a name="identifiers-limitations"></a>Limitations des identificateurs
Si un identificateur contient un espace ou symbole spécial, l’identificateur doit être encadrée de guillemets précédent. Un nom valide est une chaîne, pas plus de 64 caractères, dont le premier caractère ne doit pas être un espace. Noms valides ne peuvent pas contenir les caractères de contrôle ou les caractères spéciaux suivants : « &#124; # * ? [ ] . ! $ .  
  
 N’utilisez pas les mots réservés répertoriés dans la grammaire SQL dans l’annexe C de la *de référence du programmeur ODBC* (ou la forme abrégée de ces mots réservés) en tant qu’identificateurs (autrement dit, table ou colonne de noms), sauf si vous devez placer le mot à l’arrière guillemets (').
