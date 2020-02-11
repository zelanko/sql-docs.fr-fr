---
title: 'Options (éditeur de texte : onglet Éditeur et page barre d’État) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.editorcontextsettings
- VS.ToolsOptionsPages.Text_Editor.EditorTabAndStatusBar
ms.assetid: e4815678-7885-4631-878f-c6a2b857ee05
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 01098f2181085f17788429608afb7bdda15fb504
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66089243"
---
# <a name="options-text-editor-editor-tab-and-status-bar-page"></a>Options (Éditeur de texte/onglet Éditeur et page Barre d’état)
  L' **onglet Éditeur et la page Barre d'état** vous permettent de personnaliser les informations affichées par les éditeurs de requête [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] . Vous pouvez spécifier le niveau d'informations affiché dans l'onglet et la barre d'état de la fenêtre Éditeur de requête, et indiquer si la barre d'état doit apparaître en haut ou en bas de la fenêtre de l'éditeur.  
  
## <a name="option-settings-by-editor"></a>Paramètres d'option par éditeur  
 L'onglet d'éditeur et la barre d'état sont disponibles dans tous les éditeurs [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , mais ils présentent différents niveaux de fonctionnalité.  
  
 L'Éditeur de requête du moteur de base de données peut se connecter à un groupe de serveurs, auquel cas il ouvre des connexions à toutes les instances dans le groupe de serveurs et peut exécuter simultanément la même requête sur chaque connexion. Vous pouvez utiliser ce dialogue pour spécifier que la barre d'état offre des couleurs différentes en cas de connexion à plusieurs instances plutôt qu'à une seule. Pour modifier les options de résultats multi-serveur, utilisez la page [Options (Résultats de la requête/SQL Server/Multi-serveur)](../../2014/database-engine/options-query-results-sql-server-multi-server.md) .  
  
## <a name="status-bar-content"></a>Contenu de la barre d'état  
 Indique les informations qui apparaissent dans la barre d'état de l'éditeur de requête.  
  
 **Afficher la durée d'exécution**  
 Inclut l'heure d'exécution du script. Les paramètres sont les suivants :  
  
 **Aucun**  
 La barre d'état n'affiche pas d'informations horaires.  
  
 **Fin**  
 La barre d'état affiche l'heure réelle du jour pendant l'exécution du script. À l'achèvement du script, l'affichage indique l'heure du jour à laquelle le script s'est terminé.  
  
 **Temps écoulé**  
 La barre d'état affiche la durée d'exécution du script. Lorsque le script s'achève, l'affichage indique la durée nécessaire pour exécuter le script.  
  
 **Inclure le nom de la base de données**  
 Inclut le nom de la base de données actuelle pour la connexion. Lorsque l'éditeur de requête s'affiche pour la première fois, il s'agit de la base de données par défaut pour le compte de connexion. Le contexte de base de données peut être modifié ultérieurement en utilisant l'instruction USE Transact-SQL.  
  
 **Inclut le nom de la connexion**  
 Inclut le nom de la connexion.  
  
 **Inclure le nombre de lignes**  
 Inclut un nombre de lignes qui ont été traitées par le script en cours d'exécution.  
  
 **Inclure le nom du serveur**  
 Inclut le nom du serveur. Pour les connexions locales, il s'agit du nom de l'instance. Pour les connexions distantes, il s'agit du nom de l'ordinateur distant et du nom de l'instance.  
  
## <a name="status-bar-layout-and-colors"></a>Couleurs et disposition de la barre d'état  
 Spécifie les couleurs des éléments de la barre d'état de l'éditeur de requête.  
  
 **Grouper les connexions**  
 Définit la couleur de la barre d'état lorsque l'éditeur de requête a plusieurs connexions.  
  
 **Connexions à un seul serveur**  
 Définit la couleur de la barre d'état lorsque l'éditeur de requête a une seule connexion.  
  
 **Emplacement de la barre d'état**  
 Spécifie l'emplacement de la barre d'état. Les paramètres sont les suivants :  
  
 **Retour au début**  
 La barre d'état apparaît en haut de la fenêtre de l'éditeur de requête.  
  
 **Bas**  
 La barre d'état apparaît au bas de la fenêtre de l'éditeur de requête.  
  
## <a name="tab-text"></a>Texte de l'onglet  
 Spécifie le texte qui apparaît dans l'onglet situé dans la partie supérieure d'une fenêtre de l'éditeur de requête. Si le texte est trop long à afficher, vous pouvez consulter la chaîne complète dans l'info-bulle qui s'affiche lorsque vous pointez sur l'onglet.  
  
 **Inclure le nom de la base de données**  
 Inclut le nom de la base de données actuelle pour la connexion. Lorsque l'éditeur de requête s'affiche pour la première fois, il s'agit de la base de données par défaut pour le compte de connexion. Le contexte de base de données peut être modifié ultérieurement en utilisant l'instruction USE Transact-SQL.  
  
 **Inclure le nom du fichier**  
 Inclut le nom du fichier où est stocké le script.  
  
 **Inclure le dossier**  
 Inclut le chemin d'accès du dossier où est stocké le fichier script.  
  
 **Inclut le nom de la connexion**  
 Inclut le nom de la connexion.  
  
 **Inclure le nom du serveur**  
 Inclut le nom du serveur. Pour les connexions locales, il s'agit du nom de l'instance. Pour les connexions distantes, il s'agit du nom de l'ordinateur distant et du nom de l'instance.  
  
## <a name="see-also"></a>Voir aussi  
 [Options &#40;environnement : pages de polices et de couleurs&#41;](../ssms/menu-help/options-environment-fonts-and-colors-page.md)   
 [Codage en couleurs dans les éditeurs de requête](../relational-databases/scripting/color-coding-in-query-editors.md)  
  
  
