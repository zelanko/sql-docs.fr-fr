---
title: Ouvrir des Solutions à partir du contrôle de code Source | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- opening solutions
- solutions [SQL Server Management Studio], opening
ms.assetid: a96a1f0d-0183-4587-a3b0-4598309cbdd2
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0767df9d8ad010e17560b1f2b5e2e227d52a9f99
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285695"
---
# <a name="open-solutions-from-source-control"></a>Ouvrir des solutions à partir du contrôle de code source
  Vous pouvez utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour ouvrir des solutions directement à partir du contrôle de code source. Lorsque vous effectuez cette opération, l'environnement Studio crée une copie de la toute dernière version des fichiers solutions à l'emplacement que vous avez spécifié.  
  
 Si aucune copie locale de la solution ne figure sur votre disque local, vous devez ouvrir le projet à partir du contrôle de code source avant de pouvoir utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour extraire la solution ou récupérer les fichiers solutions.  
  
> [!NOTE]  
>  Si vous disposez déjà d'une copie locale de la solution dont vous procédez à l'ouverture à partir du contrôle de code source, le système vous demande de remplacer la copie locale.  
  
### <a name="to-open-a-solution-from-source-control"></a>Pour ouvrir une solution à partir du contrôle de code source  
  
1.  Sur le **fichier** menu, pointez sur **contrôle de code Source**, puis cliquez sur **ouvert à partir d’un contrôle de code Source**.  
  
2.  Si le système vous le demande, connectez-vous à [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.  
  
3.  Dans le **créer un projet local à partir de SourceSafe** boîte de dialogue, sélectionnez le dossier qui contient la solution que vous souhaitez ouvrir, puis cliquez sur **OK**.  
  
4.  Si un dossier de travail pour la solution existe déjà sur votre disque dur local, le **créer un nouveau projet dans le dossier** zone change et indique le répertoire local. En l'absence de dossier de travail pour la solution en question, vous pouvez indiquer le dossier local dans lequel vous souhaitez ouvrir la solution ou encore naviguer jusqu'à lui.  
  
5.  Dans le **ouvrir une Solution** boîte de dialogue, sélectionnez le fichier solution, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Ouvrir des projets à partir du contrôle de code source](../../2014/database-engine/open-projects-from-source-control.md)  
  
  
