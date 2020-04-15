---
title: Subkey de pilote par défaut (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- default subkey [ODBC]
- registry entries for components [ODBC], default subkey
- subkeys [ODBC], default subkey
- drivers subkey [ODBC]
ms.assetid: 9e58b24f-ebfc-4286-a272-0843b4d6f2d5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bb134d670964e352d94c13474d8a72fa4bd494ba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301052"
---
# <a name="default-driver-subkey"></a>Sous-clé du pilote par défaut
Le sous-clé par défaut contient une valeur unique qui décrit le pilote utilisé par la source de données par défaut. Le format de cette valeur est affiché dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|**Pilote**|REG_SZ|*par défaut-pilote-description*|  
  
 Le nom de description par défaut du conducteur est le même que le nom de la valeur sous la *sous-clé* ODBC Drivers qui décrit le conducteur.  
  
 Par exemple, si la source de données par défaut utilise le pilote SQL Server, la valeur sous le sous-clé par défaut peut être :  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  Le pilote par défaut contenu dans le sous-clé par défaut peut se référer à un utilisateur par défaut DSN ou à un système par défaut DSN. Si un utilisateur par défaut DSN et un système par défaut DSN ont été créés, le pilote par défaut est déterminé par le DSN qui a été créé en dernier, de sorte qu’il pourrait ne pas être une entrée valide pour le DSN qui a été créé en premier.
