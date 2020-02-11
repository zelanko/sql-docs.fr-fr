---
title: 'Leçon 2 : modification des propriétés d’une source de données de rapport | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c962b0ff-ce8a-4742-8262-dc730901afcf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 619d35c084884aa72de63ff221d5a6f61ea86196
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108488"
---
# <a name="lesson-2-modifying-the-report-data-source-properties"></a>Lesson 2: Modifying the Report Data Source Properties
  Dans cette leçon, vous allez utiliser le Gestionnaire de rapports pour sélectionner un rapport qui sera remis à ses destinataires. L’abonnement piloté par les données que vous allez définir distribue le rapport **Sales Order** créé dans le didacticiel [Créer un rapport de tableau de base &#40;Didacticiel SSRS&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md). Au cours des étapes qui suivent, vous allez modifier les informations de connexion à la source de données utilisée par le rapport pour extraire les données. Seuls les rapports qui utilisent des **informations d’identification stockées** pour accéder à une source de données de rapport peuvent être distribués par le biais d’un abonnement piloté par les données. Les informations d'identification stockées sont nécessaires pour traiter les rapports de façon autonome.  
  
 Vous allez également modifier le dataset et le rapport pour qu'ils utilisent un paramètre permettant de filtrer le rapport sur `[Order]` de sorte que l'abonnement puisse générer plusieurs instances différentes du rapport pour des commandes et des formats de rendu spécifiques.  
  
 **Dans cette rubrique :**  
  
-   [Pour modifier les propriétés d'une source de données](#bkmk_modify_datasource)  
  
-   [Pour modifier le AdventureWorksDataset](#bkmk_modify_dataset)  
  
-   [Pour ajouter un paramètre de rapport et republier le rapport](#bkmk_add_reportparameter)  
  
-   [Pour redéployer le rapport](#bkmk_redeploy)  
  
##  <a name="bkmk_modify_datasource"></a>Pour modifier les propriétés de la source de données  
  
1.  Démarrez [Gestionnaire de rapports &#40;&#41;en mode natif SSRS](../../2014/reporting-services/report-manager-ssrs-native-mode.md) avec des privilèges d’administrateur. par exemple, cliquez avec le bouton droit sur l’icône d’Internet Explorer, puis cliquez sur **exécuter en tant qu’administrateur**.  
  
2.  Accédez au dossier contenant le rapport **Sales Orders** et, dans le menu contextuel du rapport, cliquez sur **Gérer**.  
  
     ![Ouvrir le menu contextuel du rapport et sélectionnez gérer](../../2014/tutorials/media/ssrs-tutorial-datadriven-manage-report.gif "Ouvrir le menu contextuel du rapport et sélectionnez gérer")  
  
3.  Cliquez sur l'onglet **Sources de données** .  
  
4.  Pour **type de connexion**, sélectionnez **Microsoft SQL Server**.  
  
5.  La chaîne de connexion à la source de données personnalisée sera la chaîne suivante et l'on suppose que l'exemple de base de données se trouve sur un serveur de base de données local :  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2012  
    ```  
  
6.  Cliquez sur **Informations d'identification stockées en sécurité dans le serveur de rapports**.  
  
7.  Tapez votre nom d’utilisateur (utilisez le format *domaine\utilisateur*) et votre mot de passe. Si vous n'êtes pas autorisé à accéder à la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] , spécifiez une connexion qui rendra cet accès possible.  
  
8.  Cliquez sur **Utiliser comme informations d'identification Windows lors de la connexion à la source de données**, puis cliquez sur **OK**. Si vous n'utilisez pas de compte de domaine (par exemple, si vous utilisez une connexion [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ), n'activez pas cette case à cocher.  
  
9. Cliquez sur **Tester la connexion** pour vous assurer que vous pouvez vous connecter à la source de données.  
  
10. Cliquez sur **Appliquer**.  
  
11. Affichez le rapport pour vérifier qu'il s'exécute avec les informations d'identification que vous avez spécifiées. Pour afficher le rapport, cliquez sur l’onglet **affichage** . Notez qu’une fois le rapport ouvert, vous devez sélectionner un nom d’employé, puis cliquer sur le bouton **afficher le rapport** pour afficher le rapport.  
  
##  <a name="bkmk_modify_dataset"></a>Pour modifier le AdventureWorksDataset  
  
1.  Ouvrez le rapport Sales Orders dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
2.  Cliquez avec le bouton droit sur le dataset `AdventureWorksDataset` et cliquez sur **Propriétés du dataset**.  
  
3.  Ajoutez l'instruction `WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)` avant l'instruction `Group By` . La syntaxe de requête complète est la suivante :  
  
    ```  
    SELECT soh.OrderDate AS Date, soh.SalesOrderNumber AS [Order], pps.Name AS Subcat, pp.Name AS Product, SUM(sd.OrderQty) AS Qty, SUM(sd.LineTotal)  AS LineTotal  
    FROM Sales.SalesPerson AS sp INNER JOIN  
      Sales.SalesOrderHeader AS soh ON sp.BusinessEntityID = soh.SalesPersonID INNER JOIN  
       Sales.SalesOrderDetail AS sd ON sd.SalesOrderID = soh.SalesOrderID INNER JOIN  
       Production.Product AS pp ON sd.ProductID = pp.ProductID  
    INNER JOIN  
       Production.ProductSubcategory AS pps ON pp.ProductSubcategoryID = pps.ProductSubcategoryID   
    INNER JOIN  
        Production.ProductCategory AS ppc ON ppc.ProductCategoryID = pps.ProductCategoryID  
  
    WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)  
  
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name, soh.SalesPersonID  
    HAVING (ppc.Name = 'Clothing')  
    ```  
  
4.  Cliquez sur **OK** .  
  
##  <a name="bkmk_add_reportparameter"></a>Pour ajouter un paramètre de rapport et republier le rapport  
  
1.  Dans le volet des **données de rapport** , cliquez sur **Nouveau** , puis sur **Paramètre...**  
  
2.  Dans **Nom**, tapez `OrderNumber`.  
  
3.  À l' **Invite**, tapez `OrderNumber`.  
  
4.  Sélectionnez **Autoriser une valeur vide ("")**.  
  
5.  Sélectionnez **Autoriser les valeurs de type Null**.  
  
6.  Cliquez sur **OK**. Ce paramètre sera ajouté dans le volet des **données de rapport** et il ressemblera à l'image suivante :  
  
     ![Le nouveau paramètre est ajouté au volet des données de rapport](../../2014/tutorials/media/ssrs-tutorial-datadriven-parameter.gif "Le nouveau paramètre est ajouté au volet des données de rapport")  
  
7.  Cliquez sur l'onglet **Aperçu** pour exécuter le rapport. Notez la zone d'entrée du paramètre en haut du rapport. Vous pouvez :  
  
    -   Cliquez sur Afficher le rapport pour afficher le rapport dans son intégralité sans utiliser de paramètre.  
  
    -   Désélectionnez l'option Null et tapez un numéro de commande, so71949 par exemple, pour afficher uniquement cette commande dans le rapport.  
  
         ![Visionneuse de rapports avec zone de paramètres visible](../../2014/tutorials/media/ssrs-tutorial-datadriven-reportviewer-parameter.gif "Visionneuse de rapports avec zone de paramètres visible")  
  
8.  Redéployez le rapport afin que la configuration de l'abonnement dans la leçon suivante puisse utiliser les modifications que vous avez apportées dans cette leçon. Pour plus d’informations sur les propriétés de projet utilisées dans le tutoriel de table, consultez la section « Pour publier le rapport sur le serveur de rapports (facultatif) » de la [Leçon 6 : ajout d’un regroupement et de totaux &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).  
  
##  <a name="bkmk_redeploy"></a>Pour redéployer le rapport  
  
1.  Redéployez le rapport afin que la configuration de l'abonnement dans la leçon suivante puisse utiliser les modifications que vous avez apportées dans cette leçon. Pour plus d’informations sur les propriétés de projet utilisées dans le tutoriel de table, consultez la section « Pour publier le rapport sur le serveur de rapports (facultatif) » de la [Leçon 6 : ajout d’un regroupement et de totaux &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).  
  
2.  Dans la barre d'outils, cliquez sur **Générer** , puis sur **Déployer le didacticiel**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez correctement configuré le rapport pour extraire les données au moyen des informations d'identification stockées. Vous allez ensuite spécifier l'abonnement en utilisant les pages d'abonnement piloté par les données du Gestionnaire de rapports. Consultez la [Leçon 3 : Définition d’un abonnement piloté par les données](../reporting-services/lesson-3-defining-a-data-driven-subscription.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer des sources de données de rapports](report-data/manage-report-data-sources.md)   
 [Spécifier les informations d’identification et de connexion pour les sources de données de rapport](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Créer un abonnement piloté par les données &#40;didacticiel SSRS&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)   
 [Créer un rapport de tableau de base &#40;Didacticiel SSRS&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  
  
  
