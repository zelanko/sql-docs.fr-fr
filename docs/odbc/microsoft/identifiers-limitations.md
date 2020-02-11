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
ms.openlocfilehash: 251ae0e4e94cec903e2c4b5cf687ed9b8b41dfc8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67952399"
---
# <a name="identifiers-limitations"></a>Limitations des identificateurs
Si un identificateur contient un espace ou un symbole spécial, l’identificateur doit être placé entre guillemets. Un nom valide est une chaîne de plus de 64 caractères, dont le premier caractère ne doit pas être un espace. Les noms valides ne peuvent pas contenir de caractères de contrôle ou les caractères spéciaux suivants : ' &#124; # * ? [ ] . ! $ .  
  
 N’utilisez pas les mots réservés listés dans la grammaire SQL de l’annexe C du *Guide de référence du programmeur ODBC* (ou la forme abrégée de ces mots réservés) en tant qu’identificateurs (autrement dit, les noms de table ou de colonne), à moins que vous n’entouriez le mot placé entre guillemets (').
