---
title: Spécifier une version comme étant la dernière version | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], latest version
- latest file version specified
- file versions [SQL Server]
ms.assetid: 407dffb1-3ecf-461e-835d-124781f26ee7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f34631e979ded7a329939c23a758ccc0c9aea959
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62773475"
---
# <a name="specify-a-version-as-the-latest-version"></a>Désigner une version comme étant la dernière version
  Lorsque vous archivez un fichier dans le contrôle de code source, la version que vous archivez devient la dernière version. Les utilisateurs qui extraient ou récupèrent la dernière version reçoivent des copies locales du tout dernier élément archivé.  
  
 Dans certains cas, vous pouvez toutefois souhaiter désigner une version antérieure d'un élément comme étant la dernière version. Par exemple, vous effectuez l'extraction d'un fichier, vous le modifiez, vous l'archivez, puis vous décidez d'ignorer vos modifications. Comme vous avez archivé l'élément, il est alors inutile d'annuler l'extraction d'origine. Vous pouvez dans ce cas désigner la version extraite à l'origine comme étant la dernière version de l'élément.  
  
 Vous pouvez désigner une version comme étant la dernière version en procédant comme suit :  
  
-   **Épinglage d’une version**. Lorsque vous mettez une version de fichier en attente, les versions ultérieures à la version en attente ne sont pas supprimées. Vous pouvez par ailleurs annuler la mise en attente d'un fichier préalablement définie. Lorsque vous effectuez cette opération, la toute dernière version archivée du fichier devient la dernière version. Vous ne pouvez toutefois pas extraire un fichier en attente.  
  
-   **Restauration d’une version spécifiée**. Lorsque vous restaurez une version, toutes les versions ultérieures à la version que vous avez restaurée sont supprimées du contrôle de code source. Vous pouvez alors extraire la dernière version restante.  
  
### <a name="to-pin-a-version"></a>Pour mettre une version en attente  
  
1.  Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], ouvrez la solution.  
  
2.  Dans l'Explorateur de solutions, sélectionnez le fichier que vous souhaitez désigner comme étant la dernière version.  
  
3.  Dans le menu **fichier** , pointez sur **contrôle de code source** , puis cliquez sur **ViewHistory**.  
  
4.  Dans la boîte **de dialogue historique du** \<fichier>, sélectionnez la version que vous souhaitez spécifier comme la plus récente, puis cliquez sur **épingler**.  
  
     Un symbole de mise en attente s'affiche à côté de la version sélectionnée, indiquant qu'il s'agit de la version en cours du fichier. En cas de chargement d'une version différente dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], le système vous demande de recharger le fichier.  
  
### <a name="to-roll-back-to-a-version"></a>Pour restaurer une version  
  
1.  Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], ouvrez la solution.  
  
2.  Dans l'Explorateur de solutions, sélectionnez l'élément que vous souhaitez désigner comme étant la dernière version.  
  
3.  Dans le menu **fichier** , pointez sur **contrôle de code source** , puis cliquez sur **historique**.  
  
4.  Dans la boîte de dialogue **options d’historique** , cliquez sur **OK** pour afficher la boîte **de dialogue historique du fichier** .  
  
5.  Dans la zone **historique du fichier** , sélectionnez la version que vous souhaitez spécifier comme version la plus récente, puis cliquez sur **restaurer**.  
  
     Un message, vous notifiant que toutes les versions ultérieures à la version que vous avez sélectionnée seront supprimées, s'affiche.  
  
6.  Cliquez sur **Oui** pour revenir à la version sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les archivages](../../2014/database-engine/manage-checkins.md)   
 [Archiver des fichiers](../../2014/database-engine/check-in-files.md)  
  
  
