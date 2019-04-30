---
title: Réduire l’utilisation de l’espace de fichier journal | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- log file space in RDS [ADO]
ms.assetid: 669662a0-e20f-483e-ab28-53f66c524c98
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 061cae6b387611886943aabcfa3dfd99579a59d7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63134396"
---
# <a name="minimizing-log-file-space-usage"></a>Minimisation de l’espace utilisé par un fichier journal
Un fichier journal peut se remplir rapidement (provoquant ainsi l’abandon du serveur) s’il existe un gros volume d’activité sur une base de données SQL Server. Vous pouvez définir le fichier journal sur **vidage au point de contrôle** pour étendre considérablement la durée de vie du fichier journal pour une base de données.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-65"></a>Pour activer le vidage au point de contrôle dans Microsoft SQL Server 6.5  
  
1.  Démarrez Microsoft SQL Server Enterprise Manager, ouvrez l’arborescence pour le serveur, puis ouvrez l’arborescence de la base de données des appareils.  
  
2.  Double-cliquez sur le nom de la base de données sur lequel cette fonctionnalité sera activée.  
  
3.  À partir de la **base de données** onglet, sélectionnez **Truncate**.  
  
4.  À partir de la **Options** onglet, sélectionnez **tronquer le journal sur le point de contrôle**, puis cliquez sur **OK**.  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-70"></a>Pour activer le vidage au point de contrôle dans Microsoft SQL Server 7.0  
  
1.  Démarrez Microsoft SQL Server Enterprise Manager, ouvrez l’arborescence pour le serveur, puis ouvrez l’arborescence de bases de données.  
  
2.  Cliquez sur le nom de la base de données sur lequel cette fonctionnalité sera activée et choisissez **propriétés**.  
  
3.  À partir de la **Options** onglet, sélectionnez **tronquer le journal sur le point de contrôle**, puis cliquez sur **OK**.  
  
 Pour plus d’informations sur la **vidage au point de contrôle** fonctionnalité, consultez la documentation de Microsoft SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


