---
title: Nouvelles fonctionnalités de l’interface graphique utilisateur de SSMA pour DB2 (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: a8ed33e9-185a-492d-a4cf-2fded1aa5c70
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b15759f9cee25c214ba67c09590f46093d41f22f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635947"
---
# <a name="new-gui-features-in-ssma-for-db2-db2tosql"></a>Nouvelles fonctionnalités de l’interface graphique utilisateur de SSMA pour DB2 (DB2ToSQL)
Ce chapitre décrit les nouvelles fonctionnalités de l’Interface utilisateur de SSMA.  
  
## <a name="layouts"></a>Dispositions  
Cette fonctionnalité vous permet de choisir l’une des deux fenêtres prédéfinis mise en page-out ou créer votre propre disposition. Pour accéder au sous-menu de disposition, dans le menu Affichage pointez dispositions. Vous pouvez choisir une des dispositions existantes, ajouter la nouvelle disposition ou gérer les dispositions.  
  
### <a name="add-current-layout"></a>Ajouter la disposition actuelle  
Pour enregistrer la disposition actuelle de windows, dans le menu Affichage, pointez sur les dispositions, puis cliquez sur Ajouter une disposition actuelle.  
  
### <a name="choose-predefined-layout"></a>Choisir une disposition prédéfinie  
Pour choisir une des dispositions prédéfinies, dans le menu Affichage, pointez sur les dispositions, puis cliquez sur disposition par défaut ou sans explorateurs. Vous pouvez également utiliser des raccourcis Ctrl + Alt + 1 ou Ctrl + Alt + 2 pour les dispositions prédéfinies.  
  
### <a name="choose-user-defined-layout"></a>Choisir la disposition défini par l’utilisateur  
Pour choisir la disposition défini par l’utilisateur, dans le menu Affichage, pointez sur mises en page, puis cliquez sur un de la mise en page définie par l’utilisateur. Vous pouvez également utiliser des raccourcis définis pour les dispositions.  
  
### <a name="manage-layouts"></a>Gérer les dispositions  
Pour ouvrir la boîte de dialogue Gérer les dispositions, dans le menu Affichage, pointez sur les dispositions et cliquez sur Gérer les dispositions. Dans la boîte de dialogue Gérer les dispositions, vous trouverez une liste des configurations existantes sur le côté gauche de la boîte de dialogue. Il vous pouvez sélectionner la mise en page pour modifier ses paramètres. Vous pouvez également modifier l’ordre de dispositions dans la liste ou supprimer la disposition à l’aide des boutons en haut de la liste. Sur le côté droit de la boîte de dialogue, vous pouvez modifier les paramètres de disposition suivants :  
  
-   Nom de la disposition  
  
-   Synchronisation des explorateurs de métadonnées  
  
-   Visibilité et la largeur des explorateurs de métadonnées source et cible  
  
-   Visibilité de leurs tailles et les fenêtres source ou cible  
  
-   Visibilité et la hauteur de windows auxiliaires  
  
## <a name="bookmarks"></a>Signets  
Cette fonctionnalité vous permet de définir un ou plusieurs signets dans la source ou le code cible, rapide trouvé un signet à l’aide de raccourcis, gérer les signets avec une boîte de dialogue convivial.  
  
### <a name="toggle-bookmark"></a>Basculer le signet  
Vous pouvez définir/supprimer un signet comme suit :  
  
-   Utilisez le bouton Masquer le signet en haut de la fenêtre SQL source ou cible  
  
-   Cliquez sur la zone grise située à gauche de la fenêtre SQL  
  
-   Utilisez Ctrl + Maj +&lt;0.9&gt; pour définir le signet numéroté  
  
### <a name="bookmark-navigation"></a>Navigation vers les signets  
Vous pouvez visite les signets de plusieurs manières :  
  
-   Utilisez les boutons signet suivant, le signet précédent en haut de la fenêtre SQL  
  
-   Utilisez Ctrl +&lt;0.9&gt; pour trouver le signet numéroté  
  
-   Utilisez les boutons Atteindre ou afficher la Source dans la boîte de dialogue Gérer les signets  
  
### <a name="removing-bookmark"></a>Suppression de signet  
Vous pouvez supprimer un signet comme suit :  
  
-   Utilisez le bouton Effacer en haut de la fenêtre SQL pour supprimer tous les signets dans le document actif  
  
-   Utilisez les boutons Supprimer ou supprimer tout dans la boîte de dialogue Gérer les signets  
  
### <a name="manage-bookmarks"></a>Gérer les signets  
Pour ouvrir la boîte de dialogue Gérer les signets, cliquez sur Gérer les signets dans le menu Edition. Dans la boîte de dialogue, vous verrez une liste de signets existants. Vous pouvez utiliser les boutons sur le côté droit de la boîte de dialogue pour gérer les signets.  
  
## <a name="object-history"></a>Historique de l’objet  
L’historique de l’interface graphique utilisateur objet vous permet des avantages suivants lorsque vous naviguez d’objets :  
  
-   Vous pouvez utiliser les boutons Précédent et suivant pour parcourir les objets que vous avez déjà consultées  
  
-   Lors de la sauvegarde à l’objet, vous sauvegardez sur le même onglet que vous avez laissées  
  
-   Lorsque vous revenez à l’objet et l’onglet est SQL, vous sauvegardez vers la même position de curseur qui vous avez quitté  
  
## <a name="advanced-search-capabilities"></a>Fonctionnalités de recherche avancées  
Fonctionnalités de recherche avancées fournissent les fonctionnalités de recherche puissantes et flexibles et vous permettent de trouver la déclaration d’objet, obtenir des informations relatives aux objets, effectuer une recherche rapide, effectuer d’objet avancée recherche dans les catégories à l’aide de modèles, etc.  
  
### <a name="get-quick-information"></a>Obtenir rapidement des informations  
Vous pouvez obtenir rapidement des informations sur l’objet à la position du curseur comme suit :  
  
-   Cliquez sur le bouton Info Express en haut de la fenêtre SQL  
  
-   Sélectionnez Info express dans le menu contextuel  
  
-   Appuyez sur Ctrl + Maj + espace  
  
### <a name="find-declaration"></a>Recherchez la déclaration  
Vous pouvez accéder à la déclaration de l’objet à la position du curseur comme suit :  
  
-   Cliquez sur le bouton Atteindre la déclaration en haut de la fenêtre SQL  
  
-   Sélectionnez Atteindre la déclaration dans le menu contextuel  
  
-   Appuyez sur F12  
  
### <a name="quick-search"></a>Recherche rapide  
Vous pouvez effectuer la recherche en texte rapide à l’aide des fonctionnalités suivantes :  
  
-   Vous pouvez commencer la recherche à l’aide du raccourci Ctrl + F  
  
-   Vous pouvez répéter la dernière recherche vers l’avant à l’aide de F3  
  
-   Vous pouvez répéter la dernière recherche vers l’arrière à l’aide de MAJ + F3  
  
-   Vous pouvez trouver l’occurrence suivante du mot à la position de curseur à l’aide de Ctrl + F3  
  
-   Vous pouvez trouver l’occurrence précédente du mot à la position de curseur à l’aide de Ctrl + Maj + F3  
  
-   Vous pouvez également effectuer toutes ces actions avec les éléments de menu.  
  
### <a name="advanced-search"></a>Recherche avancée  
Pour ouvrir la boîte de dialogue Recherche avancée, sur le point de menu Modifier Rechercher, puis cliquez sur recherche avancée. Dans la boîte de dialogue, vous serez en mesure de trouver n’importe quel objet à l’aide du modèle. En haut de la boîte de dialogue vous pouvez choisir les catégories d’objet et de la zone de recherche.  
  
