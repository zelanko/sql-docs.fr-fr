---
title: Créer une Session d’événements étendus à l’aide de l’Assistant (Explorateur d’objets) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- Sql12.ssms.XeWizard.Summary.f1
- Sql12.ssms.XeWizard.SetSessionProperties.f1
- Sql12.ssms.XeWizard.CaptureAddFields.f1
- Sql12.ssms.XeWizard.SelectEvents.f1
- Sql12.ssms.XeWizard.SpecifySessionTargets.f1
- Sql12.ssms.XeWizard.Welcome.f1
- sql12.ssms.XeWizard.Welcome.f1
- Sql12.ssms.XeWizard.ChooseTemplate.f1
- Sql12.ssms.XeWizard.SetSessionEventFilters.f1
- Sql12.ssms.XeWizard.Results.f1
helpviewer_keywords:
- Sql11.ssms.XeWizard.CaptureAddFields.f1
- Sql11.ssms.XeWizard.SetSessionEventFilters.f1
- Sql11.ssms.XeWizard.SpecifySessionTargets.f1
- Sql11.ssms.XeWizard.Results.f1
- Sql11.ssms.XeWizard.ChooseTemplate.f1
- Sql11.ssms.XeWizard.SetSessionProperties.f1
- Sql11.ssms.XeWizard.Welcome.f1
- Sql11.ssms.XeWizard.Summary.f1
- Sql11.ssms.XeWizard.SelectEvents.f1
ms.assetid: 80c0456f-17c0-41d8-b2aa-502a2f3bb6de
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fc69e3683656c5705e7e82df27b80a8a41cb81a9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48067879"
---
# <a name="create-an-extended-events-session-using-the-wizard-object-explorer"></a>Créer une session d'événements étendus à l'aide de l'Assistant (Explorateur d'objets)
  Pour vous aider à sélectionner et capturer des événements sur votre serveur, les événements étendus incluent un Assistant Nouvelle session qui vous guide tout au long des étapes de création d'une session d'événements étendus. L'Assistant Nouvelle session expose la plupart des fonctionnalités Événements étendus. La [boîte de dialogue Nouvelle session](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md) vous permet également de définir une session Événements étendus qui capture, affiche et analyse vos données. La boîte de dialogue Nouvelle session expose toutes les fonctionnalités Événements étendus.  
  
### <a name="to-open-the-new-session-wizard"></a>Pour ouvrir l'Assistant Nouvelle session  
  
1.  Dans l'Explorateur d'objets, développez le nœud **Gestion** , puis **Événements étendus**.  
  
2.  Cliquez avec le bouton droit sur **Sessions**, puis cliquez sur **Assistant Nouvelle session**.  
  
### <a name="use-the-following-new-session-wizard-pages-to-create-an-event-session"></a>Utiliser les pages suivantes de l'Assistant Nouvelle session pour créer une session d'événements  
  
