---
title: Spécifiez une Version comme étant la dernière Version | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- version control services [SQL Server], latest version
- latest file version specified
- file versions [SQL Server]
ms.assetid: 407dffb1-3ecf-461e-835d-124781f26ee7
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 598fc6f2d90220f85cef590600d8fcf397384f28
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040218"
---
# <a name="specify-a-version-as-the-latest-version"></a>Désigner une version comme étant la dernière version
  Lorsque vous archivez un fichier dans le contrôle de code source, la version que vous archivez devient la dernière version. Les utilisateurs qui extraient ou récupèrent la dernière version reçoivent des copies locales du tout dernier élément archivé.  
  
 Dans certains cas, vous pouvez toutefois souhaiter désigner une version antérieure d'un élément comme étant la dernière version. Par exemple, vous effectuez l'extraction d'un fichier, vous le modifiez, vous l'archivez, puis vous décidez d'ignorer vos modifications. Comme vous avez archivé l'élément, il est alors inutile d'annuler l'extraction d'origine. Vous pouvez dans ce cas désigner la version extraite à l'origine comme étant la dernière version de l'élément.  
  
 Vous pouvez désigner une version comme étant la dernière version en procédant comme suit :  
  
-   **L’épinglage d’une version**. Lorsque vous mettez une version de fichier en attente, les versions ultérieures à la version en attente ne sont pas supprimées. Vous pouvez par ailleurs annuler la mise en attente d'un fichier préalablement définie. Lorsque vous effectuez cette opération, la toute dernière version archivée du fichier devient la dernière version. Vous ne pouvez toutefois pas extraire un fichier en attente.  
  
-   **Restauration d’une version spécifiée**. Lorsque vous restaurez une version, toutes les versions ultérieures à la version que vous avez restaurée sont supprimées du contrôle de code source. Vous pouvez alors extraire la dernière version restante.  
  
### <a name="to-pin-a-version"></a>Pour mettre une version en attente  
  
1.  Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], ouvrez la solution.  
  
2.  Dans l'Explorateur de solutions, sélectionnez le fichier que vous souhaitez désigner comme étant la dernière version.  
  
3.  Sur le **fichier** menu, pointez sur **contrôle de code Source** et cliquez sur **ViewHistory**.  
  
4.  Dans le **l’historique de** \<fichier > boîte de dialogue, sélectionnez la version que vous souhaitez spécifier en tant que la dernière version, puis cliquez sur **code confidentiel**.  
  
     Un symbole de mise en attente s'affiche à côté de la version sélectionnée, indiquant qu'il s'agit de la version en cours du fichier. En cas de chargement d'une version différente dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], le système vous demande de recharger le fichier.  
  
### <a name="to-roll-back-to-a-version"></a>Pour restaurer une version  
  
1.  Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], ouvrez la solution.  
  
2.  Dans l'Explorateur de solutions, sélectionnez l'élément que vous souhaitez désigner comme étant la dernière version.  
  
3.  Sur le **fichier** menu, pointez sur **contrôle de code Source** et cliquez sur **historique**.  
  
4.  Dans le **Options d’historique** boîte de dialogue, cliquez sur **OK** pour afficher les **historique du fichier** boîte de dialogue.  
  
5.  Dans le **historique du fichier** , sélectionnez la version que vous voulez spécifier comme étant la dernière version, puis cliquez sur **restauration**.  
  
     Un message, vous notifiant que toutes les versions ultérieures à la version que vous avez sélectionnée seront supprimées, s'affiche.  
  
6.  Cliquez sur **Oui** pour revenir à la version sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les archivages](../../2014/database-engine/manage-checkins.md)   
 [Archiver les fichiers](../../2014/database-engine/check-in-files.md)  
  
  