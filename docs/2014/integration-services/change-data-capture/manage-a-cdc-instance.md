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
ms.openlocfilehash: 7f29463784436918834fe94c3ac5e4a8c5420703
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62835601"
---
# <a name="manage-a-cdc-instance"></a>Gérer une instance de capture de données modifiées
  Vous pouvez utiliser la console du concepteur CDC pour afficher des informations sur les instances que vous créez et gérer le fonctionnement des instances.  
  
 Cliquez sur le nom d'une instance dans le volet gauche pour afficher les informations sur l'instance.  
  
> [!NOTE]  
>  Si vous sélectionnez un service dans le volet gauche, la liste des instances disponibles s'affiche également au centre de la console du concepteur CDC. Si vous sélectionnez l'une des instances dans cette section, vous pouvez effectuer les tâches indiquées dans le volet droit ; toutefois, vous ne pourrez pas afficher les informations dans les onglets de propriétés.  
  
## <a name="what-you-can-do-when-you-display-the-cdc-instance-information"></a>Opérations réalisables lorsque vous affichez les informations d'instance CDC  
 Les actions suivantes s'effectuent à partir du volet droit :  
  
 **Start**  
 Cliquez sur **Démarrer** pour démarrer la capture des modifications pour l’instance de capture des données modifiées sélectionnée.  
  
 **Stop**  
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
  
-   **État**: icône indiquant l’état actuel de l’instance de capture de données modifiées. La section suivante décrit les états.  
  
    |||  
    |-|-|  
    |![Error](../media/error.gif "Error")|**Erreur**. L'instance Oracle CDC n'est pas en cours d'exécution, car une erreur non renouvelable s'est produite. Les sous-états suivants sont disponibles :<br /><br /> **Mal configuré**: une erreur de configuration qui nécessite une intervention manuelle s’est produite.<br /><br /> **Mot de passe requis**: aucun mot de passe n’a été défini pour l’instance Oracle CDC ou le mot de passe n’est pas valide.<br /><br /> **Inattendu**. Toutes les autres erreurs non récupérables.|  
    |![OK](../media/okay.gif "OK")|**En cours d’exécution**: l’instance de capture de données modifiées s’exécute et traite les enregistrements de modification. Les sous-états suivants sont disponibles.<br /><br /> **Idle**: tous les enregistrements de modification ont été traités et stockés dans les tables de modifications cibles. Il n'y a plus de transactions actives.<br /><br /> **Traitement**: des enregistrements de modification sont en cours de traitement qui ne sont pas encore écrits dans les tables de modifications.|  
    |![Stop](../media/stop.gif "Arrêter")|**Arrêté**: l’instance de capture de données modifiées n’est pas en cours d’exécution. L'état Stopped indique que l'instance de capture de données modifiées a été arrêtée de manière régulière.|  
    |![Suspendu](../media/paused.gif "Suspendu")|**Paused**: l’instance de capture de données modifiées s’exécute mais le traitement est interrompu en raison d’une erreur renouvelable. Les sous-états suivants sont disponibles :<br /><br /> **Déconnecté**: impossible d’établir la connexion à la base de données Oracle source. Le traitement reprend lorsque la connexion est restaurée.<br /><br /> **Stockage**: le stockage est saturé. Le traitement reprend lorsque le stockage supplémentaire est disponible.<br /><br /> **Logger**: le journal est connecté à Oracle, mais il ne peut pas lire les journaux des transactions Oracle en raison d’un problème temporaire, par exemple, un journal des transactions requis n’est pas disponible.|  
  
-   **État détaillé**: sous-état actuel.  
  
-   **Message d’État**: informations supplémentaires sur l’état actuel.  
  
-   **Timestamp**: heure UTC de la dernière lecture de l’état de capture de données modifiées dans la table d’État.  
  
