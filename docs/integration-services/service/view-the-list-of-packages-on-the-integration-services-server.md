---
title: Afficher la liste des Packages sur le serveur Integration Services | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67a992d1-7524-4f4b-b3d8-ebd9e5ea82a8
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7686512a05d243f1802d1dd5b0d27bd777210161
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="view-the-list-of-packages-on-the-integration-services-server"></a>Afficher la liste des packages sur le serveur Integration Services
  Vous pouvez afficher la liste des packages stockés sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de deux façons :  
  
 Accès à [!INCLUDE[tsql](../../includes/tsql-md.md)]  
 Pour afficher la liste des packages stockés sur le serveur, interrogez la vue [catalog.packages &#40;base de données SSISDB&#41;](../../integration-services/system-views/catalog-packages-ssisdb-database.md).  
  
 Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
 Pour afficher les packages stockés sur le serveur à l’aide de l’Explorateur d’objets dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], procédez comme indiqué ci-dessous.  
  
### <a name="to-view-packages-using-includessmanstudiofullincludesssmanstudiofull-mdmd"></a>Pour afficher les packages à l’aide de[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous au serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Autrement dit, connectez-vous à l'instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui héberge la base de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
2.  Dans l'Explorateur d'objets, développez l'arborescence pour afficher le nœud **Integration Services Catalogues** .  
  
3.  Développez le nœud **Catalogues Integration Services** pour afficher le nœud **SSISDB** .  
  
4.  Développez le nœud **SSISDB** pour afficher une liste d'un ou de plusieurs dossiers. Chaque dossier contient un ou plusieurs projets dans le dossier **Projets** et chaque projet contient un ou plusieurs packages dans le dossier **Packages** .  
  
  
