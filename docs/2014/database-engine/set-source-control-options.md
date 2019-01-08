---
title: Définir les Options de contrôle de code Source | Microsoft Docs
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
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53589893"
---
# <a name="set-source-control-options"></a>Définir les options du contrôle de code source
  Pour pouvoir bénéficier des fonctionnalités du contrôle de code source intégrées à [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], vous devez préalablement configurer les options du contrôle de code source relatives aux différents environnements dans lesquels vous travaillez.  
  
 Vous configurez les options de contrôle de code source à l’aide de la **Options** boîte de dialogue pour configurer un ou plusieurs rôles de contrôle de code source. Un rôle comporte une description générale de la configuration dans laquelle vous utilisez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et les options du contrôle de code source associées à cette configuration.  
  
 Par exemple, si vous êtes un développeur indépendant, vous ne créez généralement pas de conflits avec d'autres utilisateurs en conservant des fichiers extraits après les avoir archivés. Par conséquent, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] définit un rôle Développeur indépendant. Pour ce rôle, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] sélectionne automatiquement le **conserver les éléments en extraction lors de l’archivage** option.  
  
 Comme vous pouvez définir et personnaliser des rôles, vous pouvez travailler dans différentes configurations de développement sans avoir à redéfinir intégralement le contrôle de code source chaque fois que vous passez d'une configuration à une autre.  
  
### <a name="to-set-source-control-options"></a>Pour configurer les options du contrôle de code source  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Dans le **Options** boîte de dialogue, développez **contrôle de code Source**, puis cliquez sur le **sélection du plug-in** page.  
  
     **Plug-in de contrôle de code source en cours**  
     Sélectionnez le contrôle de code source que vous souhaitez utiliser dans cette liste. Le client du produit de contrôle de code source doit être installé sur votre ordinateur pour apparaître dans la liste. Si aucun client de contrôle de code source n'est installé sur votre ordinateur, la seule sélection disponible est Aucun. Si vous avez installé Microsoft SourceSafe, les plug-ins suivants sont affichés :  
  
    -   Microsoft Visual SourceSafe  
  
    -   Microsoft Visual SourceSafe (Internet)  
  
3.  Définissez les informations d'identification de connexion pour chaque rôle de contrôle de code source que vous souhaitez utiliser. Cette page est disponible uniquement si un plug-in de contrôle de code source est installé.  
  
     **Description du rôle**  
     Lorsque vous choisissez l'un de ces rôles, les options du contrôle de code source correspondantes sont automatiquement sélectionnées.  
  
    |Role|Description|  
    |----------|-----------------|  
    |**Visual SourceSafe**|Spécifie que vous souhaitez utiliser les paramètres couramment utilisés par [!INCLUDE[msCoName](../includes/msconame-md.md)] utilisateurs Visual SourceSafe.|  
    |**Développeur indépendant**|Indique que vous travaillez de manière indépendante.|  
    |**Personnalisé**|Indique que vous avez modifié les paramètres d'un rôle.|  
  
     **Effectuer des mises à jour du statut d’arrière-plan**  
     Met automatiquement à jour les icônes du signal de contrôle de code source dans l'Explorateur de solutions au fur et à mesure que l'état d'un élément change. Si vous rencontrez des problèmes de retards lors de l'exécution des opérations de serveur, particulièrement lors de l'ouverture d'une solution ou d'un projet à partir du contrôle de code source, le fait de désactiver cette case à cocher peut améliorer les performances.  
  
     **Nom d'accès**  
     Spécifie le nom d'utilisateur à employer pour se connecter au fournisseur de contrôle de code source. Si la prise en charge par votre fournisseur de contrôle de code source, ce nom est renseigné automatiquement dans le **connexion** boîte de dialogue pour atteindre votre serveur de contrôle de code source. Pour activer cette option, désactivez les connexions utilisateur automatiques à l'aide du programme d'administrateur de votre fournisseur de contrôle de code source, puis redémarrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
     **Avancé**  
     Affiche d'autres options permettant d'ajouter des éléments au contrôle de code source. Ces options varient en fonction de votre fournisseur de contrôle de code source. Vous pouvez obtenir de l'aide sur ces options dans le programme de contrôle de code source.  
  
