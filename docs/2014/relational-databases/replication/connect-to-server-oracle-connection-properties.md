---
title: Se connecter au serveur (Oracle), Propriétés de connexion | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.connectionprops.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 479b0d562ffb78bc0003ca320eea0a85ab172430
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721689"
---
# <a name="connect-to-server-oracle-connection-properties"></a>Se connecter au serveur (Oracle), Propriétés de connexion
  Utilisez l’onglet **Propriétés de connexion** de la boîte de dialogue **se connecter au serveur** pour spécifier une option de publication **passerelle** ou **complet**. Une fois qu'un serveur de publication est identifié, vous ne pouvez pas modifier cette option sans supprimer et reconfigurer ce serveur. Pour plus d’informations, consultez [Configurer un serveur de publication Oracle](non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Options  
 **Type de serveur de publication**  
 Sélectionnez **Passerelle** ou **Complet**. L’option **complet** est conçue pour fournir des publications transactionnelles et d’instantané avec l’ensemble complet des fonctionnalités prises en charge pour la publication Oracle. L'option **Passerelle** permet l'optimisation de la conception en améliorant les performances pour les cas où la réplication sert de passerelle entre les systèmes. Vous ne pouvez pas utiliser l'option **Passerelle** si vous envisagez de publier la même table dans plusieurs publications transactionnelles. Une table peut apparaître au maximum dans une publication transactionnelle et dans une ou plusieurs publications d'instantané si vous sélectionnez **Passerelle**.  
  
 **Délais d’attente**  
 Spécifiez la durée [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pendant laquelle le serveur de distribution doit essayer de se connecter au serveur de publication Oracle avant qu’une erreur de délai d’attente se produise.  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des termes de la publication Oracle](non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Réglage des performances pour les serveurs de publication Oracle](non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
