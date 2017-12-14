---
title: "Notes de publication de SQL Server 2012 SP2 | Microsoft Docs"
ms.prod: sql-server
ms.prod_service: sql-non-specified
ms.service: server-general
ms.component: 
ms.technology: server-general
ms.custom: 
ms.date: 01/31/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67cb8b3e-3d82-47f4-840d-0f12a3bff565
caps.latest.revision: "6"
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 83969d05f234dc5e6384754971ca6eb5a2621006
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sql-server-2012-sp2-release-notes"></a>Notes de publication de SQL Server 2012 SP2
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)] Ces notes de publication décrivent des problèmes dont vous devez avoir connaissance avant d’installer ou de dépanner SQL Server 2012 Service Pack 2. Les notes de publication sont disponibles uniquement en ligne, et non sur un support d’installation. Elles sont mises à jour régulièrement à mesure que des problèmes sont identifiés. Pour plus d'informations, consultez [Bogues corrigés dans SQL Server 2012 Service Pack 2](http://support.microsoft.com/KB/2958429) .  
  
## <a name="choose-the-correct-file-to-download-and-install"></a>Choisir le fichier approprié à télécharger et installer  
Utilisez le tableau suivant pour identifier l'emplacement et le nom du fichier à télécharger en fonction de la version installée actuellement. Les pages de téléchargement indiquent la configuration système requise et contiennent des instructions d'installation de base.  
  
||||  
|-|-|-|  
|**La version installée actuellement est...**|**Vous souhaitez…**|**Téléchargez et installez...**|  
|Installations 32 bits :|||  
|Une version 32 bits de n’importe quelle édition de SQL Server 2012|Effectuer la mise à niveau vers la version 32 bits de SQL Server 2012 SP2|**SQLServer2012SP2-KB2958429-**<arch>**-**<lang id>**.exe** à partir de la [page de téléchargement de SQL Server 2012 SP2](http://go.microsoft.com/fwlink/?LinkID=401006)|  
|Une version 32 bits de SQL Server 2012 RTM Express|Effectuer la mise à niveau vers la version 32 bits de SQL Server 2012 Express SP2|**SQLEXPR_**<arch>**8**<lang>**.msi** à partir de la [page de téléchargement de SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|Une version 32 bits de seulement le client et les outils de gestion pour SQL Server 2012 (y compris SQL Server 2012 Management Studio)|Effectuer la mise à niveau du client et des outils de gestion vers la version 32 bits de SQL Server 2012 SP2|**SQLEXPRWT_**<arch>**8**<lang>**.msi** à partir de la [page de téléchargement de SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|Une version 32 bits de SQL Server 2012 Management Studio Express|Effectuer la mise à niveau vers la version 32 bits de SQL Server 2012 SP2 Management Studio Express|**SQLManagementStudio_**<arch>**_**<lang>**.msi** à partir de la [page de téléchargement de SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|Une version 32 bits d'une édition quelconque de SQL Server 2012 et une version 32 bits du client et des outils de gestion (y compris SQL Server 2012 RTM Management Studio)|Effectuer la mise à niveau de tous les produits vers la version 32 bits de SQL Server 2012 SP2|**SQLEXPRADV_**<arch>**_**<lang>**.msi** à partir de la [page de téléchargement de SQL Server 2012 SP2 Express.](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|Une version 32 bits d'un ou plusieurs outils du [Feature Pack Microsoft SQL Server 2012 RTM](http://www.microsoft.com/download/details.aspx?id=29065) ou du [Feature Pack Microsoft SQL Server 2012 SP1](http://go.microsoft.com/fwlink/p/?LinkID=268266)|Effectuer la mise à niveau des outils vers la version 32 bits du Feature Pack Microsoft SQL Server 2012 SP2|Un ou plusieurs outils à partir de la [page de téléchargement du Feature Pack Microsoft SQL Server 2012 SP2](http://go.microsoft.com/fwlink/?LinkID=401008)|  
|Installations 64 bits :|||  
|Une version 64 bits d'une édition quelconque de SQL Server 2012|Effectuer la mise à niveau vers la version 64 bits de SQL Server 2012 SP2|SQLServer2012SP2-KB2958429-<arch>-<langid>.exe à partir de la [page de téléchargement de SQL Server 2012 SP2](http://go.microsoft.com/fwlink/?LinkID=401006)|  
|Version 64 bits de SQL Server 2012 RTM Express|Effectuer la mise à niveau vers la version 64 bits de SQL Server 2012 SP2|**SQLEXPR_**<arch>**8**<lang>**.msi** à partir de la [page de téléchargement de SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|Une version 64 bits uniquement du client et des outils de gestion de SQL Server 2012 (y compris SQL Server 2012 Management Studio)|Effectuer la mise à niveau du client et des outils de gestion vers la version 64 bits de SQL Server 2012 SP2|**SQLEXPRWT_**<arch>**8**<lang>**.msi** à partir de la [page de téléchargement de SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|Version 64 bits de SQL Server 2012 Management Studio Express|Effectuer la mise à niveau vers la version 64 bits de SQL Server 2012 SP2 Management Studio Express|**SQLManagementStudio_**<arch>**_**<lang>**.msi** à partir de la [page de téléchargement de SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|Une version 64 bits d'un ou plusieurs outils du [Feature Pack Microsoft SQL Server 2012 RTM](http://www.microsoft.com/download/details.aspx?id=29065) ou du [Feature Pack Microsoft SQL Server 2012 SP1](http://go.microsoft.com/fwlink/p/?LinkID=268266)|Effectuer la mise à niveau des outils vers la version 64 bits du Feature Pack Microsoft SQL Server 2012 SP2|Un ou plusieurs outils à partir de la [page de téléchargement du Feature Pack Microsoft SQL Server 2012 SP2](http://go.microsoft.com/fwlink/?LinkID=401008)|  
  
