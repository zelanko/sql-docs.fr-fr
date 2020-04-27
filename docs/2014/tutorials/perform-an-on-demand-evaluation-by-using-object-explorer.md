---
title: Effectuer une évaluation à la demande à l’aide de l’Explorateur d’objets | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: ee6d3b79-18bc-49d3-8a1d-0c0905b990f0
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8d2aadd055334c7ee64871c2fdfe5239c9849e90
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68210945"
---
# <a name="perform-an-on-demand-evaluation-by-using-object-explorer"></a>Effectuer une évaluation à la demande à l'aide de l'Explorateur d'objets
  Dans cette tâche, vous allez utiliser l’Explorateur d’objets pour effectuer une évaluation à la demande des stratégies des meilleures [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] pratiques pour le sur une [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]seule instance de.  
  
> [!NOTE]  
>  Vous pouvez également évaluer des stratégies sur une instance unique via des serveurs inscrits. Pour plus d’informations, consultez [effectuer une évaluation à la demande à l’aide de serveurs inscrits](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Cette leçon est basée sur la version de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  Pour effectuer une évaluation à la demande des stratégies des meilleures pratiques sur des instances qui [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]exécutent, vous devez utiliser la procédure décrite dans la rubrique [effectuer une évaluation à la demande à l’aide de serveurs inscrits](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).  
  
### <a name="to-perform-an-on-demand-evaluation-by-using-object-explorer"></a>Pour effectuer une évaluation à la demande à l'aide de l'Explorateur d'objets  
  
1.  Démarrez [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], puis connectez-vous au [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dans l’Explorateur d’objets, développez **gestion**, gestion de la **stratégie**, cliquez avec le bouton droit sur **stratégies**, puis cliquez sur **évaluer**.  
  
    > [!NOTE]  
    >  Par défaut, l'instance locale est utilisée comme source des stratégies. Si vous avez précédemment importé des stratégies des meilleures pratiques, elles apparaîtront avec toutes les autres stratégies que vous avez créées. Vous pouvez sélectionner l’une des stratégies des meilleures pratiques importées, puis cliquer sur **évaluer**. Si vous n'avez pas importé les stratégies des meilleures pratiques, continuez cette procédure.  
  
3.  Dans la boîte de dialogue **évaluer les stratégies** , en regard de la zone **source** , cliquez sur le bouton de sélection (**...**).  
  
4.  Dans la boîte de dialogue **Sélectionner une source** , vous pouvez sélectionner **fichiers** ou **serveur** comme source des fichiers de stratégie à évaluer. Si vous cliquez sur **serveur**, vous pouvez effectuer une évaluation à la demande des stratégies des meilleures pratiques qui ont été précédemment importées dans la gestion basée sur des stratégies sur un serveur local ou distant. Dans ce didacticiel, vous allez cliquer sur **fichiers**, puis sélectionner les fichiers de stratégie individuels que vous souhaitez évaluer. Pour cela, procédez comme suit :  
  
    1.  Cliquez sur **fichiers**.  
  
    2.  En regard de **fichiers**, cliquez sur le bouton de sélection (**...**).  
  
    3.  Dans la boîte de dialogue **Sélectionner une stratégie** , accédez au dossier suivant, qui contient les stratégies des meilleures pratiques :  
  
         **C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**  
  
        > [!NOTE]  
        >  Le chemin d'accès du fichier varie, selon l'emplacement d'installation des fichiers programme [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], si vous exécutez un système d'exploitation 32 bits ou 64 bits, et selon l'identificateur de langue.  
  
    4.  Sélectionnez un ou plusieurs fichiers de stratégie. XML à évaluer, puis cliquez sur **ouvrir**.  
  
         La liste des fichiers sélectionnés s’affiche dans la zone **fichiers** .  
  
    5.  Dans la boîte de dialogue **Sélectionner une source** , cliquez sur **OK**.  
  
    6.  Si la boîte de dialogue **chargement des stratégies** s’affiche, cliquez sur **Fermer**.  
  
     Les stratégies que vous avez sélectionnées sont répertoriées dans la page sélection de la **stratégie** . Gardez à l'esprit qu'une icône d'avertissement en regard d'une stratégie indique que la stratégie contient des scripts.  
  
5.  Cliquez sur **évaluer** pour évaluer les stratégies.  
  
     Dans le tableau des **résultats** , les résultats de chaque stratégie sont répertoriés. Une icône rouge avec un x indique que la conformité aux stratégies a échoué.  
  
6.  Pour certains échecs de stratégie, la Gestion basée sur des stratégies vous permet de mettre immédiatement en vigueur la conformité aux stratégies sur la cible. Pour de tels échecs, une case à cocher s'affichera en regard de la stratégie qui a échoué. Si vous activez la case à cocher, le bouton **appliquer** devient disponible. Lorsque vous cliquez sur **appliquer**, le paramètre non conforme est automatiquement mis à jour sur l’instance cible.  
  
    > [!CAUTION]  
    >  Assurez-vous de bien comprendre le paramètre de stratégie avant de mettre à jour automatiquement une instance cible. Après avoir sélectionné une ou plusieurs cases à cocher, nous vous recommandons de cliquer sur **script**et de choisir un emplacement de sortie afin de pouvoir [!INCLUDE[tsql](../includes/tsql-md.md)] examiner le code sous-jacent avant d’appliquer les modifications.  
  
7.  Pour afficher les résultats détaillés d’une stratégie, cliquez sur la stratégie dans le tableau des **résultats** .  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Effectuer une évaluation à la demande à l'aide des serveurs inscrits](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)  
  
  
