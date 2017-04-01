---
title: "Bo&#238;te de dialogue Propri&#233;t&#233;s du dataset, Requ&#234;te (G&#233;n&#233;rateur de rapports) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "10024"
  - "sql13.rtp.rptdesigner.datasetproperties.query.f1"
  - "10160"
ms.assetid: 75432318-0b00-4797-917c-0a2e74f9d951
caps.latest.revision: 12
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 12
---
# Bo&#238;te de dialogue Propri&#233;t&#233;s du dataset, Requ&#234;te (G&#233;n&#233;rateur de rapports)
  Sélectionnez **Requête** dans la boîte de dialogue **Propriétés du dataset** afin de choisir un dataset partagé dans un serveur de rapports ou de créer un dataset incorporé. Dans le cas d'un dataset incorporé, vous devez choisir une source de données et générer une requête.  
  
 La boîte de dialogue **Propriétés du dataset** inclut les éléments suivants :  
  
-   [Boîte de dialogue Propriétés du dataset, Paramètres &#40;Générateur de rapports&#41;](../Topic/Dataset%20Properties%20Dialog%20Box,%20Parameters%20\(Report%20Builder\).md)  
  
-   [Boîte de dialogue Propriétés du dataset, Champs &#40;Générateur de rapports&#41;](../Topic/Dataset%20Properties%20Dialog%20Box,%20Fields%20\(Report%20Builder\).md)  
  
-   [Boîte de dialogue Propriétés du dataset, Options &#40;Générateur de rapports&#41;](../../reporting-services/report-data/dataset-properties-dialog-box-options-report-builder.md)  
  
-   [Boîte de dialogue Propriétés du dataset, Filtres &#40;Générateur de rapports&#41;](../Topic/Dataset%20Properties%20Dialog%20Box,%20Filters%20\(Report%20Builder\).md)  
  
 Pour plus d’informations, consultez [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## Options  
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
 Cette option apparaît quand vous choisissez l’option de type de commande **Texte**. Tapez une requête ou importez-en une existante en cliquant sur **Importer**. Cliquez sur le bouton **Expression** (*fx*) pour modifier l’expression.  
  
> [!NOTE]  
>  Si vous avez utilisé un concepteur de requêtes pour générer une requête, le texte de celle-ci s'affiche dans cette zone.  
  
 **Nom de la table**  
 Entrez le nom de la table que vous souhaitez utiliser comme dataset. Cette option apparaît lorsque vous sélectionnez **Table**.  
  
 **Sélectionnez ou entrez un nom de procédure stockée**  
 Tapez ou choisissez le nom de la procédure stockée que vous souhaitez utiliser. Cliquez sur le bouton **Expression** (*fx*) pour modifier l’expression. Cette option apparaît lorsque vous choisissez l'option de type de commande Procédure stockée.  
  
 **Délai dépassé (en secondes)**  
 Tapez la valeur en secondes du délai d'expiration de la requête. La valeur par défaut est 30 secondes. La valeur de **Délai dépassé** doit être vide ou supérieure à zéro. Si elle ne contient aucune valeur, la requête n'est soumise à aucun délai d'expiration.  
  
 **Actualiser les champs**  
 Exécutez la commande de requête pour mettre à jour la liste de champs dans la page [Boîte de dialogue Propriétés du dataset, Champs](../Topic/Dataset%20Properties%20Dialog%20Box,%20Fields%20\(Report%20Builder\).md).  
  
## Voir aussi  
 [Jeux de données du rapport &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](http://msdn.microsoft.com/fr-fr/2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Concepteurs de requêtes &#40;Générateur de rapports&#41;](../Topic/Query%20Designers%20\(Report%20Builder\).md)  
  
  