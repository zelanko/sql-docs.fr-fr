---
title: ft notify bandwidth (option de configuration de serveur) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- ft notify bandwidth opion
- small memory buffers
- memory [SQL Server], buffers
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b02d56b6c9874a1d92524280f2f22ef9c7b190b4
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="ft-notify-bandwidth-server-configuration-option"></a>ft notify bandwidth (option de configuration de serveur)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilisez l’option **ft notify bandwidth** pour spécifier la taille maximale que peut prendre le pool des petites mémoires tampons. Les petites mémoires tampons ont une taille de 64 kilo-octets (Ko). La valeur du paramètre *max* spécifie le nombre maximal de tampons que le gestionnaire de mémoire de texte intégral doit maintenir dans un pool de petites mémoires tampons. Si la valeur **max** vaut zéro, aucune limite n’est imposée quant au nombre de tampons que peut contenir un pool de petites mémoires tampons.  
  
 Le paramètre **min** spécifie le nombre minimal de mémoires tampons devant être maintenues dans le pool des petites mémoires tampons. À la demande du gestionnaire de mémoire [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , tous les pools de mémoires tampons supplémentaires sont libérés, mais ce nombre minimal de mémoires tampons est conservé. Toutefois, si la valeur **min** spécifiée vaut zéro, alors toutes les mémoires tampons sont libérées.  
  
 Dans certains cas, le nombre de mémoires tampons allouées actuellement est inférieur à la valeur spécifiée par le paramètre **min** .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [ft crawl bandwidth (option de configuration de serveur)](../../database-engine/configure-windows/ft-crawl-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  

