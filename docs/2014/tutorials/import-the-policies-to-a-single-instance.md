---
title: Importer les stratégies à une seule Instance | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc5bcd87-663f-41d9-bb7b-b3e083cd63df
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 945cd03bb574bc180af5567888a6d171966bccf6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141669"
---
# <a name="import-the-policies-to-a-single-instance"></a>Importer les stratégies vers une instance unique
  Dans cette tâche, vous importerez les stratégies des meilleures pratiques que vous souhaitez planifier dans la Gestion basée sur des stratégies sur une instance unique de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="prerequisites"></a>Prérequis  
 Vous devez effectuer cette procédure sur un serveur qui exécute [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] ou une version ultérieure.  
  
### <a name="import-the-best-practices-policies-for-the-database-engine"></a>Importer les stratégies des meilleures pratiques pour le moteur de base de données  
  
1.  Démarrer [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], puis connectez-vous à le [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dans l’Explorateur d’objets, développez **gestion**, puis développez **gestion des stratégies de**.  
  
3.  Avec le bouton droit **stratégies**, puis cliquez sur **stratégie d’importation**.  
  
4.  Dans le **importer** boîte de dialogue, à côté du **fichiers à importer** , cliquez sur le bouton de sélection (**...** ) bouton.  
  
5.  Dans le **Regarder dans** liste, recherchez le dossier suivant, qui contient les stratégies des meilleures pratiques :  
  
     **C:\Program fichiers (x86) \Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**  
  
    > [!NOTE]  
    >  Le chemin d'accès du fichier varie, selon l'emplacement d'installation des fichiers programme [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], si vous exécutez un système d'exploitation 32 bits ou 64 bits, et selon l'identificateur de langue.  
  
6.  Dans le **sélectionner la stratégie** boîte de dialogue, sélectionnez Stratégie d’un ou plusieurs fichiers.  
  
     Pour sélectionner des fichiers non adjacents, cliquez sur un fichier, maintenez la touche CTRL enfoncée, puis cliquez sur chaque fichier supplémentaire. Pour sélectionner des fichiers adjacents, cliquez sur le premier fichier dans la séquence, maintenez la touche MAJ enfoncée, puis cliquez sur le dernier fichier.  
  
7.  Lorsque vous avez fini de sélectionner les fichiers, cliquez sur **ouvrir**.  
  
8.  Dans le **importer** boîte de dialogue zone, assurez-vous que le **état de la stratégie** liste de **conserver l’état de la stratégie lors de l’importation** (la valeur par défaut), puis cliquez sur **OK**.  
  
     Les stratégies sont importées dans le **stratégies** nœud sous **gestion des stratégies de**. Par défaut, les stratégies importées sont définies sur le mode d'évaluation « à la demande ».  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Planifier les stratégies](../../2014/tutorials/schedule-the-policies.md)  
  
  