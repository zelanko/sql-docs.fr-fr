---
title: Limitations d’identifications Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7154f2db09b69e6376b1fe3af1de3f2c646ee94e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286249"
---
# <a name="identifiers-limitations"></a>Limitations des identificateurs
Si un identifiant contient un espace ou un symbole spécial, l’identifiant doit être inclus dans des citations arrière. Un nom valide est une chaîne de pas plus de 64 caractères, dont le premier personnage ne doit pas être un espace. Les noms valides ne peuvent pas inclure les personnages de contrôle ou les caractères spéciaux suivants : ' &#124; ' ? [ ] . ! $ .  
  
 N’utilisez pas les mots réservés énumérés dans la grammaire SQL à l’Annexe C de la *Référence du programmeur ODBC* (ou la forme abrégée de ces mots réservés) comme identificateurs (c’est-à-dire, noms de table ou de colonne), à moins que vous n’entouriez le mot dans des citations en arrière (').
