---
title: Gérer une instance CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- manIns
ms.assetid: cfed22c8-c666-40ca-9e73-24d93e85ba92
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3215f28615511f3c35fcc6cc3ea80209c7c44d41
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58378817"
---
# <a name="manage-a-cdc-instance"></a>Gérer une instance de capture de données modifiées
  Vous pouvez utiliser la console du concepteur CDC pour afficher des informations sur les instances que vous créez et gérer le fonctionnement des instances.  
  
 Cliquez sur le nom d'une instance dans le volet gauche pour afficher les informations sur l'instance.  
  
> [!NOTE]  
>  Si vous sélectionnez un service dans le volet gauche, la liste des instances disponibles s'affiche également au centre de la console du concepteur CDC. Si vous sélectionnez l'une des instances dans cette section, vous pouvez effectuer les tâches indiquées dans le volet droit ; toutefois, vous ne pourrez pas afficher les informations dans les onglets de propriétés.  
  
## <a name="what-you-can-do-when-you-display-the-cdc-instance-information"></a>Opérations réalisables lorsque vous affichez les informations d'instance CDC  
 Les actions suivantes s'effectuent à partir du volet droit :  
  
 **Démarrer**  
 Cliquez sur **Démarrer** pour démarrer la capture des modifications pour l’instance de capture des données modifiées sélectionnée.  
  
 **Arrêter**  
 Cliquez sur **Arrêter** pour arrêter de capturer des modifications pour l’instance sélectionnée de capture de données modifiées. Lorsque vous arrêtez l'instance de capture de données modifiées, les modifications qui ont été capturées à ce stade ne sont pas perdues et sont remises lorsque l'instance de capture de données modifiées reprend.  
  
 **Réinitialiser**  
 Cliquez sur **Réinitialiser** pour rétablir l’état (vide) initial de l’instance de capture de données modifiées. Cette option est disponible lorsque l'instance de capture de données modifiées est arrêtée. Toutes les modifications des tables de modifications et de l'état interne de l'instance de capture de données modifiées sont supprimées. Lorsque l'instance de capture de données modifiées est démarrée ultérieurement, la capture de modifications démarre à partir de ce point et inclut uniquement les transactions qui ont démarré après que l'instance de capture de données modifiées a démarré.  
  
 Cliquez sur **OK** dans la boîte de dialogue de confirmation pour confirmer que vous voulez réinitialiser l'instance de capture de données modifiées et supprimer les modifications écrites dans les tables de modifications.  
  
 **Supprimer**  
 Cliquez sur **Supprimer** pour supprimer de façon permanente l’instance de capture des données modifiées. Cette option n'est disponible que lorsque l'instance de capture de données modifiées est arrêtée.  
  
 Cliquez sur **OK** dans la boîte de dialogue de confirmation pour confirmer que vous souhaitez supprimer l'instance de capture de données modifiées.  
  
 **Script de journalisation Oracle**  
 Cliquez sur ce lien pour afficher la boîte de dialogue du script de journalisation Oracle avec le script de journalisation supplémentaire Oracle. Pour plus d'informations sur les opérations réalisables dans cette boîte de dialogue, consultez [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md).  
  
> [!NOTE]  
>  Lorsque vous exécutez des scripts de journalisation supplémentaires, la boîte de dialogue des informations d'identification Oracle pour l'exécution de script s'ouvre et vous permet de spécifier un nom d'utilisateur et un mot de passe Oracle valides. Pour plus d'informations sur la façon de fournir les informations d'identification Oracle appropriées, consultez [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md).  
  
 **Script de déploiement d'instance CDC**  
 Cliquez sur ce lien pour afficher la boîte de dialogue du script de déploiement d'instance de capture de données modifiées qui affiche le script de déploiement d'instance de capture de données modifiées. Pour plus d'informations sur cette boîte de dialogue, consultez [CDC Instance Deployment Script](cdc-instance-deployment-script.md).  
  
 **Propriétés**  
 Cliquez sur ce lien pour ouvrir l'éditeur de propriétés. Vous modifiez la configuration de l'instance de capture de données modifiées à l'aide de l'éditeur de propriétés. Pour plus d'informations sur la modification des propriétés pour une instance de capture de données modifiées, consultez [Edit Instance Properties](edit-instance-properties.md).  
  
 **Onglets de la visionneuse**  
  
 Les onglets suivants de la visionneuse sont disponibles lorsque vous affichez des informations pour l'instance de capture de données modifiées. Les informations contenues dans ces onglets sont en lecture seule.  
  
 **État**  
 Cet onglet fournit des informations et des statistiques sur l'état actuel de l'instance CDC. Il contient les informations suivantes :  
  
