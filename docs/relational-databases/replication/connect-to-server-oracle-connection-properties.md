---
title: "Se connecter au serveur (Oracle), Propri&#233;t&#233;s de connexion | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.oracleconnection.connectionprops.f1"
helpviewer_keywords: 
  - "boîte de dialogue Se connecter au serveur, réplication"
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# Se connecter au serveur (Oracle), Propri&#233;t&#233;s de connexion
  Utilisez le **Propriétés de connexion** onglet de le **se connecter au serveur** boîte de dialogue pour spécifier une option de publication **passerelle** ou **terminé**. Une fois qu'un serveur de publication est identifié, vous ne pouvez pas modifier cette option sans supprimer et reconfigurer ce serveur. Pour plus d’informations, consultez [configurer un serveur de publication Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## Options  
 **Type de serveur de publication**  
 Sélectionnez **passerelle** ou **terminé**. L’option **Complet** est conçue pour fournir des publications transactionnelles et d’instantané avec l’ensemble complet de fonctionnalités prises en charge pour la publication Oracle. L’option **Passerelle** fournit des optimisations de conception spécifiques pour améliorer les performances dans les cas où la réplication sert de passerelle entre les systèmes. L’option **Passerelle** ne peut pas être utilisée si vous avez l’intention de publier la même table dans plusieurs publications transactionnelles. Une table peut apparaître au maximum dans une publication transactionnelle et dans une ou plusieurs publications d'instantané si vous sélectionnez **Passerelle**.  
  
 **Délais d'attente**  
 Spécifiez la durée pendant laquelle le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] distributeur doit essayer de se connecter au serveur de publication Oracle avant une erreur de délai d’attente se produit.  
  
## Voir aussi  
 [Glossaire des termes de la publication Oracle](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Réglage des performances pour les serveurs de publication Oracle](../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)  
  
  