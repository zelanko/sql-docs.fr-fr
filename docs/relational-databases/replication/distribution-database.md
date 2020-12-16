---
title: Base de données de distribution | Microsoft Docs
description: Dans SQL Server, la base de données de distribution stocke les métadonnées et les données d’historique pour tous les types de réplications, et les transactions pour la réplication transactionnelle.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.configuredistributionwizard.distributiondatabase.f1
ms.assetid: 5b42a083-7a11-41d8-9e3f-320c7c907237
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: 6fa550fd5cbe31535161e25ef86a394d44badcef
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97484881"
---
# <a name="distribution-database"></a>Base de données de distribution
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  La base de données de distribution stocke les métadonnées et les données d'historique pour tous les types de réplications, et les transactions pour la réplication transactionnelle.  
  
 Dans de nombreux cas, une seule base de données de distribution est suffisante. Toutefois, si plusieurs serveurs de publication utilisent un seul serveur de distribution, créez une base de distribution pour chaque serveur de publication Ainsi, vous vous assurerez que les données transitant entre chaque base de données de distribution seront bien séparées. Vous pouvez définir une base de données de distribution pour le serveur de distribution en utilisant l'Assistant Configuration de la distribution. Si nécessaire, définissez des bases de données de distribution supplémentaires dans la boîte de dialogue **Propriétés du serveur de distribution** .  
  
## <a name="options"></a>Options  
 **Nom de la base de données de distribution**  
 Entrez le nom de la base de données de distribution. Le nom par défaut de la base de données de distribution est « distribution ». Si vous définissez un nom, celui-ci peut contenir jusqu’à 128 caractères. Il doit être unique dans une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et être conforme aux règles des identificateurs. Pour plus d'informations, consultez [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
 **Dossier du fichier de la base de données de distribution** et **Dossier du fichier-journal de la base de données de distribution**  
 Entrez le chemin d'accès aux fichiers journaux et de base de données de distribution. Les chemins d'accès doivent faire référence à des disques locaux situés sur le serveur de distribution et commencer par une lettre de lecteur local suivie des deux-points (par exemple, C:). Les lettres d'unités mappées et les chemins d'accès réseau ne sont pas valides.  
  
> [!NOTE]  
>  Vous pouvez réduire le délai d'écriture des transactions et améliorer les performances de la réplication en plaçant le journal de la base de données de distribution sur un disque différent de celui de la base de données de distribution.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)   
 [Configurer la publication et la distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  
