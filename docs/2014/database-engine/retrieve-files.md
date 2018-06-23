---
title: Récupérer des fichiers | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- version control services [SQL Server], file retrieval
- file retrieval [SQL Server]
- retrieving files
ms.assetid: 37b74426-e262-43b2-a81f-79b1fd1a36ec
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f1b53eb99abc77e809bd7aaac30f8f218cd4ee03
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041173"
---
# <a name="retrieve-files"></a>Récupérer des fichiers
  Une fois un projet sous contrôle de code source ouvert, vous pouvez utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour récupérer des copies locales des fichiers projet dans le magasin du contrôle de code source et les placer dans le dossier local dans lequel réside le projet.  
  
 Vous pouvez utiliser le contrôle de code source intégré pour récupérer des fichiers à l'aide des deux commandes suivantes :  
  
-   **Obtenir la dernière Version (récursif)** commande  
  
     Récupère la toute dernière version archivée des fichiers sélectionnés. Si une solution ou un projet est sélectionné, cette commande récupère la dernière version de tous les fichiers de la solution et du projet.  
  
-   **Obtenir** commande  
  
     Affiche la **obtenir** la boîte de dialogue, vous pouvez utiliser pour récupérer la version la plus récente d’un fichier sélectionné ou pour récupérer un sous-ensemble des fichiers dans le projet ou la solution sélectionnée.  
  
### <a name="to-retrieve-the-latest-version-of-all-the-files-in-a-project"></a>Pour récupérer la dernière version de tous les fichiers d'un projet  
  
1.  Dans l'Explorateur de solutions, sélectionnez le projet.  
  
2.  Sur le **fichier** menu, pointez sur **contrôle de code Source**, puis cliquez sur **obtenir la dernière Version (récursif)**.  
  
 Les versions les plus récentes des fichiers du projet sont récupérées et placées à l'emplacement du projet sur votre disque local.  
  
#### <a name="to-retrieve-only-certain-files-in-a-project"></a>Pour récupérer uniquement certains fichiers d'un projet  
  
1.  Dans l'Explorateur de solutions, sélectionnez l'élément à récupérer.  
  
2.  Sur le **fichier** menu, pointez sur **contrôle de code Source**, puis cliquez sur **obtenir**.  
  
3.  Dans le **obtenir** boîte de dialogue, cliquez sur **OK**. Si vous avez sélectionné une solution ou un projet dans l'Explorateur de solutions, désactivez les cases à cocher qui apparaissent en regard des éléments que vous ne souhaitez pas récupérer.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue obtenir &#40;contrôle de code Source&#41;](../../2014/database-engine/get-dialog-box-source-control.md)   
 [Définir et récupérer des informations de Version](../../2014/database-engine/set-and-retrieve-version-information.md)   
 [Afficher l’historique de projet](../../2014/database-engine/view-project-history.md)   
 [Afficher l’état de fichier](../../2014/database-engine/view-file-status.md)  
  
  