---
title: Importer les stratégies vers une instance unique | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: bc5bcd87-663f-41d9-bb7b-b3e083cd63df
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 83d688a72efaaf75305e5077634f70b016bad818
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85039980"
---
# <a name="import-the-policies-to-a-single-instance"></a>Importer les stratégies vers une instance unique
  Dans cette tâche, vous importerez les stratégies des meilleures pratiques que vous souhaitez planifier dans la Gestion basée sur des stratégies sur une instance unique de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="prerequisites"></a>Prérequis  
 Vous devez effectuer cette procédure sur un serveur qui exécute [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] ou une version ultérieure.  
  
### <a name="import-the-best-practices-policies-for-the-database-engine"></a>Importer les stratégies des meilleures pratiques pour le moteur de base de données  
  
1.  Démarrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , puis connectez-vous au [!INCLUDE[ssDE](../includes/ssde-md.md)] .  
  
2.  Dans l’Explorateur d’objets, développez **gestion**, puis gestion de la **stratégie**.  
  
3.  Cliquez avec le bouton droit sur **stratégies**, puis cliquez sur **Importer une stratégie**.  
  
4.  Dans la boîte de dialogue **Importer** , en regard de la zone **fichiers à importer** , cliquez sur le bouton de sélection (**...**).  
  
5.  Dans la liste **regarder dans** , accédez au dossier suivant, qui contient les stratégies des meilleures pratiques :  
  
     **C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**  
  
    > [!NOTE]  
    >  Le chemin d'accès du fichier varie, selon l'emplacement d'installation des fichiers programme [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], si vous exécutez un système d'exploitation 32 bits ou 64 bits, et selon l'identificateur de langue.  
  
6.  Dans la boîte de dialogue **Sélectionner une stratégie** , sélectionnez un ou plusieurs fichiers de stratégie.  
  
     Pour sélectionner des fichiers non adjacents, cliquez sur un fichier, maintenez la touche CTRL enfoncée, puis cliquez sur chaque fichier supplémentaire. Pour sélectionner des fichiers adjacents, cliquez sur le premier fichier dans la séquence, maintenez la touche MAJ enfoncée, puis cliquez sur le dernier fichier.  
  
7.  Une fois que vous avez fini de sélectionner les fichiers, cliquez sur **ouvrir**.  
  
8.  Dans la boîte de dialogue **Importer** , assurez-vous que la liste **État** de la stratégie est définie sur **conserver l’état de la stratégie lors de l’importation** (valeur par défaut), puis cliquez sur **OK**.  
  
     Les stratégies sont importées dans le nœud **stratégies** sous gestion de la **stratégie**. Par défaut, les stratégies importées sont définies sur le mode d'évaluation « à la demande ».  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Planifier les stratégies](../../2014/tutorials/schedule-the-policies.md)  
  
  
