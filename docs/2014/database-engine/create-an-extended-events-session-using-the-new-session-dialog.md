---
title: Créer une session d’événements étendus à l’aide de la boîte de dialogue nouvelle session | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.SSMS.XEDISPLAY.GROUPING.F1
- SQL12.SSMS.XEDISPLAY.AGGREGATION.F1
- SQL12.SSMS.XEDISPLAY.NEWMERGEDCOLUMN.F1
- SQL12.SSMS.XENEWEVENTSESSION.GENERAL.F1
- SQL12.SSMS.XEDISPLAY.EDITCOLUMNS.F1
- SQL12.SSMS.XEDISPLAY.FILTERS.F1
helpviewer_keywords:
- Extended Events Dialog Box
ms.assetid: 6b2244bc-df6a-4b0a-990e-ddd8d42f7907
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 819aa4e09c30fc0b1c28373583f1e224899435d9
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934516"
---
# <a name="create-an-extended-events-session-using-the-new-session-dialog"></a>Créer une session Événements étendus à l'aide de la boîte de dialogue Nouvelle session
  La boîte de dialogue Nouvelle session permet de définir une session Événements étendus qui capture, affiche et analyse vos données. La boîte de dialogue Nouvelle session expose toutes les fonctionnalités Événements étendus.  
  
 L’ [Assistant Nouvelle session](../ssms/object/object-explorer.md) vous permet également de définir une session Événements étendus, prenant en charge la plupart des fonctionnalités Événements étendus.  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Pour ouvrir la boîte de dialogue Nouvelle session, dans l’Explorateur d’objets, développez le nœud **Gestion** , puis **Événements étendus**. Cliquez avec le bouton droit sur **Sessions**, puis cliquez sur **Nouvelle session**.  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> Autorisations  
 Pour créer une session d'événements étendus, vous devez disposer de l'autorisation ALTER ANY EVENT SESSION.  
  
## <a name="to-create-an-extended-events-session-using-the-new-session-dialog"></a>Pour créer une session Événements étendus à l'aide de la boîte de dialogue Nouvelle session  
 Utilisez la page **Général** pour sélectionner un modèle et planifier une session d’événements.  
  
#### <a name="to-select-a-template-and-schedule-an-event-session"></a>Pour sélectionner un modèle et planifier une session d'événements  
  
1.  Dans l'Explorateur d'objets, développez le nœud **Gestion** , puis **Événements étendus**. Cliquez avec le bouton droit sur **Sessions**, puis cliquez sur **Nouvelle session**.  
  
2.  Dans la page **Général** , dans la zone **Nom de session** , tapez un nom explicite pour la session d’événements.  
  
3.  Dans la zone **Modèle** , sélectionnez le modèle à utiliser dans la liste déroulante.  
  
     Vous pouvez sélectionner un jeu de modèles préconfigurés conçu pour les problèmes courants ou vous pouvez sélectionner **À partir du fichier** pour utiliser un fichier modèle exporté d’une définition de session précédente. Notez que vous pouvez également modifier la configuration de la session après avoir appliqué le modèle.  
  
4.  Dans la section **Planification** , si vous souhaitez démarrer la session lorsque vous démarrez le serveur, activez la case à cocher **Démarrer la session d’événements au démarrage du serveur** .  
  
     Si vous souhaitez démarrer la session après l’avoir créée, cochez la case **Démarrer la session d’événements immédiatement après la création de la session** .  
  
5.  Pour consulter les données actives de votre session d’événements, cliquez sur **Observer les données actives à l’écran lors de leur capture**. Les données actives commenceront à afficher la trace une fois la session créée.  
  
6.  Dans la section **Suivi de la causalité** , cochez la case **Assurer le suivi des liens entre les événements** pour suivre un travail sur plusieurs tâches.  
  
     Pour plus d’informations sur le suivi de causalité, consultez « contenu et caractéristiques de la session » dans la rubrique [sessions d’événements étendus SQL Server](../relational-databases/extended-events/sql-server-extended-events-sessions.md) .  
  
     Pour ajouter des événements à votre session, dans la section **Sélectionner une page** , cliquez sur **Événements**.  
  
    > [!NOTE]  
    >  Ne cliquez pas sur **OK** avant d’avoir créé la session d’événements.  
  
 Utilisez la page **Événements** pour rechercher et ajouter les événements à capturer pour la session.  
  
