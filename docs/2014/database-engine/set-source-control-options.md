---
title: Définir les options de contrôle de code source | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Source_Control.Visual_SourceSafe
- VS.ToolsOptionsPages.Source_Control.General
- VS.ToolsOptionsPages.Source_Control.Environment
helpviewer_keywords:
- source controls [SQL Server Management Studio], options
ms.assetid: b2c6ca00-46f0-4f86-b067-07bae779c147
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0a654932689785d96aaff049551faf19494c311a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62843719"
---
# <a name="set-source-control-options"></a>Définir les options du contrôle de code source
  Pour pouvoir bénéficier des fonctionnalités du contrôle de code source intégrées à [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], vous devez préalablement configurer les options du contrôle de code source relatives aux différents environnements dans lesquels vous travaillez.  
  
 Vous configurez les options de contrôle de code source à l’aide de la boîte de dialogue **options** pour configurer un ou plusieurs rôles de contrôle de code source. Un rôle comporte une description générale de la configuration dans laquelle vous utilisez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et les options du contrôle de code source associées à cette configuration.  
  
 Par exemple, si vous êtes un développeur indépendant, vous ne créez généralement pas de conflits avec d'autres utilisateurs en conservant des fichiers extraits après les avoir archivés. Par conséquent, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] définit un rôle Développeur indépendant. Pour ce rôle, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] sélectionne automatiquement l’option **conserver les éléments extraits lors de l’archivage** .  
  
 Comme vous pouvez définir et personnaliser des rôles, vous pouvez travailler dans différentes configurations de développement sans avoir à redéfinir intégralement le contrôle de code source chaque fois que vous passez d'une configuration à une autre.  
  
### <a name="to-set-source-control-options"></a>Pour configurer les options du contrôle de code source  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Dans la boîte de dialogue **options** , développez **contrôle de code source**, puis cliquez sur la page **sélection du plug-** in.  
  
     **Plug-in de contrôle de code source actif**  
     Sélectionnez le contrôle de code source que vous souhaitez utiliser dans cette liste. Le client du produit de contrôle de code source doit être installé sur votre ordinateur pour apparaître dans la liste. Si aucun client de contrôle de code source n'est installé sur votre ordinateur, la seule sélection disponible est Aucun. Si vous avez installé Microsoft SourceSafe, les plug-ins suivants sont affichés :  
  
    -   Microsoft Visual SourceSafe  
  
    -   Microsoft Visual SourceSafe (Internet)  
  
3.  Définissez les informations d'identification de connexion pour chaque rôle de contrôle de code source que vous souhaitez utiliser. Cette page est disponible uniquement si un plug-in de contrôle de code source est installé.  
  
     **Description du rôle**  
     Lorsque vous choisissez l'un de ces rôles, les options du contrôle de code source correspondantes sont automatiquement sélectionnées.  
  
    |Role|Description|  
    |----------|-----------------|  
    |**Visual SourceSafe**|Spécifie que vous souhaitez utiliser les paramètres les plus couramment utilisés [!INCLUDE[msCoName](../includes/msconame-md.md)] par les utilisateurs de Visual SourceSafe.|  
    |**Développeur indépendant**|Indique que vous travaillez de manière indépendante.|  
    |**Personnalisée**|Indique que vous avez modifié les paramètres d'un rôle.|  
  
     **Effectuer les mises à jour d'état en tâche de fond**  
     Met automatiquement à jour les icônes du signal de contrôle de code source dans l'Explorateur de solutions au fur et à mesure que l'état d'un élément change. Si vous rencontrez des problèmes de retards lors de l'exécution des opérations de serveur, particulièrement lors de l'ouverture d'une solution ou d'un projet à partir du contrôle de code source, le fait de désactiver cette case à cocher peut améliorer les performances.  
  
     **Nom d'accès**  
     Spécifie le nom d'utilisateur à employer pour se connecter au fournisseur de contrôle de code source. S’il est pris en charge par votre fournisseur de contrôle de code source, ce nom est automatiquement renseigné dans la boîte de dialogue de **connexion** pour accéder à votre serveur de contrôle de code source. Pour activer cette option, désactivez les connexions utilisateur automatiques à l'aide du programme d'administrateur de votre fournisseur de contrôle de code source, puis redémarrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
     **Avancé**  
     Affiche d'autres options permettant d'ajouter des éléments au contrôle de code source. Ces options varient en fonction de votre fournisseur de contrôle de code source. Vous pouvez obtenir de l'aide sur ces options dans le programme de contrôle de code source.  
  