-   [Introduction](#BKMK_Welcome)  
  
-   [Définir les propriétés de Session](#BKMK_SetSessionProperties)  
  
-   [Choisissez le modèle](#BKMK_ChooseTemplate)  
  
-   [Sélectionnez les événements à capturer](#BKMK_SelectEventsToCapture)  
  
-   [Capturer les champs globaux](#BKMK_CaptureGlobalFields)  
  
-   [Définir des filtres d’événement de Session](#BKMK_SetSessionEventFilters)  
  
-   [Spécifier le stockage des données de Session](#BKMK_SpecifySessionDataOutput)  
  
-   [Résumé](#BKMK_Summary)  
  
-   [Créer la Session d’événements](#BKMK_CreateEventSession)  
  
##  <a name="BKMK_Welcome"></a> Introduction  
 Sur la page **Introduction** , procédez comme suit :  
  
-   Sur la page **Introduction** de l'Assistant Nouvelle session, cliquez sur **Suivant**.  
  
     Cochez la case **Ne plus afficher cette page** si vous souhaitez utiliser l’Assistant plusieurs fois et ne souhaitez pas lire l’introduction à chaque lancement de l’Assistant.  
  
##  <a name="BKMK_SetSessionProperties"></a> Définir les propriétés de Session  
 Sur la page **Définir les propriétés de session** , procédez comme suit :  
  
-   Dans la zone **Nom de session** , tapez un nom explicite pour la session d'événements.  
  
     Si vous souhaitez démarrer la session lorsque vous démarrez le serveur, activez la case à cocher **Démarrer la session d'événements au démarrage du serveur** , puis cliquez sur **Suivant**.  
  
##  <a name="BKMK_ChooseTemplate"></a> Choisissez le modèle  
 Sur la page **Choisir un modèle** , procédez comme suit :  
  
-   Sélectionnez l’option **Utilisez ce modèle de session d’événements** pour sélectionner un jeu de modèles préconfigurés conçu pour les problèmes courants. Sélectionnez le modèle à utiliser dans la liste déroulante, puis cliquez sur **Suivant**.  
  
     -ou-  
  
-   Sélectionnez l’option **Ne pas utiliser de modèle** si vous ne souhaitez pas utiliser un modèle préconfiguré, puis cliquez sur **Suivant**.  
  
##  <a name="BKMK_SelectEventsToCapture"></a> Sélectionnez les événements à capturer  
 Sur la page **Sélectionner les événements à capturer** , procédez comme suit :  
  
1.  Sélectionnez les événements à capturer dans la **Bibliothèque d'événements**, puis cliquez sur la flèche droite. Vous pouvez sélectionner plusieurs événements dans la bibliothèque d'événements en les sélectionnant et en appuyant sur la touche Shift ou Ctrl.  
  
     Vous pouvez sélectionner comment rechercher les événements à capturer dans la zone de liste déroulante. Par exemple, vous pouvez rechercher des noms d'événements ou des noms d'événements et leurs descriptions. Vous pouvez rechercher un mot dans la table en entrant le texte à rechercher dans la zone **Bibliothèque d'événements** . Par exemple, si vous souhaitez rechercher l’événement **lock_acquired** , vous pouvez entrer **lock**ou **lock acquire**.  
  
     Les événements que vous sélectionnez s'affichent dans la zone **Événements sélectionnés** . Pour supprimer des événements de la zone **Événements sélectionnés** , cliquez sur la flèche gauche.  
  
2.  Après avoir sélectionné les événements à capturer, cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  Les événements du canal de **débogage** sont masqués par défaut. Pour afficher des événements de débogage, sélectionnez **Débogage** dans la liste déroulante **Canal** .  
  
##  <a name="BKMK_CaptureGlobalFields"></a> Capturer les champs globaux  
 Vous utilisez des champs globaux (également appelés actions) pour associer une ou plusieurs actions de vos événements sélectionnés. Si vous avez sélectionné un modèle sur la page **Choisir un modèle** , tous les champs globaux définis dans le modèle sont affichés sur cette page.  
  
 Sur la page **Capturer les champs globaux** , procédez comme suit :  
  
-   Sélectionnez les champs globaux à capturer pour la session d'événements, puis cliquez sur **Suivant**.  
  
     Vous pouvez supprimer ou ajouter des champs globaux en sélectionnant ou désactivant la case à cocher en regard du champ global.  
  
    > [!NOTE]  
    >  Les actions sélectionnées sont triées par **Nom** , ce qui vous permet de consulter les actions associées dans l'ordre alphabétique. Vous pouvez trier par description ou par état activé/désactivé en cliquant sur l'en-tête de colonne en regard du nom de champ.  
  
##  <a name="BKMK_SetSessionEventFilters"></a> Définir des filtres d’événement de Session  
 Vous pouvez appliquer des filtres (également appelés prédicats) pour limiter les événements à capturer. Sur la page **Définir des filtres d'événement de session** , procédez comme suit :  
  
1.  Si vous n’utilisez pas de modèle préconfiguré, créez vos critères de filtre, puis cliquez sur **Suivant**.  
  
     Si vous utilisez un modèle préconfiguré, dans la section **Filtres du modèle (en lecture seule)** , l’Assistant Nouvelle session répertorie les filtres déjà créés à partir du modèle.  
  
2.  Dans la section **Filtres supplémentaires** , vous pouvez configurer des filtres supplémentaires pour la session d'événements.  
  
     Les filtres que vous configurez s'appliquent à tous les événements sélectionnés. L'Assistant Nouvelle session ne prend pas en charge la configuration de filtres pour chaque événement.  
  
    > [!NOTE]  
    >  Lorsque vous configurez une clause de groupe pour votre filtre, les parenthèses redondantes sont supprimées du filtre une fois le résultat enregistré. Par exemple, si vous créez un regroupement de filtre **Clause 1** et **Clause 2**, les parenthèses apparaîtront autour des clauses. Une fois que vous avez enregistré le filtre, les parenthèses redondantes sont supprimées. La suppression des parenthèses n'affecte pas la logique de filtre.  
  
##  <a name="BKMK_SpecifySessionDataOutput"></a> Spécifier le stockage des données de Session  
 Vous utilisez la page **Spécifier le stockage des données de session** pour indiquer comment vous souhaitez collecter vos données pour l'analyse. Les événements étendus SQL Server utilisent des cibles pour la sortie des données. Les cibles stockent les données d'événement et peuvent effectuer des actions telles que l'écriture dans un fichier et l'agrégation des données d'événement. Décidez comment vous souhaitez collecter vos données pour l'analyse, et sur la page **Spécifier le stockage des données de session** , procédez comme suit :  
  
1.  Pour les grands groupes de données et la création d'enregistrements historiques, activez la case à cocher **Enregistrer les données dans un fichier en vue d'une analyse ultérieure** , puis procédez comme suit :  
  
    1.  Dans la zone **Nom du fichier sur le serveur** , entrez le chemin d'accès et le nom de fichier ou cliquez sur **Parcourir** pour spécifier le répertoire de fichiers sur le serveur où vous souhaitez enregistrer les données.  
  
    2.  Dans le champ **Taille de fichier maximale** , spécifiez la taille de fichier maximale à utiliser pour la cible de fichier. Si vous ne spécifiez pas de taille de fichier maximale, la taille du fichier augmente jusqu'à ce que le disque soit saturé. La taille de fichier par défaut est 1 gigaoctet (Go).  
  
    3.  Activez la case à cocher **Activer la substitution de fichier** pour permettre la substitution de fichier pour la cible de fichier.  
  
    4.  Dans la zone **Nombre maximal de fichiers** , spécifiez le nombre maximal de fichiers à conserver dans le système de fichiers.  
  
2.  Pour recueillir des données récentes, cochez la case **Utiliser uniquement les données les plus récentes (cible de mémoire tampon en anneau)** , puis procédez comme suit :  
  
    1.  Dans la zone **Nombre d'événements à conserver** , entrez ou sélectionnez le nombre d'événements à conserver en utilisant les flèches haut et bas.  
  
    2.  Dans la zone **Taille maximale de la mémoire tampon** , spécifiez la quantité maximale de mémoire tampon à utiliser. Les événements existants sont supprimés lorsque cette valeur est atteinte.  
  
    3.  Si vous souhaitez conserver un nombre spécifique d’événements de chaque type dans la mémoire tampon, cochez la case **Conserver un nombre spécifique d’événements (par type) lorsque la mémoire tampon est saturée** .  
  
    4.  Dans la zone **Nombre d’événements à conserver (par type)** , entrez ou sélectionnez le nombre d’événements (par type) à conserver en utilisant les flèches haut et bas.  
  
##  <a name="BKMK_Summary"></a> Résumé  
 Sur la page **Résumé** , procédez comme suit :  
  
1.  Assurez-vous que vos sélections sont correctes. Développez les nœuds de la session d'événements pour vérifier que toutes vos sélections seront incluses dans la session d'événements.  
  
2.  Cliquez sur **Script** pour exporter le script de création de session vers une nouvelle fenêtre de l'Éditeur de requête.  
  
3.  Cliquez sur **Terminer** pour créer la session d'événements.  
  
##  <a name="BKMK_CreateEventSession"></a> Créer la Session d’événements  
 Sur la page **Créer une session d'événements** , une fois votre session d'événements créée, procédez comme suit :  
  
1.  Cliquez sur **Démarrer la session d'événements immédiatement après la création de la session** pour démarrer la session après avoir fermé l'Assistant. Vous devez démarrer la session d'événements immédiatement après avoir créé la session pour être en mesure d'observer les données actives.  
  
2.  Pour consulter les données actives de votre session d'événements, cliquez sur **Observer les données actives à l'écran lors de leur capture** . Les données actives commenceront à afficher la trace une fois la session créée.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une session Événements étendus à l’aide de la boîte de dialogue Nouvelle session](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md)  
  
  
