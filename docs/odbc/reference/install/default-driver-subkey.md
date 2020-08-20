---
description: Sous-clé du pilote par défaut
title: Sous-clé du pilote par défaut | Microsoft Docs
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
ms.openlocfilehash: d78cc54253d002c54510fdc47f46f10de9281b65
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494552"
---
# <a name="default-driver-subkey"></a>Sous-clé du pilote par défaut
La sous-clé par défaut contient une valeur unique qui décrit le pilote utilisé par la source de données par défaut. Le format de cette valeur est indiqué dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|**Driver**|REG_SZ|*Description du pilote par défaut*|  
  
 Le nom de la *Description par défaut du pilote* est le même que celui de la valeur sous la sous-clé pilotes ODBC qui décrit le pilote.  
  
 Par exemple, si la source de données par défaut utilise le pilote SQL Server, la valeur sous la sous-clé par défaut peut être :  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  Le pilote par défaut contenu dans la sous-clé par défaut peut faire référence à un DSN utilisateur par défaut ou à un DSN système par défaut. Si un nom de source de nom d’utilisateur par défaut et un DSN système par défaut ont été créés, le pilote par défaut est déterminé par le nom de source de noms qui a été créé en dernier. il est donc possible qu’il ne s’agit pas d’une entrée valide pour le DSN créé en premier.
