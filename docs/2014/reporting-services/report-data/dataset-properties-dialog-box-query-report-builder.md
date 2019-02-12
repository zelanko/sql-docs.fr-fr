---
title: Boîte de dialogue Propriétés du dataset, Requête (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10024"
ms.assetid: 75432318-0b00-4797-917c-0a2e74f9d951
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: bc761a1d54108818142c075ff3cceadc8875cc9c
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56038430"
---
# <a name="dataset-properties-dialog-box-query-report-builder"></a>Boîte de dialogue Propriétés du dataset, Requête (Générateur de rapports)
  Sélectionnez **Requête** dans la boîte de dialogue **Propriétés du dataset** afin de choisir un dataset partagé dans un serveur de rapports ou de créer un dataset incorporé. Dans le cas d'un dataset incorporé, vous devez choisir une source de données et générer une requête.  
  
 La boîte de dialogue **Propriétés du dataset** inclut les éléments suivants :  
  
-   [Boîte de dialogue Propriétés du dataset, Paramètres &#40;Générateur de rapports&#41;](../dataset-properties-dialog-box-parameters-report-builder.md)  
  
-   [Boîte de dialogue Propriétés du dataset, Champs &#40;Générateur de rapports&#41;](../dataset-properties-dialog-box-fields-report-builder.md)  
  
-   [Boîte de dialogue Propriétés du dataset, Options &#40;Générateur de rapports&#41;](dataset-properties-dialog-box-options-report-builder.md)  
  
-   [Boîte de dialogue Propriétés du dataset, Filtres &#40;Générateur de rapports&#41;](../dataset-properties-dialog-box-filters-report-builder.md)  
  
 Pour plus d’informations, consultez [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Options  
 **Nom**  
 Tapez le nom du dataset. Ce nom doit être différent de celui des régions ou des groupes de données du rapport.  
  
 **Utiliser un dataset partagé**  
 Sélectionnez cette option pour utiliser un dataset prédéfini du serveur de rapports.  
  
 **Parcourir**  
 Recherchez un dossier sur un serveur de rapports ou un site SharePoint, puis sélectionnez un dataset partagé (.rsd).  
  
 **Utiliser un dataset incorporé dans mon rapport**  
 Sélectionnez cette option pour créer un dataset à utiliser uniquement par ce rapport.  
  
 **Source de données**  
 Sélectionnez la source de données sur laquelle baser le dataset. Cliquez sur **Nouvelle**pour créer une nouvelle source de données.  
  
 **Type de requête**  
 Sélectionnez le type de commande ou de requête à utiliser pour le dataset. Sélectionnez **Texte** pour exécuter une requête afin d'extraire des données de la base de données. Sélectionnez **Table** pour utiliser la fonctionnalité **TableDirect** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de sélectionner tous les champs d'une table. Sélectionnez **Procédure stockée** pour exécuter une procédure stockée par nom. **Texte** est sélectionné par défaut et est utilisé pour la plupart des requêtes. Pour modifier la requête de source de données sélectionnée, cliquez sur **Concepteur de requêtes**.  
  
> [!NOTE]  
>  Les types de requêtes ne sont pas tous pris en charge par toutes les sources de données. Par exemple, le type **Table** n'est pris en charge que par les types de sources de données **OLE DB** et **ODBC**.  
  
 **Requête**  
 Cette option apparaît quand vous choisissez l’option de type de commande **Texte** . Tapez une requête ou importez-en une existante en cliquant sur **Importer**. Cliquez sur le bouton **Expression** (*fx*) pour modifier l’expression.  
  
> [!NOTE]  
>  Si vous avez utilisé un concepteur de requêtes pour générer une requête, le texte de celle-ci s'affiche dans cette zone.  
  
 **Nom de la table**  
 Entrez le nom de la table que vous souhaitez utiliser comme dataset. Cette option apparaît lorsque vous sélectionnez **Table**.  
  
 **Sélectionnez ou entrez un nom de procédure stockée**  
 Tapez ou choisissez le nom de la procédure stockée que vous souhaitez utiliser. Cliquez sur le bouton **Expression** (*fx*) pour modifier l’expression. Cette option apparaît lorsque vous choisissez l'option de type de commande Procédure stockée.  
  
 **Délai dépassé (en secondes)**  
 Tapez la valeur en secondes du délai d'expiration de la requête. La valeur par défaut est 30 secondes. La valeur de **Délai dépassé** doit être vide ou supérieure à zéro. Si elle ne contient aucune valeur, la requête n'est soumise à aucun délai d'expiration.  
  
 **Actualiser les champs**  
 Exécutez la commande de requête pour mettre à jour la liste de champs dans la page [Boîte de dialogue Propriétés du dataset, Champs](../dataset-properties-dialog-box-fields-report-builder.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-datasets-ssrs.md)   
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Concepteurs de requêtes &#40;Générateur de rapports&#41;](../query-designers-report-builder.md)  
  
  