#### <a name="to-add-events-to-a-session"></a>Pour ajouter des événements à une session  
  
1.  Dans la boîte de dialogue Nouvelle session, dans la section **Sélectionner une page** , sélectionnez **Événements**.  
  
2.  Dans la page **Événements** , cliquez sur **Sélectionner** (le bouton **Sélectionner** est estompé si vous êtes déjà au niveau de l’écran **Sélectionner les événements à capturer** ).  
  
     Vous pouvez rechercher un mot dans la table en entrant le texte à rechercher dans la zone **Bibliothèque d'événements** . Par exemple, si vous voulez rechercher l’événement **lock_acquired** , vous pouvez entrer **lock** ou **lock acquire**.  
  
3.  Dans la section **Bibliothèque d’événements** , sélectionnez la manière de rechercher les événements à capturer dans la liste déroulante. Par exemple, vous pouvez rechercher des noms d'événements ou des noms d'événements et leurs descriptions. Entrez vos critères de recherche dans la zone **Rechercher** .  
  
    > [!NOTE]  
    >  Les événements du canal de **débogage** sont masqués par défaut. Pour afficher des événements de débogage, sélectionnez **Débogage** dans la liste déroulante **Canal** .  
  
     Les détails des événements sélectionnés s’affichent dans le volet d’informations sous **Bibliothèque d’événements**.  
  
     Les événements sont triés par nom dans l'ordre alphabétique. Vous pouvez trier par d'autres détails de l'événement en cliquant sur l'en-tête de colonne approprié. Par exemple, vous pouvez trier par la colonne **Catégorie** ou **Canal** .  
  
4.  Sélectionnez le ou les événements à capturer, puis cliquez sur la flèche vers la droite pour déplacer le ou les événements vers la section **Événements sélectionnés** .  
  
    > [!NOTE]  
    >  Vous pouvez sélectionner simultanément plusieurs événements dans la **Bibliothèque d’événements** à l’aide de la touche Ctrl ou Maj.  
  
     Pour configurer les événements sélectionnés, cliquez sur **Configurer**.  
  
    > [!NOTE]  
    >  Ne cliquez pas sur **OK** avant d’avoir créé la session d’événements.  
  
 Vous utilisez la page **Stockage de données** pour ajouter des cibles à une session d’événements. Les cibles stockent des données d'événement et peuvent effectuer des actions telles que l'enregistrement des événements dans un fichier afin d'afficher et d'agréger ultérieurement les données d'événement pour la session. Pour plus d’informations sur les cibles des événements étendus, consultez [Cibles des événements étendus SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md).  
  
 Vous pouvez utiliser les cibles suivantes pour une session d'événements étendus :  
  
-   **etw_classic_sync_target**. Permet de mettre en corrélation les événements SQL Server avec les données d’événement du système d’exploitation Windows ou des applications.  
  
-   **event_counter**. Permet de comptabiliser tous les événements qui surviennent après avoir démarré une session d'événements étendus. Permet d'obtenir des informations sur les caractéristiques de charge de travail sans ajouter la surcharge de la collecte d'événements complète.  
  
-   **event_file**. Permet d'enregistrer sur le disque les résultats d'une session d'événements stockés en mémoire tampon.  
  
-   **histogramme**. À utiliser pour comptabiliser le nombre d'occurrences d'un événement donné, en fonction d'une colonne d'événement ou d'une action définie.  
  
-   **pair_matching**. Permet de savoir si un événement jumelé n'entre pas dans le cadre d'une correspondance.  
  
-   **ring_buffer**. Permet de conserver les événements en mémoire selon le principe FIFO (premier entré/premier sorti) ou au cas par cas.  
  
#### <a name="to-configure-global-fields-for-a-session"></a>Pour configurer des champs globaux pour une session  
  
1.  Dans la page **Événements** , après avoir sélectionné les événements à ajouter à la session d’événements, cliquez sur **Configurer**.  
  
     Après avoir cliqué sur **Configurer**, la section **Bibliothèque d’événements** est réduite et la section **Événements sélectionnés** glisse vers la gauche de la page. La section **Options de configuration d’événement** que vous utilisez pour configurer les événements apparaît du côté droit de la page. Vous utilisez les onglets de cette page pour configurer des actions pour votre session d'événements.  
  
