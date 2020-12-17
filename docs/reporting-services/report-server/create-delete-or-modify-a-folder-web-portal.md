---
title: Créer, supprimer ou modifier un dossier - Reporting Services | Microsoft Docs
description: Découvrez comment créer, modifier et supprimer des dossiers afin de pouvoir organiser et gérer les éléments que vous publiez sur un serveur de rapports Reporting Services.
ms.date: 06/26/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
ms.assetid: 70a38879-856c-414b-8479-5f9dead38f15
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6826e09f85e001e9932e2c6f85c400f722534c2a
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97409345"
---
# <a name="create-delete-or-modify-a-folder---reporting-services"></a>Créer, supprimer ou modifier un dossier - Reporting Services
  Vous pouvez créer des dossiers pour organiser et gérer les éléments à publier sur un serveur de rapports. La création de dossiers peut permettre aux utilisateurs de rechercher les rapports qui les intéressent. Pour les gestionnaires de contenu, les dossiers fournissent l'infrastructure nécessaire à l'application d'autorisations. Vous pouvez créer des attributions de rôles pour des dossiers spécifiques afin de restreindre l'accès aux rapports en cours de développement ou dont la diffusion doit être restreinte.  

::: moniker range="=sql-server-2016"

## <a name="to-create-a-folder"></a>Pour créer un dossier  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../web-portal-ssrs-native-mode.md).  
  
2.  Dans le Gestionnaire de rapports, sélectionnez le dossier de base et cliquez sur **Nouveau dossier**. Vous pouvez également, pour créer un sous-dossier dans un dossier existant, naviguer jusqu’au dossier de votre choix dans la page **Contenu** , cliquer dessus pour l’ouvrir, puis cliquer sur **Nouveau dossier**.  
  
     La page **Nouveau dossier** s’affiche.  
  
3.  Tapez le nom du dossier. Un nom de dossier peut contenir des espaces, mais aucun caractère réservé au codage d'URL, par exemple les caractères : \; \? \: \@ \& \= \+ \, \$ \/ \* \< \> \|. Vous ne pouvez pas taper une série de noms de dossiers pour créer plusieurs dossiers en même temps.  
  
4.  Tapez éventuellement une description.  
  
5.  Sélectionnez **Masquer en mode Liste** pour faire disparaître le dossier de l’affichage par défaut de la page **Contenu** . Le dossier est visible uniquement par les utilisateurs qui cliquent sur **Afficher les détails** dans la page **Contenu** .  
  
6.  Cliquez sur **OK**.  
  
## <a name="to-delete-a-folder"></a>Pour supprimer un dossier  
  
1.  Dans le Gestionnaire de rapports, accédez à la page **Contenu** , puis recherchez l’élément à modifier.  
  
2.  Pointez sur l'élément et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Supprimer**.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="to-modify-or-delete-a-folder"></a>Pour modifier ou supprimer un dossier  
  
1.  Dans le Gestionnaire de rapports, accédez à la page **Contenu** , puis recherchez l’élément à modifier.  
  
2.  Pointez sur l'élément et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. La page des propriétés générales s'ouvre.  
  
4.  Pour changer l’emplacement du dossier, cliquez sur **Déplacer**. Indiquez l’emplacement du dossier de destination ou choisissez ce dossier dans l’arborescence, puis cliquez sur **OK**.  
  
5.  Vous pouvez aussi modifier les propriétés du dossier en procédant comme suit :  
  
    -   Pour modifier les informations qui s'affichent sur le dossier, tapez un nom ou une description.  
  
    -   Pour afficher le dossier dans l’affichage par défaut de la page **Contenu** , décochez la case **Masquer en mode liste**.  
  
6.  Vous pouvez également supprimer le dossier et son contenu en cliquant sur **Supprimer**.  
  
7.  Cliquez sur **Appliquer** pour enregistrer les modifications.  

::: moniker-end

::: moniker range=">=sql-server-2017"
 
## <a name="to-create-a-folder"></a>Pour créer un dossier  
  
1. Ouvrez [le portail web d’un serveur de rapports (Mode natif SSRS)](../../reporting-services/web-portal-ssrs-native-mode.md).  
  
2. Accédez au dossier ou au sous-dossier dans lequel vous souhaitez rechercher le nouveau dossier. Sélectionnez le dossier **Accueil** avec le bouton **Parcourir** dans la barre d’outils en haut à gauche de la page pour le créer en haut de l’arborescence des dossiers.  
  
3. Sélectionnez le bouton **Nouveau** en haut à droite de la barre d’outils du serveur de rapports, puis sélectionnez **Dossier** dans le menu déroulant.  
  
4. Dans la boîte de dialogue **Créer un nouveau dossier dans (nom du dossier actuel)** , entrez le nom du nouveau dossier à créer. Un nom de dossier peut contenir des espaces, mais aucun caractère réservé au codage d’URL, par exemple les caractères : \; \? \: \@ \& \= \+ \, \$ \/ \* \< \> \|. Vous ne pouvez pas non plus taper une série de noms de dossiers pour créer plusieurs dossiers en même temps.  
  
5. Sélectionnez **Créer** pour terminer l’action.  
  
## <a name="to-delete-a-folder"></a>Pour supprimer un dossier  
  
1. Dans le portail web, naviguez dans la hiérarchie de dossiers pour localiser le dossier à supprimer.  
  
2. Cliquez avec le bouton droit sur le dossier, puis sélectionnez **Supprimer** dans le menu déroulant.  
  
3. Sélectionnez le bouton **Supprimer** dans la boîte de dialogue **Supprimer <foldername>** pour confirmer la suppression.  
  
## <a name="to-modify-a-folders-properties"></a>Pour modifier les propriétés d’un dossier  
  
1. Dans le portail web, naviguez dans la hiérarchie de dossiers pour localiser le dossier à supprimer.  
  
2. Cliquez avec le bouton droit sur le dossier, puis sélectionnez **Supprimer** dans le menu déroulant.  
  
3. Sélectionnez l’onglet **Properties** (Propriétés). La page **Propriétés** s’affiche par défaut.  
  
4. Vous pouvez modifier le nom du dossier dans la zone de texte *Nom**.  
  
5. Vous pouvez ajouter ou modifier la description du dossier dans la zone de texte *Description**.  
  
6. Vous pouvez masquer ou afficher le dossier en cochant ou en décochant la case **Masquer cet élément**, respectivement.  
  
7. Sélectionnez **Appliquer** pour enregistrer les modifications des propriétés.  
  
8. Vous pouvez aussi déplacer ou supprimer le dossier en sélectionnant les boutons **Déplacer** ou **Supprimer** en haut de la page **Propriétés**. Pour plus d’informations, consultez l’article [Déplacer ou supprimer un élément (portail web)](../../reporting-services/report-server/move-or-delete-an-item-report-manager.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer, supprimer ou modifier un dossier (portail web)](../../reporting-services/report-server/create-delete-or-modify-a-folder-web-portal.md)   
 [Gestion du contenu du serveur de rapports (SSRS en mode natif)](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [Recherche, affichage et gestion de rapports &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)    
  
::: moniker-end