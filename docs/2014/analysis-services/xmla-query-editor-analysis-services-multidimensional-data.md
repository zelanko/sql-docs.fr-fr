---
title: Éditeur de requête XMLA (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.editor.xmla.f1
helpviewer_keywords:
- XMLA Query Editor
- Query Editor [XMLA]
ms.assetid: 14623019-7839-4038-9d12-2f8953d2ec04
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1939ea9e1de7b0b7858ad09ad26bc3b4fbf008c3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66065311"
---
# <a name="xmla-query-editor-analysis-services---multidimensional-data"></a>Éditeur de requête XMLA (Analysis Services - Données multidimensionnelles)
  Utilisez l'Éditeur de requête XMLA pour créer et exécuter des instructions et des scripts écrits en langage XMLA.  
  
## <a name="features"></a>Fonctionnalités  
  
-   Tapez les scripts dans le volet d'éditeur de requête de l'Éditeur de requête XMLA.  
  
-   Pour exécuter les scripts, appuyez sur **F5**, ou cliquez sur **Exécuter** dans la barre d'outils ou dans le menu **Requête** , cliquez sur **Exécuter**. Si une partie du code est sélectionnée, seule cette partie du code est exécutée. En revanche, si aucun code n'est sélectionné, le contenu entier de l'Éditeur de requête XMLA est exécuté.  
  
-   Affichage des métadonnées des cubes et des autres objets contenus dans une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans le volet des métadonnées.  
  
-   Pour obtenir de l'aide sur la syntaxe XMLA, sélectionnez un mot clé dans l'Éditeur de requête XMLA, puis cliquez sur **F1**.  
  
-   Pour obtenir une aide dynamique sur la syntaxe XMLA, dans le menu **?** (Aide), cliquez sur **Aide dynamique** pour ouvrir le composant correspondant. Avec l'Aide dynamique, les rubriques d'aide apparaissent dans la fenêtre **Aide dynamique** lorsque vous tapez des mots clés dans l'Éditeur de requête.  
  
## <a name="sql-server-analysis-services-editors-toolbar"></a>Barre d'outils Éditeurs SQL Server Analysis Services  
 Lorsque l'Éditeur de requête XMLA est ouvert, la barre d'outils **Éditeurs SQL Server Analysis Services** s'affiche avec les boutons ci-après.  
  
|Terme|Définition|  
|----------|----------------|  
|**Connexion**|Ouvre la boîte de dialogue **Se connecter au serveur** pour établir une connexion à une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Connect**|Déconnecte l'Éditeur de requête XMLA d'une instance d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Modifier la connexion**|Ouvre la boîte de dialogue **Se connecter au serveur** pour établir une connexion à une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] différente.|  
|**Nouvelle requête avec la connexion actuelle**|Ouvre une nouvelle fenêtre d'Éditeur de requête XMLA, avec les informations de connexion issues de la fenêtre active.|  
|**Bases de données disponibles**|Se connecte à une base de données différente [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sur la même instance.|  
|**Effectue**|Exécute le code sélectionné. Si aucun code n'est sélectionné, cette option exécute le code entier dans l'Éditeur de requête XMLA.|  
|**Analyser**|Contrôle la syntaxe du code sélectionné. Si aucun code n'est sélectionné, cette option vérifie la syntaxe de toute la fenêtre de l'Éditeur de requête XMLA.|  
|**Annuler l’exécution de la requête**|Envoie une demande d'annulation au serveur. Certaines requêtes ne peuvent pas être annulées immédiatement et doivent attendre une condition d'annulation appropriée. Une fois les requêtes annulées, un certain délai peut exister au cours de l'annulation des transactions.|  
  
## <a name="xmla-query-editor-window"></a>Fenêtre Éditeur de requête XMLA  
 Les options suivantes sont disponibles dans l'Éditeur de requête XMLA :  
  
|Terme|Définition|  
|----------|----------------|  
|**Fenêtre d'éditeur de requête**|Tapez les instructions et les scripts XMLA à exécuter par l'Éditeur de requête XMLA.<br /><br /> Le menu contextuel de l'éditeur de requête contient les options suivantes :<br /><br /> **Couper**: copie la sélection actuelle dans le presse-papiers et supprime la sélection de la fenêtre de l’éditeur de requête.<br />**Copier**: copie la sélection actuelle dans le presse-papiers.<br />**Coller**: colle le contenu du presse-papiers dans la sélection actuelle.<br />**Se connecter**: ouvre la boîte de dialogue **se connecter au serveur** pour établir une connexion [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à une instance.<br />**Déconnecter**: déconnecte l’éditeur de requête actuel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] d’une instance.<br />Déconnecter **toutes les requêtes**: déconnecte tous les éditeurs de requête ouverts.<br />**Modifier la connexion**: ouvre la boîte de dialogue **se connecter au serveur** pour établir une connexion à [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] une autre instance.<br />**Ouvrir le serveur dans l’Explorateur d’objets**: ouvre l' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance à laquelle l’éditeur de requête actuel est connecté dans l' **Explorateur d’objets**.<br />**Execute**: exécute le code sélectionné, ou si aucun code n’est sélectionné, exécute l’ensemble du code dans l’éditeur de requête actuel.<br />**Fenêtre Propriétés**: affiche la fenêtre **Propriétés** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour la fenêtre de requête actuelle.<br />**Options de requête**: affiche la boîte de dialogue **options de requête** .|  
|**Fenêtre de résultats**|Affiche les résultats d'une instruction ou d'un script XMLA sous forme de texte.|  
|**Fenêtre des messages**|Affiche des informations sur l'exécution d'une instruction ou d'un script XMLA. Cette fenêtre, par exemple, contient les erreurs détectées lors de l'exécution ou le nombre de cellules extraites après l'exécution.|  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de requête MDX &#40;Analysis Services-données multidimensionnelles&#41;](mdx-query-editor-analysis-services-multidimensional-data.md)   
 [Éditeur de requête DMX &#40;Analysis Services d’exploration de données&#41;](dmx-query-editor-analysis-services-data-mining.md)   
 [Éditeurs de texte et de requête &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)   
 [Raccourcis clavier dans SQL Server Management Studio](../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
  
  
