---
title: Ajouter des projets au contrôle de code Source | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- projects [SQL Server Management Studio], adding
ms.assetid: fd4616b2-a564-4a66-ac53-d1f5cba213c2
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c0936af9b97d08c6bcd5033e61d9fa1c9153272e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62791759"
---
# <a name="add-projects-to-source-control"></a>Ajouter des projets au contrôle de code source
  Les solutions [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] peuvent héberger plusieurs projets de script. La méthode d'ajout d'un projet au contrôle de code source varie selon que la solution à laquelle appartient le projet est ou non sous contrôle de code source. Si la solution est sous contrôle de code source, le projet s'ajoute automatiquement au contrôle de code source lors de l'archivage de la solution. Pour plus d’informations sur l’archivage de solutions, consultez [dans les fichiers](../../2014/database-engine/check-in-files.md).  
  
 Si la solution à laquelle appartient le projet n'est pas sous contrôle de code source, vous pouvez ajouter la solution au contrôle de code source. Celle-ci ajoute alors automatiquement les projets qu'elle contient au contrôle de code source. Pour plus d’informations sur l’ajout de solutions au contrôle de code source, consultez [ajouter des Solutions au contrôle de code Source](../../2014/database-engine/add-solutions-to-source-control.md).  
  
 Si vous ne souhaitez pas ajouter la solution au contrôle de code source, vous pouvez utiliser la **ajouter une sélection au contrôle de code Source** commande pour ajouter le projet manuellement.  
  
 Les objets de base de données ne sont pas protégés directement par le fournisseur de contrôle de code source, mais vous pouvez créer des scripts d'objets de base de données et enregistrer les scripts soumis au contrôle de code source.  
  
### <a name="to-add-a-project-to-source-control"></a>Pour ajouter un projet au contrôle de code source  
  
1.  Dans l'Explorateur de solutions, sélectionnez un projet.  
  
2.  Sur le **fichier** menu, pointez sur **contrôle de code Source**, puis cliquez sur **ajouter les projets sélectionnés au contrôle de code Source**.  
  
    > [!NOTE]  
    >  Si vous utilisez le **ajouter les projets sélectionnés au contrôle de code Source** commande pour ajouter un projet qui appartient à une solution sous contrôle de code source, vous êtes invité si vous souhaitez ajouter le projet en tant que sous-dossier de la solution sous contrôle de code source ou à ajouter le projet comme un dossier distinct.  
  
3.  Si vous y êtes invité, connectez-vous à votre fournisseur de contrôle de code source.  
  
4.  Le **ajouter au projet SourceSafe** boîte de dialogue s’affiche. Le nom de votre projet apparaît dans le **projet** boîte.  
  
5.  Dans le **dossiers** , ouvrez le dossier où vous souhaitez placer votre projet. Vous pouvez également cliquer sur **créer** pour créer un dossier avec le nom affiché dans le **projet** boîte.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des solutions et des projets au contrôle de code source](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)  
  
  
