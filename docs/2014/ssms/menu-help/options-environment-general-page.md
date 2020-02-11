---
title: Options (environnement-page général) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.SQLEnvironmentOptions
ms.assetid: c32ccdb8-2cf8-4c78-b474-a3abd3dbbd13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9a96b77c3f1243bc3d95cf38242463724348134b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68188504"
---
# <a name="options-environment-general-page"></a>Options (Environnement - Page Général)
  Utilisez la boîte de dialogue **options** pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] configurer les actions de démarrage, les options de gestion des fenêtres générales et d’autres paramètres généraux. Dans le menu **Outils** , cliquez sur **Options**, développez le dossier **Environnement** , puis cliquez sur **Général**.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Au démarrage**  
 Sélectionnez l'action que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] doit exécuter au démarrage. Les options sont :  
  
-   **Ouvrir l’Explorateur d’objets** invite à entrer une connexion, puis ouvre l’Explorateur d’objets.  
  
-   **Ouvrir une nouvelle fenêtre de requête** vous invite à entrer une connexion, puis ouvre l’éditeur de requête SQL.  
  
-   **Ouvrez l’Explorateur d’objets et les nouvelles** invites de requête pour une connexion, puis ouvrez l’Explorateur d’objets et l’éditeur de requête SQL avec cette connexion.  
  
-   **Ouvrir l’environnement vide** s’ouvre [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] sans fenêtre Éditeur de requête SQL et sans connecter l’Explorateur d’objets à un serveur.  
  
 **Masquer les objets système dans l’Explorateur d’objets**  
 Cocher cette case pour enlever les bases de données système, les tables système, les vues système et les procédures stockées système de l'arborescence de l'Explorateur d'objets. Les fonctions système et les types de données système ne sont pas masqués. Cette option s'applique uniquement aux instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et n'affecte pas les serveurs déjà connectés à l'Explorateur d'objets.  
  
## <a name="environment-layout"></a>Disposition d'environnement  
 Vous devez fermer, puis rouvrir [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour passer du mode d'environnement documents avec onglet au mode d'environnement MDI.  
  
 **Documents avec onglet**  
 Activez cette option pour afficher des fenêtres de documents reliées sous la forme d'onglets dans les éditeurs. Les fenêtres de documents présentées sous la forme d'onglets s'avèrent utiles pour agencer plusieurs documents ouverts et pour passer d'un document à un autre.  
  
 **Environnement MDI**  
 Activez cette option pour ouvrir les documents dans un environnement MDI. Les fenêtres de documents MDI s'avèrent utiles pour gagner de l'espace à l'écran (cet espace serait occupé par des onglets dans un environnement de documents avec onglet). Quand vous travaillez en mode MDI, vous pouvez passer d'un document à un autre en appuyant sur Ctrk+Tab ou vous pouvez utiliser les options de mosaïque du menu **Fenêtre** .  
  
## <a name="docked-tool-window-behavior"></a>Comportement de la fenêtre Outils ancrée  
 **Le bouton Fermer affecte uniquement l’onglet actif**  
 Spécifie que ce bouton ne ferme que la fenêtre Outils qui est active et non les autres fenêtres Outils de l'ensemble ancré. Par défaut, cette case à cocher est activée.  
  
 **Le bouton Masquer automatiquement affecte uniquement l’onglet actif**  
 Spécifie que ce bouton ne masque automatiquement que la fenêtre Outils qui est active et non les autres fenêtres Outils de l'ensemble ancré. Par défaut, cette case est décochée.  
  
## <a name="display"></a>Afficher  
 **Afficher n fichiers dans la liste des derniers fichiers utilisés**  
 Personnalise le nombre de projets et de fichiers récents qui apparaissent dans le menu **Fichier** . Entrez un nombre compris entre 1 et 24. Valeur par défaut : 4. Vous pouvez ainsi facilement récupérer les projets de script et les fichiers récemment utilisés.  
  
  
