---
title: SET BLOCKSIZE, commande | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set blocksize command [ODBC]
ms.assetid: 0c11580f-37f5-4a8e-99be-9fb9c44bb433
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4fe84a470f5e877c73701168394cd85d75253fb7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997759"
---
# <a name="set-blocksize-command"></a>SET BLOCKSIZE, commande
Spécifie l’espace disque alloué pour le stockage des champs de Mémo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>Arguments  
 *nBytes*  
 Spécifie la taille du bloc d’allocation d’espace disque pour les champs Mémo. Si *nBytes* est 0, l’espace disque alloué dans un octet (blocs de 1 octet). Si *nBytes* est un entier compris entre 1 et 32, de l’espace disque alloué dans des blocs de *nBytes* octets multipliant par 512. Si *nBytes* est supérieure à 32, espace disque alloué dans des blocs de *nBytes* octets. Si vous spécifiez une valeur de taille de bloc supérieure à 32, vous pouvez économiser l’espace disque important.  
  
## <a name="remarks"></a>Notes  
 La valeur par défaut pour définir la taille de bloc est 64. Pour réinitialiser la taille de bloc sur une autre valeur, une fois que le fichier a été créé, affectez-lui une nouvelle valeur, puis utilisez copie pour créer une nouvelle table. La nouvelle table a la taille de bloc spécifié.
