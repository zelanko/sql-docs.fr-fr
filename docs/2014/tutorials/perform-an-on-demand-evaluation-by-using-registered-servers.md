---
title: Effectuer une évaluation de la demande à l’aide de serveurs inscrits | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: c14034ef-6e0b-4df5-8072-bfb8d90b3172
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 127e0dbeef729c21c7155d7d3d7edf6f21a444c1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48182419"
---
# <a name="perform-an-on-demand-evaluation-by-using-registered-servers"></a>Effectuer une évaluation à la demande à l'aide des serveurs inscrits
  Vous pouvez effectuer une évaluation à la demande des stratégies des meilleures pratiques sur une ou plusieurs instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l'aide des serveurs inscrits. Vous pouvez utiliser des groupes de serveurs locaux ou un serveur d'administration centralisée.  
  
> [!NOTE]  
>  Vous pouvez effectuer une évaluation à la demande des stratégies des meilleures pratiques sur des membres de groupe de serveurs qui exécutent [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] ou une version ultérieure de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Toutefois, vous pouvez recevoir une erreur d'exception si quelques propriétés désignées par une stratégie ne sont pas prises en charge dans [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] ou [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)].  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette tâche, vous devez avoir configuré une ou plusieurs inscriptions de serveurs dans les serveurs inscrits. Pour plus d'informations, consultez les rubriques suivantes :  
  
-   [Créer ou modifier un groupe de serveurs &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   [Inscrire un serveur connecté &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).  
  
-   [Créer un serveur d’administration centralisée et un groupe de serveurs &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-evaluate-best-practices-policies-against-a-server-group"></a>Pour évaluer les stratégies des meilleures pratiques sur un groupe de serveurs  
  
1.  Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], dans le menu **Affichage** , cliquez sur **Serveurs inscrits**.  
  
2.  Développez **moteur de base de données**, puis développez soit **groupes de serveurs locaux**, ou **des serveurs d’administration centrale**, selon votre configuration.  
  
3.  Effectuez l'une des opérations suivantes :  
  
    -   Pour évaluer les stratégies sur tous les serveurs qui sont gérés par le groupe de serveurs local ou le serveur d’administration centrale, cliquez sur le nom de groupe de serveur local ou le nom de serveur d’administration centrale, puis cliquez sur **évaluer les stratégies** .  
  
        > [!NOTE]  
        >  Lorsque vous évaluez des stratégies via un serveur d'administration centralisée, les stratégies ne sont pas évaluées sur le serveur d'administration centralisée lui-même.  
  
    -   Pour évaluer les stratégies sur un serveur spécifique ou un groupe de serveurs, développez **groupes de serveurs locaux** ou le nom, cliquez sur le serveur ou du groupe que vous souhaitez évaluer les stratégies par rapport à, puis cliquez sur le serveur d’administration centralisée **Évaluer les stratégies**.  
  
4.  Dans le **évaluer les stratégies** boîte de dialogue, ensuite la **Source** , cliquez sur le bouton de sélection (**...** ) bouton.  
  
5.  Dans le **sélectionner une Source** boîte de dialogue, vous pouvez sélectionner **fichiers** ou **Server** comme source des fichiers de stratégie à évaluer. Si vous cliquez sur **Server**, vous pouvez effectuer une évaluation de la demande de n’importe quel stratégies des meilleures pratiques qui ont été précédemment importées dans la gestion basée sur un serveur local ou distant. Dans ce didacticiel, vous devrez cliquer sur **fichiers**, puis sélectionnez les fichiers de stratégie individuels que vous souhaitez évaluer. Pour cela, procédez comme suit :  
  
    1.  Cliquez sur **fichiers**.  
  
    2.  Regard **fichiers**, cliquez sur le bouton de sélection (**...** ) bouton.  
  
    3.  Sélectionnez un ou plusieurs fichiers de stratégie .xml à évaluer, puis cliquez sur **Open**.  
  
         La liste des fichiers sélectionnés s’affiche dans le **fichiers** boîte.  
  
    4.  Dans le **sélectionner une Source** boîte de dialogue, cliquez sur **OK**.  
  
    5.  Si le **chargement de stratégies** boîte de dialogue s’affiche, cliquez sur **fermer**.  
  
     Les stratégies que vous avez sélectionnés sont répertoriés dans le **sélection de la stratégie** page. Gardez à l'esprit qu'une icône d'avertissement en regard d'une stratégie indique que la stratégie contient des scripts.  
  
6.  Cliquez sur **Evaluate** pour évaluer les stratégies.  
  
7.  Pour certains échecs de stratégie, la Gestion basée sur des stratégies vous permet de mettre immédiatement en vigueur la conformité aux stratégies sur la cible. Pour de tels échecs, une case à cocher s'affichera en regard de la stratégie qui a échoué. Si vous activez la case à cocher, ou cliquez sur la ligne avec la stratégie ayant échoué, les cases à cocher s’affichent dans le **détails sur les cibles** volet en regard des instances cibles qui a échoué à l’évaluation. Si une des cases à cocher est sélectionnée, le **appliquer** bouton devient disponible. Lorsque vous cliquez sur **appliquer**, le paramètre non conforme est actualisé automatiquement sur les instances cibles que vous avez sélectionné.  
  
    > [!CAUTION]  
    >  Assurez-vous de bien comprendre le paramètre de stratégie avant de mettre à jour automatiquement une instance cible. Nous vous recommandons d’après avoir sélectionné une ou plusieurs cases à cocher, **Script**, puis choisissez un emplacement de sortie afin que vous puissiez examiner sous-jacent [!INCLUDE[tsql](../includes/tsql-md.md)] avant d’appliquer les modifications de code.  
  
8.  Pour afficher les résultats détaillés pour une stratégie, cliquez sur la stratégie dans le **résultats** table. Le **détails sur les cibles** table affiche les détails pour chaque instance.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : Évaluer les stratégies de bonnes pratiques de façon planifiée](../../2014/tutorials/lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller et appliquer les bonnes pratiques à l’aide de gestion basée sur des stratégies](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)   
 [Administrer plusieurs serveurs à l’aide de serveurs de gestion centralisée](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
