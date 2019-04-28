---
title: Base de données de distribution | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configuredistributionwizard.distributiondatabase.f1
ms.assetid: 5b42a083-7a11-41d8-9e3f-320c7c907237
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 283fd67d14d57c3d1d5d60dd9d8de2a159ca6d5e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62721372"
---
# <a name="distribution-database"></a>Base de données de distribution
  La base de données de distribution stocke les métadonnées et les données d'historique pour tous les types de réplications, et les transactions pour la réplication transactionnelle.  
  
 Dans de nombreux cas, une seule base de données de distribution est suffisante. Toutefois, si plusieurs serveurs de publication utilisent un seul serveur de distribution, créez une base de distribution pour chaque serveur de publication Ainsi, vous vous assurerez que les données transitant entre chaque base de données de distribution seront bien séparées. Vous pouvez définir une base de données de distribution pour le serveur de distribution en utilisant l'Assistant Configuration de la distribution. Si nécessaire, définissez des bases de données de distribution supplémentaires dans la boîte de dialogue **Propriétés du serveur de distribution** .  
  
## <a name="options"></a>Options  
 **Nom de la base de données de distribution**  
 Entrez le nom de la base de données de distribution. Le nom par défaut de la base de données de distribution est « distribution ». Si vous définissez un nom, le nom peut contenir jusqu'à 128 caractères et il doit être unique dans une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]et conforme aux règles des identificateurs. Pour plus d'informations, consultez [Database Identifiers](../databases/database-identifiers.md).  
  
 **Dossier du fichier de la base de données de distribution** et **Dossier du fichier-journal de la base de données de distribution**  
 Entrez le chemin d'accès aux fichiers journaux et de base de données de distribution. Les chemins d'accès doivent faire référence à des disques locaux situés sur le serveur de distribution et commencer par une lettre de lecteur local suivie des deux-points (par exemple, C:). Les lettres d'unités mappées et les chemins d'accès réseau ne sont pas valides.  
  
> [!NOTE]  
>  Vous pouvez réduire le délai d'écriture des transactions et améliorer les performances de la réplication en plaçant le journal de la base de données de distribution sur un disque différent de celui de la base de données de distribution.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la distribution](configure-distribution.md)   
 [Configurer la publication et la distribution](configure-publishing-and-distribution.md)   
 [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](view-and-modify-distributor-and-publisher-properties.md)  
  
  