2.  Sous l’onglet **Champs globaux** , sélectionnez les champs à appliquer aux événements sélectionnés.  
  
     Vous pouvez sélectionner plusieurs champs pour chaque événement.  
  
    > [!NOTE]  
    >  Si deux événements qui sont déjà sélectionnés ont des actions configurées différentes, les événements étendus afficheront les actions partiellement activées. Pour rechercher rapidement les actions activées, vous pouvez trier par l'état activé/désactivé en cliquant sur l'en-tête de colonne au-dessus des cases à cocher.  
  
3.  Sous l’onglet  **Filtres** , appliquez les filtres (également appelés prédicats) pour limiter les événements à capturer.  
  
     Si un filtre est appliqué à l'événement sélectionné, une coche s'affiche dans la colonne.  
  
    > [!NOTE]  
    >  Vous pouvez sélectionner plusieurs événements auxquels vous souhaitez appliquer un filtre à à l'aide des touches Ctrl ou Maj. Toutefois, seuls les champs d'événement communs apparaîtront pour la configuration. Si des filtres différents sont déjà configurés pour deux événements sélectionnés, le filtre n'apparaîtra pas. Reconfigurer des filtres permet de remplace des valeurs de filtre existantes.  
  
    > [!NOTE]  
    >  Lorsque vous configurez une clause de groupe pour votre filtre, les parenthèses redondantes sont supprimées du filtre une fois le résultat enregistré. Par exemple, si vous créez un regroupement de filtre **Clause 1** et **Clause 2**, les parenthèses apparaîtront autour des clauses. Une fois que vous avez enregistré le filtre, les parenthèses redondantes sont supprimées. La suppression des parenthèses n'affecte pas la logique de filtre.  
  
4.  Sous l’onglet **Champs d’événements** , vous sélectionnez les champs d’événements à appliquer à un événement sélectionné.  
  
     Les événements contiennent plusieurs champs qui sont toujours recueillis, lesquels sont affichés sous l’onglet **Champs d’événements** sans case à cocher. Un événement peut également avoir des champs facultatifs qui ne sont pas recueillis par défaut (par exemple, les champs facultatifs chers ne sont pas sélectionnés). Les champs facultatifs apparaissent également sous l’onglet **Champs d’événements** avec des cases à cocher. Pour recueillir un champ facultatif, activez la case à cocher devant le champ facultatif.  
  
    > [!NOTE]  
    >  Les options de champ d'événement afficheront des champs qui seront capturés et affichés dans les résultats de trace. (Les événements étendus affichent seulement des types de données de champs d'événements. Par exemple, les champs d'événements en lecture seule ne sont pas affichés.) Si vous sélectionnez deux événements ou plus, la boîte de dialogue Nouvelle session affiche un espace sous l’onglet **Champs d’événements** .  
  
5.  Pour ajouter des cibles à une session d’événements, dans la section **Sélectionner une page**, sélectionnez **Stockage de données**.  
  
    > [!NOTE]  
    >  Ne cliquez pas sur **OK** avant d’avoir créé la session d’événements.  
  
#### <a name="to-add-targets-to-an-event-session"></a>Pour ajouter des cibles à une session d'événements  
  
1.  Dans la boîte de dialogue Nouvelle session, dans la section **Sélectionner une page** , sélectionnez **Stockage de données**.  
  
2.  Dans la page **Stockage de données** , sélectionnez le type de cible dans la liste déroulante.  
  
     Une fois que vous avez sélectionné le type de cible, la description de la cible s'affiche. Vous pouvez ajouter une cible une seule fois. Si vous avez déjà ajouté la cible à la session, elle ne s'affichera pas dans la liste déroulante.  
  
3.  Cliquez sur **Ajouter** pour ajouter une cible pour la session d’événements. Pour supprimer une cible, cliquez sur **Supprimer**.  
  
     Les propriétés cibles apparaissent sous la section **Cibles** , selon la cible sélectionnée.  
  
