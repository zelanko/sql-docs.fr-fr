---
description: Positionnement dans un recordset
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 9d5cdea25dbf14ef5f26d02612f357768acdad61
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452961"
---
# <a name="recordset-positioning"></a>Positionnement dans un recordset
Utilisez la propriété **AbsolutePosition** pour vous déplacer vers un enregistrement, en fonction de sa position ordinale dans l’objet **Recordset** , ou pour déterminer la position ordinale de l’enregistrement actif. Le fournisseur doit prendre en charge les fonctionnalités appropriées pour que cette propriété soit disponible.  
  
 **AbsolutePosition** est de base 1 et est égal à 1 lorsque l’enregistrement actif est le premier enregistrement dans le **Recordset**. Comme mentionné précédemment, vous pouvez obtenir le nombre total d’enregistrements dans l’objet **Recordset** à partir de la propriété **RecordCount** .  
  
 Lorsque vous définissez la propriété **AbsolutePosition** , même s’il s’agit d’un enregistrement dans le cache actuel, ADO recharge le cache avec un nouveau groupe d’enregistrements à partir de l’enregistrement que vous avez spécifié. La propriété **CacheSize** détermine la taille de ce groupe.  
  
> [!NOTE]
>  Vous ne devez pas utiliser la propriété **AbsolutePosition** comme numéro d’enregistrement de substitution. La position d’un enregistrement donné change lorsque vous supprimez un enregistrement précédent. En outre, il n’est pas garanti qu’un enregistrement donné aura la même **AbsolutePosition** si l’objet **Recordset** est à nouveau interrogé ou rouvert. Les signets sont la méthode recommandée pour conserver et retourner à une position donnée et constituent la seule façon de positionner tous les types d’objets **Recordset** .
