---
title: 'Leçon 2 : Ajouter des données | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 13c3a8cc-b1db-4aba-ad9b-038b7971be8d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 370e368843fa1e9584cc341397853fcdad26922a
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66078973"
---
# <a name="lesson-2-add-data"></a>Leçon 2 : Ajouter des données
  Dans cette leçon, vous allez utiliser l'Assistant Importation de table dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] pour vous connecter à la base de données SQL AdventureWorksDW, sélectionner des données, afficher un aperçu et filtrer les données, puis les importer dans votre espace de travail de modèle.  
  
 À l’aide de l’Assistant Importation de Table, vous pouvez importer des données à partir de diverses sources relationnelles : Access, SQL, Oracle, Sybase, Informix, DB2, Teradata et bien plus encore. Les étapes d'importation de données à partir des différentes sources relationnelles sont très semblables à celles qui suivent. En outre, les données peuvent être sélectionnées à l'aide d'une procédure stockée.  
  
 Pour en savoir plus sur l’importation de données et les différents types de sources de données que vous pouvez importer, consultez [Sources de données &#40;SSAS Tabulaire&#41;](data-sources-ssas-tabular.md).  
  
 Durée estimée pour effectuer cette leçon : **20 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 1 : Créez un projet de modèle tabulaire](lesson-1-create-a-new-tabular-model-project.md).  
  
## <a name="create-a-connection"></a>Créer une connexion  
  
#### <a name="to-create-a-connection-to-a-the-adventureworksdw2012-database"></a>Pour créer une connexion à la base de données AdventureWorksDW2012  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Importer à partir de la source de données**.  
  
     Cela lance l'Assistant Importation de table qui vous guide à travers les étapes de configuration d'une connexion à une source de données. Si l'option **Importer à partir de la source de données** est grisée, double-cliquez sur **Model.bim** dans l' **Explorateur de solutions** pour ouvrir le modèle dans le concepteur.  
  
2.  Dans l' **Assistant Importation de table**, sous **Bases de données relationnelles**, cliquez sur **Microsoft SQL Server**, puis cliquez sur **Suivant**.  
  
3.  Dans le **se connecter à une base de données Microsoft SQL Server** page **nom convivial de la connexion**, type `Adventure Works DB from SQL`.  
  
4.  Dans la zone **Nom du serveur**, tapez ou sélectionnez le nom du serveur sur lequel vous avez installé la base de données AdventureWorksDW.  
  
5.  Dans le champ **Nom de la base de données** , cliquez sur la flèche orientée vers le bas et sélectionnez **AdventureWorksDW**, puis cliquez sur **Suivant**.  
  
6.  Dans la page **Informations d'emprunt d'identité** , vous devez spécifier les informations d'identification qu'Analysis Services utilisera pour se connecter à la source de données lors de l'importation et du traitement des données. Vérifiez que l'option **Nom d'utilisateur et mot de passe Windows spécifiques** est sélectionnée, puis, dans **Nom d'utilisateur** et **Mot de passe**, entrez vos informations d'identification de connexion Windows, puis cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  L'utilisation d'un compte d'utilisateur et d'un mot de passe Windows est la méthode la plus sûre pour se connecter à une source de données. Pour plus d’informations, consultez [Emprunt d’identité &#40;SSAS Tabulaire&#41;](tabular-models/impersonation-ssas-tabular.md).  
  
7.  Dans la page **Choisir comment importer les données** , vérifiez que l'option **Sélectionner les données à importer dans une liste de tables et de vues** est sélectionnée. Vous souhaitez choisir dans une liste de tables et de vues et vous devez donc cliquer sur **Suivant** pour afficher la liste de toutes les tables sources dans la base de données source.  
  
8.  Dans le **sélectionner des Tables et vues** , sélectionnez la case à cocher pour les tables suivantes : **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**,  **DimProductSubcategory**, et **FactInternetSales**.  
  
9. Nous souhaitons donner aux tables du modèle des noms plus facilement compréhensibles. Cliquez sur la cellule dans la colonne **Nom convivial** pour **DimCustomer**. Renommer la table en supprimant « Dim » de DimCustomer.  
  
