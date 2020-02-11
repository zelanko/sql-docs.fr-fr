---
title: Effectuer une évaluation à la demande à l’aide de serveurs inscrits | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: c14034ef-6e0b-4df5-8072-bfb8d90b3172
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: a3a79a6ec655e91264d6fcc00db5a920ad82a21e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66822369"
---
# <a name="perform-an-on-demand-evaluation-by-using-registered-servers"></a>Effectuer une évaluation à la demande à l'aide des serveurs inscrits

  Vous pouvez effectuer une évaluation à la demande des stratégies des meilleures pratiques sur une ou plusieurs instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l'aide des serveurs inscrits. Vous pouvez utiliser des groupes de serveurs locaux ou un serveur d'administration centralisée.  
  
> [!NOTE]  
>  Vous pouvez effectuer une évaluation à la demande des stratégies des meilleures pratiques sur des membres de groupe de serveurs qui exécutent [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] ou une version ultérieure de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Toutefois, vous pouvez recevoir une erreur d'exception si quelques propriétés désignées par une stratégie ne sont pas prises en charge dans [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] ou [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour effectuer cette tâche, vous devez avoir configuré une ou plusieurs inscriptions de serveurs dans les serveurs inscrits. Pour plus d'informations, voir les rubriques suivantes :  
  
-   [Créer ou modifier un groupe de serveurs &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   [Inscrire un serveur connecté &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).  
  
-   [Créer un serveur d’administration centralisée et un groupe de serveurs &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-evaluate-best-practices-policies-against-a-server-group"></a>Pour évaluer les stratégies des meilleures pratiques sur un groupe de serveurs  
  
1.  Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], dans le menu **Affichage** , cliquez sur **Serveurs inscrits**.  
  
2.  Développez **moteur de base de données**, puis développez **groupes**de serveurs locaux ou **serveurs de gestion centralisée**, en fonction de votre configuration.  
  
3.  Effectuez l'une des opérations suivantes :  
  
    -   Pour évaluer les stratégies par rapport à tous les serveurs gérés par le groupe de serveurs local ou le serveur de gestion centralisée, cliquez avec le bouton droit sur le nom du groupe de serveurs local ou le nom du serveur de gestion centralisée, puis cliquez sur **évaluer les stratégies**.  
  
        > [!NOTE]  
        >  Lorsque vous évaluez des stratégies via un serveur d'administration centralisée, les stratégies ne sont pas évaluées sur le serveur d'administration centralisée lui-même.  
  
    -   Pour évaluer les stratégies par rapport à un serveur ou un groupe de serveurs spécifique, développez **groupes de serveurs locaux** ou le nom du serveur de gestion centralisée, cliquez avec le bouton droit sur le serveur ou le groupe de serveurs dont vous souhaitez évaluer les stratégies, puis cliquez sur **évaluer les stratégies**.  
  
4.  Dans la boîte de dialogue **évaluer les stratégies** , en regard de la zone **source** , cliquez sur le bouton de sélection (**...**).  
  
5.  Dans la boîte de dialogue **Sélectionner une source** , vous pouvez sélectionner **fichiers** ou **serveur** comme source des fichiers de stratégie à évaluer. Si vous cliquez sur **serveur**, vous pouvez effectuer une évaluation à la demande des stratégies des meilleures pratiques qui ont été précédemment importées dans la gestion basée sur des stratégies sur un serveur local ou distant. Dans ce didacticiel, vous allez cliquer sur **fichiers**, puis sélectionner les fichiers de stratégie individuels que vous souhaitez évaluer. Pour ce faire, procédez comme suit :  
  
    1.  Cliquez sur **fichiers**.  
  
    2.  En regard de **fichiers**, cliquez sur le bouton de sélection (**...**).  
  
    3.  Sélectionnez un ou plusieurs fichiers de stratégie. XML à évaluer, puis cliquez sur **ouvrir**.  
  
         La liste des fichiers sélectionnés s’affiche dans la zone **fichiers** .  
  
    4.  Dans la boîte de dialogue **Sélectionner une source** , cliquez sur **OK**.  
  
    5.  Si la boîte de dialogue **chargement des stratégies** s’affiche, cliquez sur **Fermer**.  
  
     Les stratégies que vous avez sélectionnées sont répertoriées dans la page sélection de la **stratégie** . Gardez à l'esprit qu'une icône d'avertissement en regard d'une stratégie indique que la stratégie contient des scripts.  
  
6.  Cliquez sur **évaluer** pour évaluer les stratégies.  
  
7.  Pour certains échecs de stratégie, la Gestion basée sur des stratégies vous permet de mettre immédiatement en vigueur la conformité aux stratégies sur la cible. Pour de tels échecs, une case à cocher s'affichera en regard de la stratégie qui a échoué. Si vous activez la case à cocher ou si vous cliquez sur la ligne avec la stratégie qui a échoué, les cases à cocher s’affichent dans le volet Détails de la **cible** en regard des instances cibles dont l’évaluation a échoué. Si l’une des cases à cocher est activée, le bouton **appliquer** devient disponible. Lorsque vous cliquez sur **appliquer**, le paramètre non conforme est automatiquement mis à jour sur les instances cibles que vous avez sélectionnées.  
  
    > [!CAUTION]  
    >  Assurez-vous de bien comprendre le paramètre de stratégie avant de mettre à jour automatiquement une instance cible. Après avoir sélectionné une ou plusieurs cases à cocher, nous vous recommandons de cliquer sur **script**et de choisir un emplacement de sortie afin de pouvoir [!INCLUDE[tsql](../includes/tsql-md.md)] examiner le code sous-jacent avant d’appliquer les modifications.  
  
8.  Pour afficher les résultats détaillés d’une stratégie, cliquez sur la stratégie dans le tableau des **résultats** . La table Détails de la **cible** affiche les détails de chaque instance.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : évaluer les stratégies des meilleures pratiques de façon planifiée](../../2014/tutorials/lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller et appliquer les meilleures pratiques à l’aide de la gestion basée sur des stratégies](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)   
 [Administrer plusieurs serveurs à l’aide de serveurs de gestion centralisée](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
