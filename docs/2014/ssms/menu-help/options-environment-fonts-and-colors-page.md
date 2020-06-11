---
title: 'Options (environnement : page polices et couleurs) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ea3aa222-538d-485f-99dc-01eb02cdcfea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 21c4f3a480b039b4853c112831341b6448a7d6a7
ms.sourcegitcommit: 18a7c77be31f9af92ad9d0d3ac5eecebe8eec959
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83859379"
---
# <a name="options-environment-fonts-and-colors-page"></a>Options (Environnement : page Polices et couleurs)
  La boîte de dialogue **Options** vous permet de définir un modèle personnalisé de polices et de couleurs pour différents éléments de l’interface utilisateur dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Dans le menu **Outils** , cliquez sur **Options** , développez le dossier **Environnement** et sélectionnez **Polices et couleurs**.  
  
 Les modifications apportées à un modèle de couleurs ne sont pas prises en compte lors de la session au cours de laquelle vous avez effectué ces changements. Vous pouvez évaluer les changements de couleurs en ouvrant une autre instance de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et en reproduisant les conditions dans lesquelles vous souhaitez appliquer ces modifications.  
  
## <a name="ui-element-list"></a>Liste des éléments d’interface utilisateur  
 **Afficher les paramètres de**  
 Répertorie tous les éléments de l'interface utilisateur dont vous pouvez modifier les modèles de polices et de couleurs. Après avoir sélectionné un élément dans cette liste, vous pouvez personnaliser les paramètres de couleurs de l’élément sélectionné dans **Éléments affichés**.  
  
|Terme|Définition|  
|----------|----------------|  
|Éditeur de texte|Les modifications apportées aux paramètres d'affichage du style, de la taille et de la couleur des polices dans l'éditeur de texte influencent la présentation du texte dans l'éditeur de texte par défaut. Les documents ouverts dans un éditeur de texte en dehors de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ne sont pas affectés par ces paramètres.|  
|Imprimante|Les modifications apportées aux paramètres d'affichage du style, de la taille et de la couleur des polices de l'imprimante influencent la présentation du texte sur les documents imprimés.<br /><br /> Conseil : si nécessaire, vous pouvez sélectionner une autre police par défaut pour l’impression que celle utilisée pour l’affichage dans l’éditeur de texte. Cela peut être utile lors de l'impression de code contenant des caractères codés sur un octet et sur deux octets.|  
|[Toutes les fenêtres Outil de texte **]**|Les modifications apportées aux paramètres d'affichage du style, de la taille et de la couleur des polices pour cet élément influencent la présentation du texte dans les fenêtres Outils disposant de volets de sortie dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], par exemple les fenêtres Sortie, Résultats de texte, et ainsi de suite.<br /><br /> Remarque : Les modifications apportées au texte des éléments [Toutes les fenêtres Outil de texte] ne sont pas prises en compte lors de la session au cours de laquelle vous avez effectué les changements. Vous pouvez évaluer le résultat obtenu du fait des modifications apportées en ouvrant une autre instance de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
|Fenêtre Résultats de la recherche|Les modifications apportées aux paramètres d’affichage du style, de la taille et de la couleur des polices pour cet élément influencent la présentation du texte dans la fenêtre Résultats de la recherche.|  
|Fenêtre Sortie|Les modifications apportées aux paramètres d'affichage du style, de la taille et de la couleur des polices pour cet élément influencent la présentation du texte dans les fenêtres Sortie.|  
|Résultats de grille|Les modifications apportées aux paramètres d’affichage du style, de la taille et de la couleur des polices pour cet élément influencent la présentation du texte dans les fenêtres **Résultats de grille** .|  
|Plan d'exécution|Les modifications apportées aux paramètres d’affichage du style, de la taille et de la couleur des polices pour cet élément influencent la présentation du texte dans le plan d’exécution de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et dans les requêtes [!INCLUDE[ssEW](../../includes/ssew-md.md)].|  
|Résultats de texte|Les modifications apportées aux paramètres d’affichage du style, de la taille et de la couleur des polices pour cet élément influencent la présentation du texte dans la zone **Résultats de texte** des fenêtres Requête.|  
|Concepteurs Business Intelligence|Les modifications apportées aux paramètres d’affichage du style, de la taille et de la couleur des polices pour cet élément influencent la présentation du texte dans la fenêtre Concepteurs Business Intelligence.|  
  
 **Par défaut**  
 Le bouton **Par défaut** réinitialise les valeurs par défaut des paramètres de police et de couleur de l’élément sélectionné dans la liste **Afficher les paramètres de** .  
  
 **Police (les polices à largeur fixe sont en gras)**  
 Répertorie toutes les polices installées sur votre ordinateur. Quand la liste déroulante s’ouvre, c’est la police actuelle de l’élément choisi dans la liste **Afficher les paramètres de** qui est sélectionnée. Les polices fixes, qui sont plus faciles à aligner dans un éditeur, apparaissent en gras.  
  
 **Taille**  
 Répertorie les tailles en points disponibles pour la police sélectionnée. La modification de la taille de la police affecte toutes les entrées **Éléments affichés** de la sélection **Afficher les paramètres de** .  
  
 **Éléments affichés**  
 Répertorie les éléments dont vous pouvez modifier la couleur de premier plan et d'arrière-plan.  
  
