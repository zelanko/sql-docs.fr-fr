---
title: Éditeur de requête MDX (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.startpage.mdx.f1
helpviewer_keywords:
- Query Editor [MDX]
- MDX Query Editor
ms.assetid: 777f2c23-1c1c-4b72-9d19-48a4866551f8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 579af162998ffaa7c9483a6e6d29a87f98e96fac
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66077877"
---
# <a name="mdx-query-editor-analysis-services---multidimensional-data"></a>Éditeur de requête MDX (Analysis Services - Données multidimensionnelles)
  Utilisez l'Éditeur de requête MDX pour créer et exécuter des instructions et des scripts écrits en langage MDX.  
  
## <a name="features"></a>Fonctionnalités  
  
-   Tapez les scripts dans le volet de l'Éditeur de requête MDX.  
  
-   Pour exécuter les scripts, appuyez sur **F5**, ou cliquez sur **Exécuter** dans la barre d'outils ou dans le menu **Requête** , cliquez sur **Exécuter**. Si une partie du code est sélectionnée, seule cette partie du code est exécutée. Si aucun code n'est sélectionné, l'ensemble du contenu de l'Éditeur de requête MDX est exécuté.  
  
-   Affichage des métadonnées des cubes et des autres objets contenus dans une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans le volet des métadonnées.  
  
-   Pour obtenir des informations d'aide sur la syntaxe MDX, sélectionnez un mot clé dans l'Éditeur de requête MDX, puis cliquez sur **F1**.  
  
-   Pour obtenir une aide dynamique sur la syntaxe MDX, dans le menu **Aide** , cliquez sur **Aide dynamique**pour ouvrir le composant Aide dynamique. Avec l'Aide dynamique, les rubriques d'aide apparaissent dans la fenêtre **Aide dynamique** lorsque vous tapez des mots clés dans l'Éditeur de requête.  
  
## <a name="sql-server-analysis-services-editors-toolbar"></a>Barre d'outils Éditeurs SQL Server Analysis Services  
 Lorsque l'Éditeur de requête MDX est ouvert, la barre d'outils Éditeurs [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] apparaît avec les boutons répertoriés dans le tableau ci-dessous.  
  
|Terme|Définition|  
|----------|----------------|  
|**Connexion**|Ouvre la boîte de dialogue **Se connecter au serveur** pour établir une connexion à une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Connect**|Déconnecte l'Éditeur de requête MDX d'une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Modifier la connexion**|Ouvre la boîte de dialogue **Se connecter au serveur** pour établir une connexion à une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] différente.|  
|**Nouvelle requête avec la connexion actuelle**|Ouvre une nouvelle fenêtre Éditeur de requête MDX en utilisant les informations de connexion de la fenêtre Éditeur de requête MDX actuelle.|  
|**Bases de données disponibles**|Se connecte à une base de données différente [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sur la même instance.|  
|**Effectue**|Exécute le code sélectionné, ou si aucun code n'est sélectionné, exécute l'ensemble du code dans l'Éditeur de requête MDX.|  
|**Analys**|Contrôle la syntaxe du code sélectionné. Si aucun code n'est sélectionné, cette option vérifie la syntaxe de l'ensemble de la fenêtre de l'Éditeur de requête MDX.|  
|**Annuler l'exécution de la requête**|Envoie une demande d'annulation au serveur. Certaines requêtes ne peuvent pas être annulées immédiatement et doivent attendre une condition d'annulation appropriée. Une fois les requêtes annulées, un certain délai peut exister au cours de l'annulation des transactions.|  
  
## <a name="mdx-query-editor-window"></a>Fenêtre Éditeur de requête MDX  
 Les options répertoriées dans le tableau ci-dessous sont disponibles dans l'Éditeur de requête MDX.  
  
|Terme|Définition|  
|----------|----------------|  
|**Fenêtre d'éditeur de requête**|Tapez les instructions MDX et les scripts que doit exécuter l'Éditeur de requête MDX.<br /><br /> Le menu contextuel de l'éditeur de requête contient les options suivantes :<br /><br /> **Couper**: copie la sélection actuelle dans le presse-papiers et supprime la sélection de la fenêtre de l’éditeur de requête.<br /><br /> **Copier**: Copie la sélection actuelle dans le Presse-papiers.<br /><br /> **Coller**: colle le contenu du presse-papiers dans la sélection actuelle.<br /><br /> **Se connecter**: ouvre la boîte de dialogue **Se connecter au serveur** pour établir une connexion à une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .<br /><br /> **Déconnecter**: déconnecte l’éditeur de requête actuel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] d’une instance.<br /><br /> Déconnecter **toutes les requêtes**: déconnecte tous les éditeurs de requêtes actuellement ouverts.<br /><br /> **Modifier la connexion**: ouvre la boîte de dialogue **se connecter au serveur** pour établir une connexion à [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] une autre instance.<br /><br /> **Ouvrir le serveur dans l’Explorateur d’objets**: ouvre l' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance à laquelle l’éditeur de requête actuel est connecté dans l' **Explorateur d’objets**.<br /><br /> **Exécuter**: exécuter le code sélectionné, ou si aucun code n’est sélectionné, exécute l’ensemble du code dans l’éditeur de requête actuel.<br /><br /> **Fenêtre Propriétés**: affiche la fenêtre **Propriétés** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour la fenêtre de requête actuelle.<br /><br /> **Options de requête**: affiche la boîte de dialogue **options de requête** .|  
|**Fenêtre des métadonnées**|Affiche les métadonnées de la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] connectée.|  
|**Dernier**|Sélectionnez un cube dans la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] connectée pour afficher les métadonnées associées au cube dans l'onglet **Métadonnées** .|  
|**Métadonnées**|Affiche les métadonnées du cube sélectionné dans **Cube**, notamment les groupes de mesures et les mesures, les indicateurs de performances clés, les dimensions, les hiérarchies, les niveaux, les membres et les propriétés des membres. Pour extraire la clé qualifiée complète d'un objet, procédez de l'une des manières suivantes :<br /><br /> Faites glisser l'objet de l'onglet **Métadonnées** vers le volet de requête.<br /><br /> Cliquez avec le bouton droit sur l’objet et sélectionnez **Copier**, puis cliquez avec le bouton droit sur le volet de requête et sélectionnez **Coller**.|  
|**Fonctions**|Affiche les métadonnées des fonctions MDX accessibles à la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , telles qu’elles sont extraites de l’ensemble de lignes de schéma MDSCHEMA_FUNCTIONS. Pour extraire la syntaxe d'une fonction, procédez de l'une des manières suivantes :<br /><br /> Faites glisser l'objet de l'onglet **Fonctions** vers le volet de requête.<br /><br /> Cliquez avec le bouton droit sur la fonction et sélectionnez **Copier**, puis cliquez avec le bouton droit sur le volet de requête et sélectionnez **Coller**.|  
|**Fenêtre de résultats**|Affiche le résultat d'une instruction ou d'un script MDX dans une grille.|  
|**Fenêtre des messages**|Contient des informations sur l'exécution d'une instruction ou d'un script MDX. Cette fenêtre, par exemple, contient les erreurs détectées lors de l'exécution ou le nombre de cellules extraites après l'exécution.|  
  
  
