---
title: Récupérer les fichiers | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], file retrieval
- file retrieval [SQL Server]
- retrieving files
ms.assetid: 37b74426-e262-43b2-a81f-79b1fd1a36ec
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 548fac7dbc7d1f2750a130da9847be406361d8bf
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62843655"
---
# <a name="retrieve-files"></a>Récupérer des fichiers
  Une fois un projet sous contrôle de code source ouvert, vous pouvez utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour récupérer des copies locales des fichiers projet dans le magasin du contrôle de code source et les placer dans le dossier local dans lequel réside le projet.  
  
 Vous pouvez utiliser le contrôle de code source intégré pour récupérer des fichiers à l'aide des deux commandes suivantes :  
  
-   Commande d' **extraction de la dernière version (récursif)**  
  
     Récupère la toute dernière version archivée des fichiers sélectionnés. Si une solution ou un projet est sélectionné, cette commande récupère la dernière version de tous les fichiers de la solution et du projet.  
  
-   Commande d' **extraction**  
  
     Affiche la boîte de dialogue **obtenir** , que vous pouvez utiliser pour récupérer la version la plus récente d’un fichier sélectionné, ou pour récupérer un sous-ensemble des fichiers dans la solution ou le projet sélectionné.  
  
### <a name="to-retrieve-the-latest-version-of-all-the-files-in-a-project"></a>Pour récupérer la dernière version de tous les fichiers d'un projet  
  
1.  Dans l’Explorateur de solutions, sélectionnez le projet.  
  
2.  Dans le menu **fichier** , pointez sur **contrôle de code source**, puis cliquez sur **Télécharger la dernière version (récursif)**.  
  
 Les versions les plus récentes des fichiers du projet sont récupérées et placées à l'emplacement du projet sur votre disque local.  
  
#### <a name="to-retrieve-only-certain-files-in-a-project"></a>Pour récupérer uniquement certains fichiers d'un projet  
  
1.  Dans l'Explorateur de solutions, sélectionnez l'élément à récupérer.  
  
2.  Dans le menu **fichier** , pointez sur **contrôle de code source**, puis cliquez sur **récupérer**.  
  
3.  Dans la boîte de dialogue **récupérer** , cliquez sur **OK**. Si vous avez sélectionné une solution ou un projet dans l'Explorateur de solutions, désactivez les cases à cocher qui apparaissent en regard des éléments que vous ne souhaitez pas récupérer.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue récupérer &#40;contrôle de code source&#41;](../../2014/database-engine/get-dialog-box-source-control.md)   
 [Définir et récupérer les informations de version](../../2014/database-engine/set-and-retrieve-version-information.md)   
 [Afficher l’historique du projet](../../2014/database-engine/view-project-history.md)   
 [Afficher l'état d'un fichier](../../2014/database-engine/view-file-status.md)  
  
  
