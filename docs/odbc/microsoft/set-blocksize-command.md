---
title: SET BLOCKSIZE Commande ( Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3eb9fbe9df90f7ddafebc6baa029164a578a6da3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300899"
---
# <a name="set-blocksize-command"></a>SET BLOCKSIZE, commande
Précise comment l’espace de disque est alloué pour le stockage des champs de notes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>Arguments  
 *nBytes (en)*  
 Spécifie la taille du bloc dans lequel l’espace disque pour les champs de mémo est alloué. Si *nBytes* est de 0, l’espace disque est alloué en octets simples (blocs de 1 octet). Si *nBytes* est un intégrateur entre 1 et 32, l’espace disque est alloué en blocs *d’octets nBytes* multiplié par 512. Si *nBytes* est supérieur à 32, l’espace disque est alloué en blocs *d’octets nBytes.* Si vous spécifiez une valeur de taille de bloc supérieure à 32, vous pouvez économiser de l’espace disque substantiel.  
  
## <a name="remarks"></a>Notes  
 La valeur par défaut pour SET BLOCKSIZE est de 64. Pour réinitialiser la taille du bloc à une valeur différente après la création du fichier, définissez-le à une nouvelle valeur, puis utilisez COPY pour créer une nouvelle table. La nouvelle table a la taille spécifiée de bloc.