-   **État** : Une icône qui indique l’état actuel de l’instance de capture de données modifiées. La section suivante décrit les états.  
  
    |||  
    |-|-|  
    |![Erreur](../media/error.gif "Erreur")|**Erreur**. L'instance Oracle CDC n'est pas en cours d'exécution, car une erreur non renouvelable s'est produite. Les sous-états suivants sont disponibles :<br /><br /> **Mal configuré**: Une erreur de configuration s’est produite qui nécessite une intervention manuelle.<br /><br /> **Mot de passe requis**: Aucun mot de passe a été défini pour l’Instance Oracle CDC ou le mot de passe n’est pas valide.<br /><br /> **Unexpected**. Toutes les autres erreurs non récupérables.|  
    |![OK](../media/okay.gif "OK")|**En cours d’exécution** : L’Instance de capture de données modifiées s’exécute et traite les enregistrements de modification. Les sous-états suivants sont disponibles.<br /><br /> **Inactivité**: Tous les enregistrements de modification ont été traitées et stockées dans les tables de modifications cible. Il n'y a plus de transactions actives.<br /><br /> **Traitement**: Il existe des enregistrements de modification en cours de traitement qui ne sont pas encore écrits dans les tables de modifications.|  
    |![Arrêter](../media/stop.gif "Arrêter")|**Arrêté** : L'instance CDC n'est pas en cours d'exécution. L'état Stopped indique que l'instance de capture de données modifiées a été arrêtée de manière régulière.|  
    |![Paused](../media/paused.gif "Paused")|**Suspendu**: L’instance de capture de données modifiées s’exécute mais le traitement est interrompu en raison d’une erreur renouvelable. Les sous-états suivants sont disponibles :<br /><br /> **Déconnecté**: Impossible d’établir la connexion à la base de données Oracle source. Le traitement reprend lorsque la connexion est restaurée.<br /><br /> **Stockage**: Le stockage est saturé. Le traitement reprend lorsque le stockage supplémentaire est disponible.<br /><br /> **Enregistreur d’événements**: Le journal est connecté à Oracle mais ne peut pas lire les journaux des transactions Oracle en raison d’un problème temporaire, par exemple, un journal des transactions n’est pas disponible.|  
  
-   **État détaillé**: Le sous-statut actuel.  
  
-   **Message d’état**: Plus d’informations sur l’état actuel.  
  
-   **Horodatage**: L’heure UTC lorsque l’état de capture de données modifiées a été lu à partir de la table d’état.  
  
-   **En cours de traitement**: Vous surveillez les informations suivantes dans cette section.  
  
    -   **Horodatage de la dernière transaction**: L’heure locale de la dernière transaction écrite dans les tables de modifications.  
  
    -   **Horodatage de la dernière modification**: L’heure locale de la modification la plus récente détectée par l’Instance de capture de données modifiées Oracle dans les journaux de transaction de base de données Oracle source. Cela fournit des informations sur la latence actuelle de l'instance de capture de données modifiées lors de la lecture du journal des transactions Oracle.  
  
    -   **Tête de journaux de transaction CN**: Dernier numéro de modification (CN) qui a été lu dans le journal des transactions Oracle.  
  
    -   **La fin du journal de transactions CN**: Numéro de modification pour la récupération ou le redémarrage de l’instance de capture de données modifiées. L'instance Oracle CDC se replacera à cet emplacement en cas de redémarrage ou de tout autre type d'échec (notamment basculement de cluster).  
  
    -   **Current CN**: Le dernier numéro de modification (SCN) vu dans la base de données Oracle source (pas le journal des transactions).  
  
    -   **Transactions actives**: Le nombre actuel de transactions Oracle sources qui sont traités par l’Instance Oracle CDC et ne sont pas encore décidé (validation/restauration).  
  
    -   **Intermédiaire transactions**: Nombre actuel source Oracle de transactions intermédiaires dans le [cdc.xdbcdc_staged_transactions](the-oracle-cdc-databases.md#BKMK_cdcxdbcdc_staged_transactions) table.  
  
-   **Compteurs**: Vous surveillez les informations suivantes dans cette section.  
  
    -   **Transactions terminées**: Le nombre de transactions terminées depuis la dernière réinitialisation de l’instance de capture de données modifiées. Cela n'inclut pas les transactions qui ne contiennent pas les tables d'intérêt.  
  
    -   **Écrit les modifications**: Le nombre de modifications écrites dans le serveur SQL Server des tables de modifications.  
  
 **Oracle**  
 Affiche des informations sur l'instance de capture de données modifiées et sa connexion à la base de données Oracle. Cet onglet est en lecture seule. Pour modifier ces propriétés, cliquez avec le bouton droit sur l’instance dans le volet gauche et sélectionnez **Propriétés** ou cliquez sur **Propriétés** dans le volet droit pour ouvrir la boîte de dialogue Propriétés de \<instance>.  
  
 Pour plus d'informations sur ces propriétés et la façon de les modifier, consultez [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md).  
  
 **Tables**  
 Affiche des informations sur les tables incluses dans l'instance de capture de données modifiées. Les informations de colonne sont également disponibles ici. Cet onglet est en lecture seule. Pour modifier ces propriétés, cliquez avec le bouton droit sur l’instance dans le volet gauche et sélectionnez **Propriétés** ou cliquez sur **Propriétés** dans le volet droit pour ouvrir la boîte de dialogue Propriétés de \<instance>.  
  
 Pour plus d'informations sur ces propriétés et la façon de les modifier, consultez [Edit Tables](edit-tables.md).  
  
 **Avancé**  
 Affiche les propriétés avancées pour l'instance de capture de données modifiées et les valeurs de propriété. Cet onglet est en lecture seule. Pour modifier ces propriétés, cliquez avec le bouton droit sur l’instance dans le volet gauche et sélectionnez **Propriétés** ou cliquez sur **Propriétés** dans le volet droit pour ouvrir la boîte de dialogue Propriétés de \<instance>.  
  
 Pour plus d'informations sur ces propriétés et la façon de les modifier, consultez [Edit the Advanced Properties](edit-the-advanced-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : créer l'instance SQL Server de base de données de modifications](how-to-create-the-sql-server-change-database-instance.md)   
 [Procédure : afficher les propriétés d'une instance de capture de données modifiées](how-to-view-the-cdc-instance-properties.md)   
 [Procédure : modifier les propriétés d'une instance de capture de données modifiées](how-to-edit-the-cdc-instance-properties.md)   
 [Utiliser l'Assistant Nouvelle instance](use-the-new-instance-wizard.md)  
  
  