4.  Sélectionnez la page **environnement** .  
  
5.  Dans la zone paramètres de l' **environnement du contrôle de code source** , sélectionnez le rôle sur lequel vous souhaitez définir les options de contrôle de code source.  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] sélectionne automatiquement les options par défaut du contrôle de code source correspondant au rôle que vous avez choisi. Si vous désactivez l’une des options par défaut, la zone paramètres de l' **environnement du contrôle de code source** affiche l’option **personnalisé** pour indiquer que vous avez personnalisé le rôle sélectionné à l’origine.  
  
     **Paramètres de l'environnement du contrôle de code source**  
     Spécifie le rôle que vous souhaitez utiliser. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] définit les rôles suivants.  
  
    |Role|Description|  
    |----------|-----------------|  
    |**Visual SourceSafe**|Spécifie que vous souhaitez utiliser les paramètres les plus couramment utilisés [!INCLUDE[msCoName](../includes/msconame-md.md)] par les utilisateurs de Visual SourceSafe.|  
    |**Développeur indépendant**|Indique que vous travaillez de manière indépendante.|  
    |**Personnalisée**|Indique que vous avez modifié les paramètres d'un rôle.|  
  
     Lorsque vous choisissez l'un de ces rôles, les options du contrôle de code source correspondantes sont automatiquement sélectionnées.  
  
     **Conserver les éléments en extraction lors de l'archivage**  
     Spécifie que les éléments doivent rester extraits à votre niveau lorsque vous procédez à l'archivage d'éléments pour mettre à jour le magasin du contrôle de code source. Si vous souhaitez modifier cette option pour un archivage spécifique, cliquez sur la flèche **options** dans la boîte de dialogue **Archiver** , puis désactivez la case à cocher **conserver** l’extraction.  
  
     **Éléments archivés**  
     Affiche une liste d’options qui spécifient [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] comment se comporter quand vous essayez de modifier un élément qui n’est pas extrait. Les tableaux suivants décrivent les options disponibles.  
  
     **Enregistrement**  
  
    |Action|Description|  
    |------------|-----------------|  
    |**Demander l'extraction**|Affiche la boîte de dialogue **extraire** .|  
    |**Extraire automatiquement**|Extrait l’élément sans afficher la boîte de dialogue **extraire** . Il s'agit de l'option par défaut.|  
    |**Enregistrer sous**|Enregistre en tant que nouveau fichier.|  
  
     **Modification**  
  
    |Action|Description|  
    |------------|-----------------|  
    |**Demander l'extraction**|Affiche la boîte de dialogue **extraire** .|  
    |**Demander des extractions exclusives**|Affiche la boîte de dialogue **extraire** .|  
    |**Extraire automatiquement**|Extrait l’élément sans afficher la boîte de dialogue **extraire** . Il s'agit de l'option par défaut.|  
    |**Ne rien faire**|N'extrait pas le fichier.|  
  
     **Permettre la modification des éléments archivés**  
     Spécifie que les éléments archivés peuvent être modifiés en mémoire. Si vous activez cette case à cocher, un bouton **modifier** apparaît dans la boîte de dialogue **extraire** lorsque vous tentez de modifier un élément archivé. Après avoir cliqué sur ce bouton, vous pouvez modifier l'élément. Si vous souhaitez enregistrer l'élément, vous devez l'extraire ou l'enregistrer dans un autre emplacement.  
  
     **Réinitialiser**  
     Rétablit les paramètres par défaut des boîtes de dialogue de confirmation du contrôle de code source. Par exemple, si vous avez activé la case à cocher **ne plus afficher cette boîte de dialogue** dans un contrôle de code source, la sélection de l’option de **réinitialisation** inverse cette action.  
  
## <a name="see-also"></a>Voir aussi  
 [Notions de base sur le contrôle de code source](../../2014/database-engine/source-control-basics.md)   
 [Modifier les connexions du contrôle de code source](../../2014/database-engine/change-source-control-connections.md)   
 [Exclure des fichiers du contrôle de code source](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
