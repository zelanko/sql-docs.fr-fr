---
title: Créer un projet | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.newproject
- vs.addnewproject
helpviewer_keywords:
- projects [SQL Server Management Studio], creating
ms.assetid: 7897be19-365b-4b06-bcf0-8a669f67a673
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8ee87fea9b2586b8da9c54b2d074228b93a97e11
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37191199"
---
# <a name="create-a-project"></a>Créer un projet
  Vous pouvez créer un ou plusieurs projets à l'intérieur d'une solution existante.  
  
### <a name="to-create-a-new-project-and-add-it-to-a-solution"></a>Pour créer un projet et l'ajouter à une solution  
  
1.  Dans l'Explorateur de solutions, sélectionnez la solution de votre choix.  
  
2.  Dans le menu **Fichier** , pointez sur **Ajouter**, puis cliquez sur **Nouveau projet**.  
  
3.  Dans la boîte de dialogue  **Nouveau projet** , cliquez sur un type de projet.  
  
     **Modèles**  
     Dans la zone **Modèles** , sélectionnez un modèle. Une brève description du modèle de projet sélectionné apparaît sous la zone **Modèles** .  
  
     **Nom**  
     Entrez le nom du projet de script que vous voulez créer. Un dossier avec un nom identique à celui du projet est également créé à l’emplacement indiqué dans le champ **Emplacement** . Pour certains projets, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] crée des fichiers sources et de prise en charge, qu'il place dans le dossier du nouveau projet.  
  
    > [!NOTE]  
    >  Pour certains types de projets, la zone de texte **Nom** n’est pas disponible car l’indication de l’emplacement définit le nom. Par exemple, les applications Web et les services Web sont situés sur un serveur Web et leur nom est dérivé du répertoire virtuel spécifié sur ce serveur.  
  
     Les noms ne peuvent pas contenir les caractères suivants :  
  
    -   dièse (#)  
  
    -   Pourcentage (%)  
  
    -   Esperluette (&)  
  
    -   astérisque (*)  
  
    -   barre verticale (|)  
  
    -   Barre oblique inverse (\\)  
  
    -   deux-points (:)  
  
    -   guillemets (")  
  
    -   Inférieur à (\<)  
  
    -   Supérieur à (>)  
  
    -   point d'interrogation (?)  
  
    -   barre oblique (/)  
  
    -   espaces à gauche ou à droite (' ')  
  
    -   noms réservés pour Microsoft Windows ou MS-DOS (« nul », « aux », « con », « com1 », « lpt1 », etc.)  
  
     **Emplacement**  
     Entrez l'emplacement dans lequel vous voulez créer votre projet ou choisissez-en un dans la liste.  
  
     **Parcourir**  
     Affiche la boîte de dialogue **Emplacement du projet** , afin que vous puissiez naviguer jusqu’au répertoire dans lequel le projet doit être enregistré.  
  
     **Solution**  
     Sélectionnez **Créer une nouvelle solution** pour créer une solution dans l’Explorateur de solutions. Sélectionnez **Ajouter à la solution** pour ajouter le nouveau projet à la solution ouverte dans l’Explorateur de solutions.  
  
     **Créer le répertoire pour la solution**  
     Sélectionnez cette option pour activer la zone de texte **Nom de solution** . Cette option crée un nouveau répertoire portant le nom choisi pour le projet et la solution.  
  
     **Nom de solution**  
     Entrez le nom de la nouvelle solution dans laquelle le projet doit être créé. Par défaut, ce champ utilise le même nom que celui qui a été entré dans le champ **Nom** .  
  
     **Remarque** Pour accéder à cette option, vous devez cocher les cases **Créer une nouvelle solution** dans **Solution** et **Créer un répertoire pour la solution** . Certains modèles de projet, comme les applications Web, ne prennent pas en charge cette option.  
  
     **Ajouter au contrôle de code source**  
     Si cette case est cochée, l’application de contrôle de code source s’ouvre quand vous cliquez sur **OK**. Pour poursuivre, fournissez les informations requises par l'application de contrôle de code source. Pour utiliser cette option, une application cliente de contrôle de code source doit être installée.  
  
4.  Cliquez sur **OK**.  
  
 Vous pouvez attribuer un nom au projet de script mais vous ne pouvez pas modifier les noms de dossiers qui sont attribués par [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] . Vous pouvez configurer la spécification de lecteur et de chemin d’accès pour l’ensemble commun des dossiers à l’aide de la boîte de dialogue **Ajouter un nouveau projet** . Cliquez avec le bouton droit sur l’icône de la solution dans **l’Explorateur de solutions**, puis cliquez sur **Ajouter**. L’emplacement par défaut pour les dossiers de projets de scripts est : C:\Documents and Settings\\*nom_utilisateur*\My Documents\SQL Server Management Studio\Projects\\.  
  
## <a name="see-also"></a>Voir aussi  
 [Explorateur de solutions](solution-explorer.md)   
 [Ajouter un projet existant à une Solution](add-an-existing-project-to-a-solution.md)   
 [Ajouter de nouveaux éléments à un projet](add-new-items-to-a-project.md)   
 [Ajouter des éléments existants à un projet](add-existing-items-to-a-project.md)   
 [Modifier l’emplacement par défaut pour les projets](change-the-default-location-for-projects.md)   
 [Enlever ou supprimer un élément ou un projet](remove-or-delete-an-item-or-project.md)   
 [Supprimer une solution](delete-a-solution.md)  
  
  
