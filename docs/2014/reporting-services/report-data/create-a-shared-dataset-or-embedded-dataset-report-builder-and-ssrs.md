---
title: Créer un dataset partagé ou incorporé (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: d1d7bc71-f0e9-4ce5-b3ad-6fee54388a31
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dc91e50c96018e14066f6e6cc0ad4625c128b639
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62697498"
---
# <a name="create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs"></a>Créer un dataset partagé ou incorporé (Générateur de rapports et SSRS)
  Vous pouvez créer un dataset incorporé pour une utilisation dans un rapport unique ou un dataset partagé à enregistrer sur un serveur de rapports, en vue d'une utilisation par plusieurs rapports. Pour créer un dataset, vous devez disposer d'une source de données incorporée ou partagée.  
  
 Utilisez le Générateur de rapports pour effectuer les tâches suivantes :  
  
-   Créez un dataset partagé en mode création de dataset. Les datasets partagés doivent utiliser des sources de données partagées publiées.  
  
-   Créez un dataset incorporé en mode création de rapport.  
  
-   Enregistrez le dataset directement sur le serveur de rapports ou le site SharePoint.  
  
 Utilisez le Concepteur de rapports dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour effectuer les tâches suivantes :  
  
1.  Créez un dataset partagé dans l'Explorateur de solutions. Les datasets partagés doivent utiliser les sources de données du dossier Sources de données partagées dans l'Explorateur de solutions.  
  
2.  Créez un dataset incorporé dans le volet des données de rapport.  
  
3.  Éventuellement déployez des datasets partagés et la source de données partagées avec le rapport. Pour chaque type d'élément, utilisez les propriétés du projet pour spécifier les chemins d'accès aux dossiers sur le serveur de rapports ou le site SharePoint.  
  
 Pour plus d’informations, consultez [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-open-report-builder-and-create-a-shared-dataset"></a>Pour ouvrir le Générateur de rapports et créer un dataset partagé  
  
1.  Ouvrez le Générateur de rapports. Le volet **Nouveau rapport ou dataset** s'ouvre, comme indiqué dans l'illustration suivante :  
  
     ![rs_NewSharedDataset](../media/rs-newshareddataset.gif "rs_NewSharedDataset")  
  
    > [!NOTE]  
    >  Si le volet **Nouveau rapport ou dataset** ne s’affiche pas, à partir du bouton Générateur de rapports, cliquez sur **Nouveau**.  
  
2.  Dans le volet gauche, sous **Créer un dataset**, cliquez sur **Dataset partagé**.  
  
3.  Dans le volet droit, cliquez sur **Parcourir** pour sélectionner une source de données partagée sur le serveur de rapports, puis cliquez sur **Créer**. Le concepteur de requêtes associé à la source de données partagée s'ouvre.  
  
4.  Dans le Concepteur de requêtes, spécifiez les champs à inclure au dataset.  
  
5.  Cliquez sur **Exécuter** (**!**) pour exécuter la requête.  
  
6.  Sur le bouton **Générateur de rapports** , cliquez sur **Enregistrer** ou **Enregistrer sous** pour enregistrer le dataset partagé sur le serveur de rapports.  
  
7.  Pour quitter le Générateur de rapports, cliquez sur **Générateur de rapports**, puis sur **Quitter le Générateur de rapports**. Pour utiliser des rapports, cliquez sur **Générateur de rapports**, puis sur **Nouveau** ou **Ouvrir**.  
  
### <a name="to-set-query-parameter-options"></a>Pour définir des options de paramètre de requête  
  
1.  Ouvrez le Générateur de rapports.  
  
2.  Cliquez sur **Ouvrir**.  
  
3.  Accédez au serveur de rapports et sélectionnez le dossier pour la source de données partagée.  
  
4.  Dans **Éléments de type**, cliquez sur Datasets (*.rsd) dans la liste déroulante.  
  
5.  Sélectionnez le dataset partagé, puis cliquez sur **Ouvrir**. Le concepteur de requêtes associé s'ouvre.  
  
6.  Sur le ruban, cliquez sur **Propriétés du dataset**.  
  
7.  Cliquez sur **Paramètres**. Dans cette page, définissez une valeur par défaut sur une constante ou une expression, marquez le paramètre en lecture seule, nullable ou **Omettre de la requête**. Pour plus d’informations, consultez [Boîte de dialogue Propriétés du dataset, Paramètres &#40;Générateur de rapports&#41;](../dataset-properties-dialog-box-parameters-report-builder.md).  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
### <a name="to-create-a-dataset-from-a-sql-server-relational-database"></a>Pour créer un dataset à partir d'une base de données relationnelle SQL Server  
  
1.  Dans le volet Données du rapport, cliquez avec le bouton droit sur le nom de la source de données, puis cliquez sur **Ajouter un dataset**. La page **Requête** de la boîte de dialogue **Propriétés du dataset** s'ouvre.  
  
2.  Dans **Nom**, tapez un nom pour le dataset ou acceptez le nom par défaut.  
  
    > [!NOTE]  
    >  Le nom du dataset est utilisé en interne dans le rapport. Par souci de clarté, il est recommandé d'utiliser un nom de dataset qui décrit les données retournées par la requête.  
  
3.  Dans **Source de données**, recherchez et sélectionnez le nom d'une source de données partagée existante ou cliquez sur **Nouveau** pour créer une source de données incorporée.  
  
4.  Sélectionnez une option pour le **Type de requête** . Les options disponibles dépendent du type de source de données.  
  
    -   Sélectionnez **Texte** pour rédiger une requête adoptant le langage de requête de la source de données.  
  
    -   Sélectionnez **Table** pour retourner tous les champs dans une table de base de données relationnelle.  
  
    -   Sélectionnez **StoredProcedure** pour exécuter une procédure stockée par nom.  
  
5.  Dans la zone **Requête**, tapez le nom de la requête, de la procédure stockée ou de la table. Vous pouvez aussi cliquer sur **Concepteur de requêtes** pour ouvrir le concepteur de requêtes graphique ou textuel, ou sur **Importer** pour importer la requête depuis un rapport existant.  
  
     Dans certains cas, la collection de champs spécifiée par la requête ne peut être déterminée qu'en exécutant la requête sur la source de données. Par exemple, une procédure stockée peut retourner un jeu variable de champs dans le jeu de résultats. Cliquez sur **Actualiser les champs** pour exécuter la requête sur la source de données et récupérer les noms de champs qui sont requis pour remplir la collection de champs de dataset dans le volet des données de rapport. La collection de champs s'affiche sous le nœud de dataset une fois que vous avez fermé la boîte de dialogue **Propriétés du dataset** .  
  
6.  Dans la zone **Délai d'expiration**, tapez le nombre de secondes pendant lequel le serveur de rapports attend une réponse de la base de données. La valeur par défaut est 0 seconde. Lorsque la valeur du délai d'expiration est de 0 secondes, la requête n'expire pas.  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Le dataset et sa collection de champs s'affichent dans le volet des données de rapport sous le nœud de source de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)   
 [Concepteurs de requêtes &#40;Générateur de rapports&#41;](../query-designers-report-builder.md)   
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-datasets-ssrs.md)   
 [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../data-connections-data-sources-and-connection-strings-in-report-builder.md)   
 [Datasets incorporés et partagés &#40;Générateur de rapports et SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