-   En **cours de traitement**: vous surveillez les informations suivantes dans cette section.  
  
    -   **Horodateur de la dernière transaction**: heure locale de la dernière transaction écrite dans les tables de modifications.  
  
    -   **Horodatage de la dernière modification**: heure locale de la modification la plus récente détectée par l’instance Oracle CDC dans les journaux des transactions de la base de données Oracle source. Cela fournit des informations sur la latence actuelle de l'instance de capture de données modifiées lors de la lecture du journal des transactions Oracle.  
  
    -   Nom du **Journal des transactions : CN**: numéro de modification le plus récent (CN) qui a été lu dans le journal des transactions Oracle.  
  
    -   **Journal des transactions tail CN**: numéro de modification pour la récupération ou le redémarrage de l’instance de capture de données modifiées. L'instance Oracle CDC se replacera à cet emplacement en cas de redémarrage ou de tout autre type d'échec (notamment basculement de cluster).  
  
    -   **CN actuel**: dernier numéro de modification (SCN) vu dans la base de données Oracle source (pas dans le journal des transactions).  
  
    -   **Transactions actives**: nombre actuel de transactions Oracle sources qui sont traitées par l’instance Oracle CDC et qui ne sont pas encore décidées (validation/restauration).  
  
    -   **Transactions intermédiaires**: nombre actuel de transactions Oracle sources intermédiaires dans la table [CDC. xdbcdc_staged_transactions](the-oracle-cdc-databases.md#bkmk_cdcxdbcdc_staged_transactions) .  
  
-   **Compteurs**: vous surveillez les informations suivantes dans cette section.  
  
    -   **Transactions terminées**: nombre de transactions terminées depuis la dernière réinitialisation de l’instance de capture de données modifiées. Cela n'inclut pas les transactions qui ne contiennent pas les tables d'intérêt.  
  
    -   **Modifications écrites**: nombre de modifications écrites dans les tables de modifications de SQL Server.  
  
 **Oracle**  
 Affiche des informations sur l'instance de capture de données modifiées et sa connexion à la base de données Oracle. Cet onglet est en lecture seule. Pour modifier ces propriétés, cliquez avec le bouton droit sur l’instance dans le volet gauche et sélectionnez **Propriétés** ou cliquez sur **Propriétés** dans le volet droit pour ouvrir la boîte de dialogue Propriétés de \<instance>.  
  
 Pour plus d'informations sur ces propriétés et la façon de les modifier, consultez [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md).  
  
 **Tables**  
 Affiche des informations sur les tables incluses dans l'instance de capture de données modifiées. Les informations de colonne sont également disponibles ici. Cet onglet est en lecture seule. Pour modifier ces propriétés, cliquez avec le bouton droit sur l’instance dans le volet gauche et sélectionnez **Propriétés** ou cliquez sur **Propriétés** dans le volet droit pour ouvrir la boîte de dialogue Propriétés de \<instance>.  
  
 Pour plus d'informations sur ces propriétés et la façon de les modifier, consultez [Edit Tables](edit-tables.md).  
  
 **Avancée**  
 Affiche les propriétés avancées pour l'instance de capture de données modifiées et les valeurs de propriété. Cet onglet est en lecture seule. Pour modifier ces propriétés, cliquez avec le bouton droit sur l’instance dans le volet gauche et sélectionnez **Propriétés** ou cliquez sur **Propriétés** dans le volet droit pour ouvrir la boîte de dialogue Propriétés de \<instance>.  
  
 Pour plus d'informations sur ces propriétés et la façon de les modifier, consultez [Edit the Advanced Properties](edit-the-advanced-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : créer l'instance SQL Server de base de données de modifications](how-to-create-the-sql-server-change-database-instance.md)   
 [Comment afficher les propriétés de l’instance CDC](how-to-view-the-cdc-instance-properties.md)   
 [Procédure : modifier les propriétés d'une instance de capture de données modifiées](how-to-edit-the-cdc-instance-properties.md)   
 [Utiliser l’Assistant Nouvelle instance](use-the-new-instance-wizard.md)  
