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
manager: craigg
ms.openlocfilehash: e904d341513047b3940cf5b3fc2ba9538cdb5c8f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764227"
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
