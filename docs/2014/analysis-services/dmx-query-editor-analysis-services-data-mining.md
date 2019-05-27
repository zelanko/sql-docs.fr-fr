---
title: Éditeur de requête DMX (Analysis Services - Exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.startpage.dmx.f1
ms.assetid: 7ac877a1-0f29-46b9-9a51-73b02172bef1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3be28b0a402743e4d9c26b346386202127c5f74d
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66081568"
---
# <a name="dmx-query-editor-analysis-services---data-mining"></a>Éditeur de requête DMX (Analysis Services – Exploration de données)
  Utilisez l'Éditeur de requête DMX pour créer et exécuter des instructions écrites en langage DMX (Data Mining Extensions).  
  
## <a name="features"></a>Fonctionnalités  
  
-   Tapez les scripts dans le volet de l'Éditeur de requête DMX.  
  
-   Pour exécuter les scripts, appuyez sur **F5**ou cliquez sur **Exécuter** dans la barre d'outils ou dans le menu **Requête** . Si une partie du code est sélectionnée, seule cette partie du code est exécutée. Si aucun code n'est sélectionné, l'ensemble du contenu de l'Éditeur de requête DMX est exécuté.  
  
-   Affichez les métadonnées des cubes et des autres objets contenus dans une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans le volet des métadonnées.  
  
-   Pour obtenir des informations d'aide sur la syntaxe, sélectionnez un mot clé dans l'Éditeur de requête DMX, puis cliquez sur **F1**.  
  
-   Pour obtenir une aide dynamique sur la syntaxe DMX, dans le menu **Aide** , cliquez sur **Aide dynamique** pour ouvrir le composant Aide dynamique. Avec l'Aide dynamique, les rubriques d'aide apparaissent dans la fenêtre **Aide dynamique** lorsque vous tapez des mots clés dans l'Éditeur de requête.  
  
## <a name="sql-server-analysis-services-editors-toolbar"></a>Barre d'outils Éditeurs SQL Server Analysis Services  
 Lorsque l'Éditeur de requête DMX est ouvert, la barre d'outils **Éditeurs SQL Server Analysis Services** apparaît avec les boutons répertoriés dans le tableau ci-dessous.  
  
|Terme|Définition|  
|----------|----------------|  
|**Se connecter**|Ouvre la boîte de dialogue **Se connecter au serveur** pour établir une connexion à une instance Analysis Services.|  
|**Déconnecter**|Déconnecte l'Éditeur de requête DMX d'une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Modifier la connexion**|Ouvre la boîte de dialogue **Se connecter au serveur** pour établir une connexion à une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] différente.|  
|**Nouvelle requête avec la connexion actuelle**|Ouvre la fenêtre Éditeur de requête DMX en utilisant les informations de connexion de la fenêtre Éditeur de requête DMX actuelle.|  
|**Bases de données disponibles**|Se connecte à une base de données différente [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sur la même instance.|  
|**Exécuter**|Exécute le code sélectionné, ou si aucun code n'est sélectionné, cette option exécute l'ensemble du code dans l'Éditeur de requête DMX.|  
|**Analyser**|Contrôle la syntaxe du code sélectionné. Si aucun code n'est sélectionné, cette option vérifie la syntaxe de l'ensemble de la fenêtre de l'Éditeur de requête DMX.|  
|**Annuler l'exécution de la requête**|Envoie une demande d'annulation au serveur. Certaines requêtes ne peuvent pas être annulées immédiatement et doivent attendre une condition d'annulation favorable. Une fois la requête annulée, un certains délai peut exister au cours de l'annulation des transactions.|  
  
## <a name="dmx-query-editor-window"></a>Fenêtre Éditeur de requête DMX  
 Les options répertoriées dans le tableau ci-dessous sont disponibles dans l'Éditeur de requête DMX.  
  
|Terme|Définition|  
|----------|----------------|  
|**Fenêtre Éditeur de requête**|Tapez les instructions DMX et les scripts que doit exécuter l'Éditeur de requête DMX.<br /><br /> Le menu contextuel de l'éditeur de requête contient les options suivantes :<br /><br /> **Couper**: Copie la sélection actuelle vers le Presse-papiers et supprime la sélection de la fenêtre de l'éditeur de requête.<br /><br /> **Copier**: Copie la sélection actuelle vers le Presse-papiers.<br /><br /> **Coller**: Colle le contenu du Presse-papiers vers la sélection actuelle.<br /><br /> **Connecter**: Ouvre la boîte de dialogue **Se connecter au serveur** pour établir une connexion à une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .<br /><br /> **Déconnecter**: Déconnecte l'éditeur de requête actuel d'une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .<br /><br /> **Déconnecter toutes les requêtes**: Déconnecte tous les éditeurs de requête ouverts.<br /><br /> **Modifier la connexion**: Ouvre la boîte de dialogue **Se connecter au serveur** pour établir une connexion à une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] différente.<br /><br /> **Ouvrir le serveur dans l’Explorateur d’objets**: Ouvre la boîte de dialogue [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à laquelle l’éditeur de requête actuel est connecté dans l’ **Explorateur d’objets**.<br /><br /> **Exécuter**: Exécute le code sélectionné. Si aucun code n'est sélectionné, cette option exécute le code entier dans l'éditeur de requête actuel.<br /><br /> **Fenêtre Propriétés**: Affiche la fenêtre **Propriétés** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour la fenêtre de requête active.<br /><br /> **Options de requête**: Affiche la boîte de dialogue **Options de requête** .|  
|**Fenêtre des métadonnées**|Affiche les métadonnées de la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] connectée.|  
|**Cube**|Sélectionnez un cube dans la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] connectée pour afficher les métadonnées associées au cube dans l'onglet **Métadonnées** .|  
|**Métadonnées**|Affiche les métadonnées du cube sélectionné dans **Cube**, notamment les groupes de mesures et les mesures, les indicateurs de performances clés, les dimensions, les hiérarchies, les niveaux, les membres et les propriétés des membres. Pour extraire la clé qualifiée complète d'un objet, procédez de l'une des manières suivantes :<br /><br /> Faites glisser l'objet de l'onglet **Métadonnées** vers le volet de requête.<br /><br /> - ou -<br /><br /> Cliquez avec le bouton droit sur l’objet et sélectionnez **Copier**, puis cliquez avec le bouton droit sur le volet de requête et sélectionnez **Coller**.|  
|**Fonctions**|Affiche les métadonnées des fonctions DMX accessibles à la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , telles qu’elles sont extraites de l’ensemble de lignes de schéma DMSCHEMA_MINING_FUNCTIONS.<br /><br /> Pour extraire la syntaxe d'une fonction, procédez de l'une des manières suivantes :<br /><br /> Faites glisser l'objet de l'onglet **Fonctions** vers le volet de requête.<br /><br /> - ou -<br /><br /> Cliquez avec le bouton droit sur la fonction et sélectionnez **Copier**, puis cliquez avec le bouton droit sur le volet de requête et sélectionnez **Coller**.|  
|**Fenêtre des résultats**|Affiche les résultats d'une instruction DMX dans une grille.|  
|**Fenêtre de messages**|Contient des informations sur l'exécution d'une instruction DMX. Cette fenêtre, par exemple, contient les erreurs détectées lors de l'exécution ou le nombre de cellules extraites après l'exécution.|  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteurs et boîtes de dialogue Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Référence DMX &#40;Data Mining Extensions&#41;](/sql/dmx/data-mining-extensions-dmx-reference)   
 [Éditeur de requête MDX &#40;Analysis Services - données multidimensionnelles&#41;](mdx-query-editor-analysis-services-multidimensional-data.md)   
 [Éditeur de requête XMLA &#40;Analysis Services - données multidimensionnelles&#41;](xmla-query-editor-analysis-services-multidimensional-data.md)   
 [Les éditeurs de texte et de requête &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)   
 [Raccourcis clavier SQL Server Management Studio](../ssms/sql-server-management-studio-keyboard-shortcuts.md)   
 [Personnaliser des Menus et des touches de raccourci](../ssms/customize-menus-and-shortcut-keys.md)   
 [Codage en couleurs dans les éditeurs de requête](../relational-databases/scripting/color-coding-in-query-editors.md)  
  
  
