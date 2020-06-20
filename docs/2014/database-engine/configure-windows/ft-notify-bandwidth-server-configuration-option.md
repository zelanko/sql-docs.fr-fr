---
title: ft notify bandwidth (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- ft notify bandwidth opion
- small memory buffers
- memory [SQL Server], buffers
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dc5839f699d55edf86c5e3e3f0eb001089a0a5dd
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935277"
---
# <a name="ft-notify-bandwidth-server-configuration-option"></a>ft notify bandwidth (option de configuration de serveur)
  Utilisez l’option **ft notify bandwidth** pour spécifier la taille maximale que peut prendre le pool des petites mémoires tampons. Les petites mémoires tampons ont une taille de 64 kilo-octets (Ko). La valeur du paramètre *max* spécifie le nombre maximal de tampons que le gestionnaire de mémoire de texte intégral doit maintenir dans un pool de petites mémoires tampons. Si la `max` valeur est égale à zéro, il n’y a aucune limite supérieure au nombre de mémoires tampons qui peuvent se trouver dans un petit pool de mémoires tampons.  
  
 Le paramètre **min** spécifie le nombre minimal de mémoires tampons devant être maintenues dans le pool des petites mémoires tampons. À la demande du gestionnaire de mémoire [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tous les pools de mémoires tampons supplémentaires sont libérés, mais ce nombre minimal de mémoires tampons est conservé. Toutefois, si la valeur **min** spécifiée est nulle, toutes les mémoires tampons sont libérées.  
  
 Dans certains cas, le nombre de mémoires tampons allouées actuellement est inférieur à la valeur spécifiée par le paramètre **min** .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [ft crawl bandwidth (option de configuration de serveur)](ft-crawl-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
