---
title: "Se connecter au serveur (Oracle), Propriétés de connexion | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.oracleconnection.connectionprops.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f65a185a723debd6ff1e8d2d240409521fe4c50f
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-oracle-connection-properties"></a>Se connecter au serveur (Oracle), Propriétés de connexion
  L'onglet **Propriétés de connexion** de la boîte de dialogue **Se connecter au serveur** permet de spécifier une option de publication **Passerelle** ou **Complet**. Une fois qu'un serveur de publication est identifié, vous ne pouvez pas modifier cette option sans supprimer et reconfigurer ce serveur. Pour plus d’informations, consultez [Configurer un serveur de publication Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Options  
 **Type de serveur de publication**  
 Sélectionnez **Passerelle** ou **Complet**. L'option **Complet** a pour but de fournir un instantané et des publications transactionnelles avec le jeu complet de fonctionnalités prises en charge pour le serveur de publication Oracle. L’option **Passerelle** fournit des optimisations de conception spécifiques pour améliorer les performances dans les cas où la réplication sert de passerelle entre les systèmes. L’option **Passerelle** ne peut pas être utilisée si vous avez l’intention de publier la même table dans plusieurs publications transactionnelles. Une table peut apparaître au maximum dans une publication transactionnelle et dans une ou plusieurs publications d'instantané si vous sélectionnez **Passerelle**.  
  
 **Délais d'attente**  
 Indiquez la durée pendant laquelle le serveur de distribution [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit essayer de se connecter au serveur de publication Oracle avant qu'une erreur de temporisation ne se produise.  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des termes de la publication Oracle](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Performance Tuning for Oracle Publishers](../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