4.  Vous pouvez spécifier les propriétés suivantes, en fonction des cibles sélectionnées :  
  
    |Cible|Propriétés cibles|  
    |------------|-----------------------|  
    |**etw_classic_sync_target**|**Nom du fichier journal de la session sur le serveur**. Entrez le nom du fichier journal et le répertoire sur le serveur, ou cliquez sur **Parcourir** pour rechercher et sélectionner le fichier journal.<br /><br /> **Taille maximale du fichier journal**. Entrez la taille maximale du fichier journal pour l'événement du Suivi d'événements pour Windows (ETW). La valeur par défaut est 20 mégaoctets (Mo). Vous pouvez sélectionner une unité différente de stockage dans la liste déroulante.<br /><br /> **Taille de la mémoire tampon**. Entrez la taille de la mémoire tampon pour la session d'événements. La valeur par défaut est 128 kilo-octets (Ko). Vous pouvez sélectionner une unité différente de stockage dans la liste déroulante.<br /><br /> **Nom de session**. Entrez un nom de session ETW explicite.<br /><br /> **Réessayer en cas d’erreur d’écriture dans le suivi des événements ETW**. Activez cette case à cocher pour effectuer une nouvelle tentative de publication de l'événement dans le sous-système ETW.<br /><br /> **Nombre maximal de tentatives**. Entrez le nombre maximal de nouvelles tentatives de publication de l'événement dans le sous-système ETW avant la suppression de l'événement. Le nombre de tentatives par défaut est zéro (0). Pour cette propriété cible, zéro (0) signifie aucune tentative.|  
    |**event_counter**|Il n'y a pas de propriété cible pour le compteur d'événements.|  
    |**event_file**|**Nom du fichier sur le serveur**. Entrez le répertoire et le nom du fichier cible sur le serveur, ou cliquez sur **Parcourir** pour rechercher et sélectionner le fichier cible.<br /><br /> **Taille de fichier maximale**. Spécifiez la taille de fichier maximale pour la cible de fichier. Si vous ne spécifiez pas de taille de fichier maximale, la taille du fichier augmente jusqu'à ce que le disque soit saturé. La taille de fichier par défaut est 1 gigaoctet (Go). Vous pouvez sélectionner une unité différente de stockage dans la liste déroulante.<br /><br /> **Activez la substitution de fichier**. Activez cette case à cocher pour permettre la substitution de fichier pour la cible de fichier.<br /><br /> **Nombre maximal de fichiers**. Entrez le nombre maximal de fichiers à conserver dans le système de fichiers.|  
    |**histogramme**|**Événement sur lequel filtrer**. Sélectionnez l'événement sur lequel vous souhaitez filtrer dans la liste déroulante. Vous pouvez appliquer un filtre sur tout événement qui existe dans la session d'événements. Vous pouvez également sélectionner **\<None>** dans la liste déroulante pour inclure tous les événements et les compartiments de base sur l’action.<br /><br /> **Baser les compartiments sur : Action**. Sélectionnez cette option pour baser les compartiments sur le nom d'action utilisé comme source de données, puis sélectionnez l'action dans la liste déroulante.<br /><br /> **Baser les compartiments sur : Champ**. Sélectionnez cette option pour baser les compartiments sur le champ d'événement utilisé comme source de données, puis sélectionnez le champ dans la liste déroulante.<br /><br /> **Nombre maximal de compartiments**. Entrez le nombre maximal de compartiments à conserver. Lorsque cette valeur est atteinte, la session d'événements ignore tous les nouveaux événements qui n'appartiennent pas aux compartiments existants.|  
    |**pair_matching**|**Événements : Commencer par**. Sélectionnez le nom d'événement dans la liste déroulante qui spécifie l'événement de début dans une séquence appariée.<br /><br /> **Événements : Se terminer par**. Sélectionnez le nom d'événement dans la liste déroulante qui spécifie l'événement de fin dans une séquence appariée.<br /><br /> **Champs et actions : Commencer par**. Sélectionnez le champ de début et/ou l'action dans une séquence appariée dans la liste déroulante.<br /><br /> **Champs et actions : Se terminer par**. Sélectionnez le champ de fin et/ou l'action dans une séquence appariée dans la liste déroulante.<br /><br /> **Ignorer les nouveaux événements non appariés en cas de sollicitation de la mémoire**. Activez cette case à cocher pour cesser de collecter des événements dans la cible pair_matching lorsque la mémoire de l'ordinateur est sollicitée. Lorsque la mémoire ne sera plus sollicitée, la collecte des événements reprendra.<br /><br /> **Nombre maximal d’événements orphelins**. Spécifiez le nombre maximal d'événements orphelins à conserver dans la mémoire.|  
    |**ring_buffer**|**Nombre d’événements à conserver**. Utilisez les flèches haut et bas pour spécifier le nombre d'événements à conserver. La valeur par défaut est 1000.<br /><br /> **Taille maximale de la mémoire tampon**. Entrez la quantité de mémoire maximale à utiliser. Les événements existants sont supprimés lorsque cette valeur est atteinte. La taille de la mémoire par défaut est 0 mégaoctet (Mo), c'est-à-dire, illimitée. Vous pouvez sélectionner une unité différente de stockage dans la liste déroulante.<br /><br /> **Conserver un nombre spécifique d’événements (par type) lorsque la mémoire tampon est saturée**. Sélectionnez cette option pour conserver un nombre spécifique d'événements de chaque type dans la mémoire tampon.<br /><br /> **Nombre d’événements à conserver (par type)**. Entrez le nombre par défaut d'événements de chaque type à conserver dans la mémoire tampon.|  
  