> [!NOTE]  
>  L'élément affiché par défaut est Texte. Les propriétés assignées au texte seront de ce fait remplacées par les propriétés assignées aux autres éléments affichés. Par exemple, si vous assignez la couleur bleue au **texte** et la couleur verte à l’identificateur, tous les identificateurs apparaîtront alors en vert. Dans cet exemple, les propriétés de l'Identificateur se substituent à celles du Texte.  
  
 Voici quelques-uns des éléments affichés.  
  
-   Marge des indicateurs : marge à gauche de l'éditeur de code où sont affichés les points d'arrêt et les icônes de signet.  
  
-   Réduction du texte : bloc de texte ou de code que vous pouvez faire apparaître ou masquer dans l’éditeur de code (XML uniquement).  
  
 **Premier plan**  
 Répertorie les couleurs disponibles pour le premier plan de l’élément sélectionné dans **Éléments affichés**. Dans la mesure où certains éléments sont liés entre eux, veillez à conserver un modèle d'affichage cohérent. Par exemple, si vous changez la couleur de premier plan du texte, la couleur de premier plan des éléments tels que Chaîne est également modifiée.  
  
 **Personnalisée**  
 Affiche la boîte de dialogue **Couleurs** , où vous pouvez définir une couleur personnalisée pour l’élément sélectionné dans la liste **Éléments affichés** .  
  
> [!NOTE]  
>  Il se peut que les paramètres de couleur de l'affichage de votre ordinateur limitent vos possibilités en matière de définition de couleurs personnalisées. Par exemple, si votre ordinateur est configuré avec un affichage en 256 couleurs et que vous sélectionnez une couleur personnalisée dans la boîte de dialogue **Couleurs** , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] applique la valeur la plus proche disponible dans **Couleur de base** comme valeur par défaut et affiche le noir dans la boîte de dialogue **Couleurs** .  
  
 **Arrière-plan de l’élément**  
 Propose une palette de couleurs disponibles pour l’arrière-plan de l’élément sélectionné dans **Éléments affichés**. Dans la mesure où certains éléments sont liés entre eux, veillez à conserver un modèle d'affichage cohérent. Par exemple, si vous changez la couleur d'arrière-plan du texte, la couleur d'arrière-plan des éléments tels que Chaîne SQL est également modifiée.  
  
 **Personnalisée**  
 Affiche la boîte de dialogue **Couleurs** , où vous pouvez définir une couleur personnalisée pour l’élément sélectionné dans la liste **Éléments affichés** .  
  
 **Gras**  
 Cochez cette case pour afficher le texte des éléments affichés sélectionnés en gras. Le texte en gras est plus facilement repérable dans un éditeur.  
  
 **Exemple**  
 Affiche un aperçu du modèle de style, de taille et de couleur des polices correspondant aux valeurs sélectionnées dans **Afficher les paramètres de** et **Éléments affichés**. Vous pouvez utiliser cette zone pour afficher un aperçu des résultats obtenus lorsque vous essayez différentes options de mise en forme.  
  
## <a name="see-also"></a>Voir aussi  
 [Codage en couleurs dans les éditeurs de requête](../../relational-databases/scripting/color-coding-in-query-editors.md)   
 [Options &#40;éditeur de texte : onglet Éditeur et page barre d’état&#41;](../../database-engine/options-text-editor-editor-tab-and-status-bar-page.md)  
  
  
