---
title: Ajouter des projets au contrôle de code source | Microsoft Docs
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
ms.openlocfilehash: de32cbecdf132f1c881ab9fe5637af3a5c6cd400
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937350"
---
# <a name="add-projects-to-source-control"></a>Ajouter des projets au contrôle de code source
  Les solutions [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] peuvent héberger plusieurs projets de script. La méthode d'ajout d'un projet au contrôle de code source varie selon que la solution à laquelle appartient le projet est ou non sous contrôle de code source. Si la solution est sous contrôle de code source, le projet s'ajoute automatiquement au contrôle de code source lors de l'archivage de la solution. Pour plus d’informations sur l’archivage des solutions, consultez [archiver des fichiers](../../2014/database-engine/check-in-files.md).  
  
 Si la solution à laquelle appartient le projet n'est pas sous contrôle de code source, vous pouvez ajouter la solution au contrôle de code source. Celle-ci ajoute alors automatiquement les projets qu'elle contient au contrôle de code source. Pour plus d’informations sur l’ajout de solutions au contrôle de code source, consultez [Ajouter des solutions au contrôle de code source](../../2014/database-engine/add-solutions-to-source-control.md).  
  
 Si vous ne souhaitez pas ajouter la solution au contrôle de code source, vous pouvez utiliser la commande **Ajouter une sélection au contrôle de code source** pour ajouter le projet manuellement.  
  
 Les objets de base de données ne sont pas protégés directement par le fournisseur de contrôle de code source, mais vous pouvez créer des scripts d'objets de base de données et enregistrer les scripts soumis au contrôle de code source.  
  
### <a name="to-add-a-project-to-source-control"></a>Pour ajouter un projet au contrôle de code source  
  
1.  Dans l'Explorateur de solutions, sélectionnez un projet.  
  
2.  Dans le menu **fichier** , pointez sur **contrôle de code source**, puis cliquez sur **Ajouter les projets sélectionnés au contrôle de code source**.  
  
    > [!NOTE]  
    >  Si vous utilisez la commande **Ajouter les projets sélectionnés au contrôle de code source** pour ajouter un projet qui appartient à une solution sous contrôle de code source, vous êtes invité à indiquer si vous souhaitez ajouter le projet en tant que sous-dossier de la solution sous contrôle de code source ou pour ajouter le projet en tant que dossier distinct.  
  
3.  Si vous y êtes invité, connectez-vous à votre fournisseur de contrôle de code source.  
  
4.  La boîte **de dialogue Ajouter au projet SourceSafe** s’affiche. Le nom de votre projet s’affiche dans la zone **projet** .  
  
5.  Dans la liste des **dossiers** , ouvrez le dossier dans lequel vous souhaitez placer votre projet. Vous pouvez également cliquer sur **créer** pour créer un dossier avec le nom affiché dans la zone **projet** .  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des solutions et des projets au contrôle de code source](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)  
  
  
