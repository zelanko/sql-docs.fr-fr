---
title: Exclure des fichiers de contrôle de code Source | Documents Microsoft
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
- excluding files from source control
- source controls [SQL Server Management Studio], file exclusions
ms.assetid: 7dcb6514-db5c-49eb-8b5a-2c766ce39aa7
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 597be5211a36e42320f3f7601c052121ef8aa2a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141863"
---
# <a name="exclude-files-from-source-control"></a>Exclure des fichiers du contrôle de code source
  Si la solution que vous utilisez contient des fichiers qui ne nécessitent pas de services de contrôle de code source, vous pouvez utiliser la **exclure du contrôle de code Source** commande pour exclure le fichier de contrôle de code source. Lorsque vous effectuez cette opération, le fichier reste dans la base de données de [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, mais il ne fait plus l'objet d'archivage ni d'extraction dans le cadre du projet.  
  
 Vous devez utiliser le **exclure du contrôle de code Source** commande uniquement sur les fichiers générés. Un fichier généré est un objet qui peut être intégralement recréé par [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] en fonction du contenu d’un autre fichier de la solution.  
  
### <a name="to-exclude-a-file-from-source-control"></a>Pour exclure un fichier du contrôle de code source  
  
1.  Dans l'Explorateur de solutions, sélectionnez le fichier à exclure.  
  
2.  Sur le **fichier** menu, pointez sur **contrôle de code Source**, puis cliquez sur **exclure**  *\<nom de fichier >* **à partir de Contrôle de code source**.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du contrôle de code source](../../2014/database-engine/source-control-basics.md)   
 [Définir les Options de contrôle de code Source](../../2014/database-engine/set-source-control-options.md)   
 [Modification des connexions de contrôle de code Source](../../2014/database-engine/change-source-control-connections.md)  
  
  