5.  Si vous voulez définir des propriétés de configuration avancées, sélectionnez **Avancé** dans la section **Sélectionner une page** .  
  
    > [!NOTE]  
    >  Ne cliquez pas sur **OK** avant d’avoir créé la session d’événements.  
  
#### <a name="to-set-advanced-configurations"></a>Pour définir des configurations avancées  
  
1.  Dans la boîte de dialogue Nouvelle session, dans la section **Sélectionner une page** , sélectionnez **Avancé**.  
  
2.  Dans la page **Avancé** , pour spécifier les options **Mode de rétention d’événement** de la session d’événements, procédez comme suit :  
  
    1.  **Perte d’événement unique**. Sélectionnez cette option pour autoriser la perte d'un événement unique.  
  
    2.  **Perte d’événements multiples**. Sélectionnez cette option pour autoriser la perte de plusieurs événements.  
  
    3.  **Aucune perte d’événement**. Sélectionnez cette option si vous souhaitez empêcher la perte d'événement. Cette option n'est pas recommandée.  
  
        > [!NOTE]  
        >  Certains événements tels que l’événement **sqlos.wait_info** ne sont pas compatibles avec le mode de rétention d’événement **Aucune perte d’événement** .  
  
3.  Pour spécifier les options **Latence maximale de répartition** pour la session d’événements, procédez comme suit :  
  
    1.  **En secondes**. Sélectionnez cette option pour prolonger ou raccourcir la latence de répartition maximale. Utilisez les flèches haut et bas pour spécifier la latence de répartition maximale en secondes.  
  
    2.  **Illimité**. Sélectionnez cette option si vous souhaitez distribuer les événements uniquement lorsque la mémoire tampon est saturée.  
  
4.  Dans la zone **Taille de la mémoire maximale** , entrez la taille de mémoire maximale. Les événements existants sont supprimés lorsque cette valeur est atteinte. Vous pouvez sélectionner une unité différente de stockage dans la liste déroulante.  
  
5.  Dans la zone **Taille d’événement maximale** , entrez la taille d’événement maximale pour les événements qui sont trop grands pour être contenus dans la **Taille de la mémoire maximale**. Si vous ne collectez pas d'événements très volumineux, vous n'avez pas besoin de configurer cette option. Vous pouvez sélectionner une unité différente de stockage dans la liste déroulante.  
  
6.  Pour spécifier les options **Mode de partition mémoire** pour la session d’événements, procédez comme suit :  
  
    1.  **Aucun**. Sélectionnez cette option si vous ne souhaitez pas de mode de partition de la mémoire.  
  
    2.  **Par nœud**. Sélectionnez cette option si vous souhaitez partitionner la mémoire par nœud.  
  
    3.  **Par UC**. Sélectionnez cette option si vous souhaitez partitionner la mémoire par UC.  
  
 Pour restaurer les valeurs par défaut de configuration pour les propriétés de session précédentes, cliquez sur **Paramètres par défaut**.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une session d’événements étendus à l’aide de l’éditeur de requête](../../2014/database-engine/create-an-extended-events-session-using-query-editor.md)   
 [Créez une session d’événements étendus à l’aide de l’Assistant &#40;l’Explorateur d’objets&#41;](../ssms/object/object-explorer.md)   
 [Générer un script de session d'événements étendus](../../2014/database-engine/script-an-extended-event-session.md)  
  
  