10. Renommez les autres tables :  
  
    |Nom de la source|Nom convivial|  
    |-----------------|-------------------|  
    |DimDate|Date|  
    |DimGeography|Géographie|  
    |DimProduct|Produit|  
    |DimProductCategory|Catégorie de produit|  
    |DimProductSubcategory|Product Subcategory|  
    |FactInternetSales|Internet Sales|  
  
     **NE CLIQUEZ PAS** sur **Terminer**.  
  
 Maintenant que vous êtes connecté à la base de données, que vous avez sélectionné les tables à importer et que vous leur avez attribué un nom convivial, passez directement à la section suivante intitulée [Filtrer les données de table avant l'importation](#FilterData).  
  
##  <a name="FilterData"></a> Filtrer les données de Table  
 La table DimCustomer que vous importez de la base de données contient un sous-ensemble des données de la base de données d'origine SQL Server Adventure Works. Vous allez filtrer certaines colonnes de la table DimCustomer qui ne sont pas nécessaires. Lorsque cela est possible, filtrez les données qui ne seront pas utilisées afin d'économiser l'espace en mémoire utilisé par le modèle.  
  
#### <a name="to-filter-the-table-data-prior-to-importing"></a>Pour filtrer les données de table avant l'importation  
  
1.  Sélectionnez la ligne correspondant à la table **Customer**, puis cliquez sur **Afficher un aperçu et filtrer**. La fenêtre **Aperçu de la table sélectionnée** s'affiche en présentant toutes les colonnes de la table source DimCustomer.  
  
2.  Désactivez la case à cocher en haut des colonnes suivantes :  
  
    |Customer|  
    |--------------|  
    |**SpanishEducation**|  
    |**FrenchEducation**|  
    |**SpanishOccupation**|  
    |**FrenchOccupation**|  
  
     Étant donné que les valeurs de ces colonnes ne sont pas appropriées à l'analyse des ventes sur Internet, il est inutile de les importer. Éliminer les colonnes inutiles réduira la taille de votre modèle.  
  
3.  Vérifiez que toutes les autres colonnes sont cochées, puis cliquez sur **OK**.  
  
     Remarquez que les mots **filtres appliqués** s’affichent maintenant dans le **détails du filtre** colonne dans le **client** ligne ; si vous cliquez sur ce lien vous verrez une description textuelle de la vous venez d’appliquer des filtres.  
  
4.  Filtrez les autres tables en désactivant les cases à cocher des colonnes suivantes dans chaque table :  
  
    |Date|  
    |----------|  
    |**DateKey**|  
    |**SpanishDayNameOfWeek**|  
    |**FrenchDayNameOfWeek**|  
    |**SpanishMonthName**|  
    |**FrenchMonthName**|  
  
    |Géographie|  
    |---------------|  
    |**SpanishCountryRegionName**|  
    |**FrenchCountryRegionName**|  
    |**IpAddressLocator**|  
  
    |Produit|  
    |-------------|  
    |**SpanishProductName**|  
    |**FrenchProductName**|  
    |**FrenchDescription**|  
    |**ChineseDescription**|  
    |**ArabicDescription**|  
    |**HebrewDescription**|  
    |**ThaiDescription**|  
    |**GermanDescription**|  
    |**JapaneseDescription**|  
    |**TurkishDescription**|  
  
    |Catégorie de produit|  
    |----------------------|  
    |**SpanishProductCategoryName**|  
    |**FrenchProductCategoryName**|  
  
    |Product Subcategory|  
    |-------------------------|  
    |**SpanishProductSubcategoryName**|  
    |**FrenchProductSubcategoryName**|  
  
    |Internet Sales|  
    |--------------------|  
    |**OrderDateKey**|  
    |**DueDateKey**|  
    |**ShipDateKey**|  
  
 Maintenant que vous avez prévisualisé et filtré les données inutiles, vous pouvez importer les données. Allez à la section suivante **Importer les tables et les données de colonne sélectionnées**.  
  
##  <a name="Import"></a> Importer les Tables sélectionnées et les données de la colonne  
 Vous pouvez maintenant importer les données sélectionnées. L'Assistant importe les données de la table avec toutes les relations entre les tables. De nouvelles tables et colonnes sont créées dans le modèle en utilisant les noms conviviaux spécifiés, et les données filtrées ne seront pas importées.  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a>Pour importer les tables sélectionnées et les données de colonne  
  
1.  Vérifiez vos sélections. Si tout semble OK, cliquez sur **Terminer**.  
  
     Pendant l'importation des données, l'Assistant affiche le nombre de lignes qui ont été extraites. Lorsque toutes les données ont été importées, un message de réussite s'affiche.  
  
    > [!TIP]  
    >  Pour afficher les relations qui ont été créées automatiquement entre les tables importées, sur la ligne **Préparation des données** , cliquez sur **Détails**.  
  
2.  Cliquez sur **Fermer**.  
  
     L'Assistant se ferme et le concepteur de modèles est visible. Chaque table a été ajoutée en tant que nouvel onglet du concepteur de modèles.  
  
## <a name="save-the-model-project"></a>Enregistrer le projet de modèle  
 Il est important de sauvegarder fréquemment votre projet de modèle.  
  
#### <a name="to-save-the-model-project"></a>Pour enregistrer le projet de modèle  
  
-   Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Fichier** , puis cliquez sur **Enregistrer tout**.  
  
## <a name="next-step"></a>Étape suivante  
 Pour continuer ce didacticiel, passez à la leçon suivante : [Leçon 3 : Renommer des colonnes](rename-columns.md).  
  
  
