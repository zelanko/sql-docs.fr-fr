---
title: "Bande passante de l&#39;analyse de texte int&#233;gral (option de configuration de serveur) | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "mémoires tampons volumineuses"
  - "mémoire [SQL Server], tampons"
  - "ft crawl bandwidth (option)"
ms.assetid: e5864ad9-92f5-43b5-95de-46d68ded8694
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Bande passante de l&#39;analyse de texte int&#233;gral (option de configuration de serveur)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilisez l’option **Bande passante de l’analyse de texte intégral** pour spécifier la taille jusqu’à laquelle le pool des mémoires tampons volumineuses peut croître. Les mémoires tampons volumineuses ont une taille de 4 mégaoctets (Mo). La valeur du paramètre **max** spécifie le nombre maximal de mémoires tampons que le gestionnaire de mémoire de texte intégral doit conserver dans un pool de mémoires tampons volumineuses. Si la valeur **max** est nulle, il n’existe aucune limite supérieure au nombre possible de mémoires tampons dans un pool de mémoires tampons volumineuses.  
  
 La valeur du paramètre **min** spécifie le nombre minimal de mémoires tampons qui doivent être conservées dans le pool de mémoires tampons volumineuses. À la demande du gestionnaire de mémoire [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tous les pools de mémoires tampons supplémentaires sont libérés, mais ce nombre minimal de mémoires tampons est conservé. Toutefois, si la valeur **min** spécifiée est nulle, toutes les mémoires tampons sont libérées.  
  
 Dans certains cas, le nombre de mémoires tampons actuellement allouées est inférieur à la valeur spécifiée par le paramètre **min**.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Bande passante de la notification de texte intégral (option de configuration de serveur)](../../database-engine/configure-windows/ft-notify-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  