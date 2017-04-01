---
title: "D&#233;lai d&#39;attente PH (option de configuration de serveur) | Microsoft Docs"
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
  - "limite de temps pour l'attente du gestionnaire de protocole [SQL Server]"
  - "options d’expiration [SQL Server], option ph timeout"
  - "protocoles [SQL Server], expiration"
  - "ph timeout (option)"
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# D&#233;lai d&#39;attente PH (option de configuration de serveur)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilisez l’option ph timeout pour spécifier le délai, en secondes, dont dispose le gestionnaire de protocole de texte intégral pour se connecter à une base de données. La valeur par défaut est 60 secondes. Augmentez la valeur de ph timeout si vos tentatives de connexion dépassent ce délai en raison de problèmes réseau temporaires.  
  
 Le gestionnaire de protocole de texte intégral est hébergé dans l'hôte de démon de filtre et sert à rechercher dans SQL Server les données à indexer en texte intégral. Pour plus d’informations sur les composants de la recherche en texte intégral, consultez [Recherche en texte intégral](../../relational-databases/search/full-text-search.md).  
  
 Lorsque vous tentez d'extraire une ligne de données, si le gestionnaire de protocole ne peut pas se connecter à SQL Server dans le délai spécifié, il émet une erreur de temporisation pour cette ligne. L'outil d'extraction de texte intégral réessaiera ultérieurement. Pour plus d’informations sur l’outil d’extraction de texte intégral, consultez [Alimenter des index de recherche en texte intégral](../../relational-databases/search/populate-full-text-indexes.md).  
  
## Voir aussi  
 [Recherche en texte intégral](../../relational-databases/search/full-text-search.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration du serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  