4.  Sélectionnez le **environnement** page.  
  
5.  Dans le **paramètres d’environnement de contrôle de Source** , sélectionnez le rôle sur lequel vous souhaitez définir les options de contrôle de code source.  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] sélectionne automatiquement les options par défaut du contrôle de code source correspondant au rôle que vous avez choisi. Si vous désactivez les options par défaut, le **paramètres d’environnement de contrôle de Source** zone affiche la **personnalisé** option pour indiquer que vous avez personnalisé le rôle sélectionné à l’origine.  
  
     **Paramètres d’environnement de contrôle de code source**  
     Spécifie le rôle que vous souhaitez utiliser. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] définit les rôles suivants.  
  
    |Role|Description|  
    |----------|-----------------|  
    |**Visual SourceSafe**|Spécifie que vous souhaitez utiliser les paramètres couramment utilisés par [!INCLUDE[msCoName](../includes/msconame-md.md)] utilisateurs Visual SourceSafe.|  
    |**Développeur indépendant**|Indique que vous travaillez de manière indépendante.|  
    |**Personnalisé**|Indique que vous avez modifié les paramètres d'un rôle.|  
  
     Lorsque vous choisissez l'un de ces rôles, les options du contrôle de code source correspondantes sont automatiquement sélectionnées.  
  
     **Conserver les éléments en extraction lors de l’archivage**  
     Spécifie que les éléments doivent rester extraits à votre niveau lorsque vous procédez à l'archivage d'éléments pour mettre à jour le magasin du contrôle de code source. Si vous souhaitez modifier cette option pour un archivage spécifique, cliquez sur le **Options** flèche dans le **archiver** boîte de dialogue, puis désactivez la **conserver extraits** case à cocher.  
  
     **Éléments archivés**  
     Affiche une liste d'options qui spécifient comment [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] doit se comporter lorsque vous tentez de modifier un élément non extrait. Les tableaux suivants décrivent les options disponibles.  
  
     **L’enregistrement**  
  
    |Action|Description|  
    |------------|-----------------|  
    |**Invite pour l’extraction**|Affiche le **Check Out** boîte de dialogue.|  
    |**Extraire automatiquement**|Extrait l’élément sans afficher la **Check Out** boîte de dialogue. Il s'agit de l'option par défaut.|  
    |**Enregistrer en tant que**|Enregistre en tant que nouveau fichier.|  
  
     **Modification**  
  
    |Action|Description|  
    |------------|-----------------|  
    |**Invite pour l’extraction**|Affiche le **Check Out** boîte de dialogue.|  
    |**Demander des extractions exclusives**|Affiche le **Check Out** boîte de dialogue.|  
    |**Extraire automatiquement**|Extrait l’élément sans afficher la **Check Out** boîte de dialogue. Il s'agit de l'option par défaut.|  
    |**Ne rien faire**|N'extrait pas le fichier.|  
  
     **Autoriser l’archivage des éléments archivés**  
     Spécifie que les éléments archivés peuvent être modifiés en mémoire. Si vous sélectionnez cette case à cocher, un **modifier** bouton s’affiche dans le **Check Out** boîte de dialogue lorsque vous tentez de modifier un élément archivé. Après avoir cliqué sur ce bouton, vous pouvez modifier l'élément. Si vous souhaitez enregistrer l'élément, vous devez l'extraire ou l'enregistrer dans un autre emplacement.  
  
     **Réinitialiser**  
     Rétablit les paramètres par défaut des boîtes de dialogue de confirmation du contrôle de code source. Par exemple, si vous avez sélectionné le **ne plus afficher cette boîte de dialogue** case à cocher dans une boîte de dialogue de contrôle de code source, en sélectionnant le **réinitialiser** option annule cette action.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de contrôle de code source](../../2014/database-engine/source-control-basics.md)   
 [Modification des connexions de contrôle de code Source](../../2014/database-engine/change-source-control-connections.md)   
 [Exclure des fichiers du contrôle de code source](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
