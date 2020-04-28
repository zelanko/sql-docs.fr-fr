---
title: Positionnement du Recordset | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- record positioning [ADO]
- Recordset object [ADO]
- repositioning record [ADO]
- AbsolutePosition property [ADO]
ms.assetid: c8f6fbcb-6675-4133-b37e-430de43949c1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cdce4c7b08a8b15cdb0a9ee1111a216aeef005bf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67924433"
---
# <a name="recordset-positioning"></a>Positionnement dans un recordset
Utilisez la propriété **AbsolutePosition** pour vous déplacer vers un enregistrement, en fonction de sa position ordinale dans l’objet **Recordset** , ou pour déterminer la position ordinale de l’enregistrement actif. Le fournisseur doit prendre en charge les fonctionnalités appropriées pour que cette propriété soit disponible.  
  
 **AbsolutePosition** est de base 1 et est égal à 1 lorsque l’enregistrement actif est le premier enregistrement dans le **Recordset**. Comme mentionné précédemment, vous pouvez obtenir le nombre total d’enregistrements dans l’objet **Recordset** à partir de la propriété **RecordCount** .  
  
 Lorsque vous définissez la propriété **AbsolutePosition** , même s’il s’agit d’un enregistrement dans le cache actuel, ADO recharge le cache avec un nouveau groupe d’enregistrements à partir de l’enregistrement que vous avez spécifié. La propriété **CacheSize** détermine la taille de ce groupe.  
  
> [!NOTE]
>  Vous ne devez pas utiliser la propriété **AbsolutePosition** comme numéro d’enregistrement de substitution. La position d’un enregistrement donné change lorsque vous supprimez un enregistrement précédent. En outre, il n’est pas garanti qu’un enregistrement donné aura la même **AbsolutePosition** si l’objet **Recordset** est à nouveau interrogé ou rouvert. Les signets sont la méthode recommandée pour conserver et retourner à une position donnée et constituent la seule façon de positionner tous les types d’objets **Recordset** .
