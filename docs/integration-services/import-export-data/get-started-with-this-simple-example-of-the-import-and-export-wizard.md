---
title: "Prise en main avec cet exemple simple de l’Assistant Importation et exportation | Documents Microsoft"
ms.custom: 
ms.date: 02/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: ea3db39b-698b-4a74-8eb8-21dc7252dc1a
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 59c7e1cc3c31f77652acb21d375e1294bdc93397
ms.openlocfilehash: 9eee58be471d8b39b051c1343f9eb26a2960b6d6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/27/2017

---
# <a name="get-started-with-this-simple-example-of-the-import-and-export-wizard"></a>Prise en main avec cet exemple simple de l’Assistant Importation et exportation
En savoir à quoi s’attendre dans le SQL Server Assistant Importation et exportation en parcourant un scénario courant - importez des données à partir d’une feuille de calcul Excel vers une base de données SQL Server. Même si vous envisagez d’utiliser une autre source et une destination différente, cette rubrique vous montre la plupart de ce que vous devez savoir sur l’exécution de l’Assistant.

## <a name="prerequisite---is-the-wizard-installed-on-your-computer"></a>Condition préalable - correspond à l’Assistant installé sur votre ordinateur ?
Si vous souhaitez exécuter l’Assistant, mais [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas installé sur votre ordinateur, vous pouvez installer l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en installant SSDT (SQL Server Data Tools). Pour plus d’informations, consultez [Télécharger SSDT (SQL Server Data Tools)](https://msdn.microsoft.com/library/mt204009.aspx).

## <a name="heres-the-excel-source-data-for-this-example"></a>Voici les données de la source Excel pour cet exemple
Voici les données source que vous allez copier - une petite table de deux colonnes dans la feuille de calcul WizardWalkthrough du classeur Excel de WizardWalkthrough.xlsx.

![Source de données Excel](../../integration-services/import-export-data/media/excel-source-data.jpg)

## <a name="heres-the-sql-server-destination-database-for-this-example"></a>Voici la base de données de destination SQL Server pour cet exemple
(Dans SQL Server Management Studio) est la base de données de destination SQL Server à laquelle vous souhaitez copier les données source. La table de destination n’est pas il - vous souhaitez laisser l’Assistant créer la table.

![Base de données de destination SQL Server](../../integration-services/import-export-data/media/sql-server-destination-database.jpg)

## <a name="step-1---start-the-wizard"></a>Étape 1 : démarrer l’Assistant
Vous démarrez l’Assistant à partir du groupe Microsoft SQL Server 2016 dans le menu Démarrer de Windows.

![Démarrer l’Assistant](../../integration-services/import-export-data/media/start-wizard.jpg)

> [!NOTE]
> Pour cet exemple, vous pouvez choisir l’Assistant 32 bits, car vous avez la version 32 bits de Microsoft Office est installé. Par conséquent, vous devez utiliser le fournisseur de données 32 bits pour se connecter à Excel. De nombreuses autres sources de données, vous pouvez généralement choisir l’Assistant 64 bits.
>
> Pour utiliser la version 64 bits du SQL Server Assistant Importation et exportation, vous devez installer SQL Server. SQL Server Data Tools (SSDT) et SQL Server Management Studio (SSMS) sont des applications 32 bits et installent uniquement les fichiers de 32 bits, y compris la version 32 bits de l’Assistant.

Pour plus d’informations, consultez [Démarrer l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).

## <a name="step-2---view-the-welcome-page"></a>Étape 2 : afficher la page d’accueil
La première page de l’Assistant est la **Bienvenue** page. 

Vous ne souhaitez probablement voir cette page, par conséquent, continuez et cliquez sur **ne plus afficher cette page de démarrage**.

![Bienvenue dans l’Assistant](../../integration-services/import-export-data/media/welcome-to-the-wizard.jpg)

## <a name="step-3---pick-excel-as-your-data-source"></a>Étape 3 : choix des Excel comme source de données
Sur la page suivante, **choisir une Source de données**, vous choisissez Microsoft Excel comme source de données. Puis vous naviguez pour sélectionner le fichier Excel. Enfin, vous spécifiez la version d’Excel que vous avez utilisé pour créer le fichier.

![Choisissez la source de données Excel](../../integration-services/import-export-data/media/choose-the-excel-data-source.jpg)

Pour plus d’informations sur la connexion à Excel, consultez [se connecter à une Source de données Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md). Pour plus d’informations sur cette page de l’Assistant, consultez [choisir une Source de données](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md).

## <a name="step-4---pick-sql-server-as-your-destination"></a>Étape 4 : choix de SQL Server en tant que destination de votre
Sur la page suivante, **choisir une Destination**, vous choisissez Microsoft SQL Server comme votre destination en choisissant parmi les fournisseurs de données dans la liste qui se connecte à SQL Server. Dans cet exemple, vous choisissez la **.Net Framework Data Provider for SQL Server**.

La page affiche une liste de propriétés du fournisseur. Bon nombre d'entre elles sont des noms hostiles et les paramètres inhabituels. Heureusement, pour vous connecter à une base de données d’entreprise, vous devez généralement fournir uniquement trois éléments d’information. Vous pouvez ignorer les valeurs par défaut pour les autres paramètres.

|Informations nécessaires|.NET framework Data Provider pour la propriété de SQL Server|
|---|---|
|Nom du serveur|**Source de données**|
|Informations d’authentification (connexion)|**La sécurité intégrée de**; ou **ID utilisateur** et **mot de passe**<br/>Si vous souhaitez afficher la liste déroulante des bases de données sur le serveur, vous devez d’abord fournir les informations de connexion valide.|
|Nom de la base de données|**Catalogue initial**|

![Choisissez la destination SQL Server](../../integration-services/import-export-data/media/choose-the-sql-server-destination.jpg)

Pour plus d’informations sur la connexion à SQL Server, consultez [se connecter à une Source de données SQL Server](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md). Pour plus d’informations sur cette page de l’Assistant, consultez [choisir une Destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md).

## <a name="step-5---copy-a-table-instead-of-writing-a-query"></a>Étape 5 - copie une table au lieu d’écrire une requête
Sur la page suivante, **spécifier copie de la Table ou requête**, vous spécifiez que vous souhaitez copier la table entière de source de données. Vous ne souhaitez pas écrire une requête en langage SQL pour sélectionner les données à copier.

![Spécifiez pour copier une table](../../integration-services/import-export-data/media/specify-to-copy-a-table.jpg)

Pour plus d’informations sur cette page de l’Assistant, consultez [spécifier copie de la Table ou requête](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md).

## <a name="step-6---pick-the-table-to-copy"></a>Étape 6 - choisir la table à copier
Sur la page suivante, **sélectionner des Tables Source et vues**, vous choisissez les tables que vous souhaitez copier à partir de la source de données. Puis vous mappez chaque table source sélectionnée dans une table de destination de nouveau ou existant.

Dans cet exemple, par défaut l’Assistant a mappé le **WizardWalkthrough$** feuille de calcul dans le **Source** colonne vers une nouvelle table portant le même nom à la destination SQL Server. (Le classeur Excel contient uniquement une feuille de calcul.)
-   Le symbole dollar ($) sur le nom de la table source indique une feuille de calcul Excel. (Une plage dans Excel nommé est représenté par son seul nom.)
-   L’étoile sur l’icône de table de destination indique que l’Assistant va créer une nouvelle table de destination.

![Sélectionnez la table (avant le changement de nom)](../../integration-services/import-export-data/media/select-the-table-before-renaming.jpg)

Vous souhaiterez probablement supprimer le signe dollar ($) à partir du nom de la nouvelle table de destination.

![Sélectionnez la table (après modification du nom)](../../integration-services/import-export-data/media/select-the-table-after-renaming.jpg)

Pour plus d’informations sur cette page de l’Assistant, consultez [sélectionner des Tables Source et vues](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md).

## <a name="optional-step-7---review-the-column-mappings"></a>Étape facultative 7 : passez en revue les mappages de colonnes
Avant de quitter la **sélectionner des Tables Source et vues** page, cliquez éventuellement sur le **modifier les mappages** bouton pour ouvrir la **mappages de colonnes** boîte de dialogue. Ici, dans le **mappages** table, vous voyez comment l’Assistant va pour mapper les colonnes dans la feuille de calcul source aux colonnes dans la nouvelle table de destination.

![Mappages de colonnes de vue](../../integration-services/import-export-data/media/view-column-mappings.jpg)

Pour plus d’informations sur cette page de l’Assistant, consultez [mappages de colonnes](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).

## <a name="optional-step-8---review-the-create-table-statement"></a>Étape facultative 8 : passez en revue l’instruction CREATE TABLE
Alors que le **mappages de colonnes** boîte de dialogue est ouverte, cliquez éventuellement sur le **Modifier SQL** bouton pour ouvrir la **Create Table SQL Statement** boîte de dialogue. Vous trouverez le **CREATE TABLE** instruction générée par l’Assistant pour créer la nouvelle table de destination. En général, vous n’êtes pas obligé de modifier l’instruction.

![Afficher l’instruction CREATE TABLE](../../integration-services/import-export-data/media/view-create-table-statement.jpg)

Pour plus d’informations sur cette page de l’Assistant, consultez [Create Table SQL Statement](../../integration-services/import-export-data/create-table-sql-statement-sql-server-import-and-export-wizard.md).

## <a name="optional-step-9---preview-the-data-to-copy"></a>Étape facultative 9 - définir les données à copier
Après avoir cliqué sur **OK** pour fermer la **Create Table SQL Statement** boîte de dialogue zone, puis cliquez sur **OK** à nouveau pour fermer la **mappages de colonnes** boîte de dialogue, vous êtes sur le **sélectionner des Tables Source et vues** page. Cliquez éventuellement sur le **aperçu** bouton pour voir un exemple des données qui le l’Assistant va copier. Dans cet exemple, il semble OK.

![Aperçu des données à copier](../../integration-services/import-export-data/media/preview-data-to-copy.jpg)

Pour plus d’informations sur cette page de l’Assistant, consultez [aperçu des données](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md).

## <a name="step-10---yes-you-want-to-run-the-import-export-operation"></a>Étape 10 : Oui, vous souhaitez exécuter l’opération d’importation / exportation
Sur la page suivante, **enregistrer et exécuter le Package**, vous conservez **exécuter immédiatement** activé pour copier les données dès que vous cliquez sur **Terminer** sur la page suivante. Ou vous pouvez ignorer la page suivante en cliquant sur **Terminer** sur la **enregistrer et exécuter le Package** page.

![Exécuter le package](../../integration-services/import-export-data/media/run-the-package.jpg)

Pour plus d’informations sur cette page de l’Assistant, consultez [enregistrer et exécuter le Package](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).

## <a name="step-11---finish-the-wizard-and-run-the-import-export-operation"></a>Étape 11 : terminer l’Assistant et exécutez l’opération d’importation / exportation
Si vous avez cliqué sur **suivant** au lieu de **Terminer** sur la **enregistrer et exécuter le Package** page, puis sur la page suivante, **terminer l’Assistant**, vous voyez un résumé de ce que l’Assistant va effectuer. Cliquez sur **Terminer** pour exécuter l’opération d’importation / exportation.

![Terminer l’Assistant](../../integration-services/import-export-data/media/complete-the-wizard.jpg)

Pour plus d’informations sur cette page de l’Assistant, consultez [terminer l’Assistant](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md).

## <a name="step-12---review-what-the-wizard-did"></a>Étape 12 : examinez ce que fait l’Assistant
Dans la page finale, observer lors de chaque tâche a terminé l’Assistant, puis passez en revue les résultats. La ligne en surbrillance indique que l’Assistant a copié vos données avec succès. Vous avez terminé !

![L’Assistant a réussi](../../integration-services/import-export-data/media/the-wizard-succeeded.jpg)

Pour plus d’informations sur cette page de l’Assistant, consultez [exécution de l’opération](../../integration-services/import-export-data/performing-operation-sql-server-import-and-export-wizard.md).

## <a name="heres-the-new-table-of-data-copied-to-sql-server"></a>Voici la nouvelle table de données copiée dans SQL Server
(Dans SQL Server Management Studio) vous trouverez la nouvelle table de destination créé par l’Assistant dans SQL Server.

![Données copiées vers SQL Server](../../integration-services/import-export-data/media/data-copied-to-sql-server.jpg)

(Dans SSMS) vous trouverez les données copié de l’Assistant dans SQL Server.

![Données copiées vers SQL Server 2](../../integration-services/import-export-data/media/data-copied-to-sql-server-2.jpg)

## <a name="learn-more"></a>En savoir plus  
En savoir plus sur le fonctionne de l’Assistant.
-   **En savoir plus sur l’Assistant.** Si vous recherchez une vue d’ensemble de l’Assistant, consultez [Importer et exporter des données avec l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

-   **En savoir plus sur les étapes de l’Assistant.** Si vous recherchez des informations sur les étapes de l’Assistant, sélectionnez la page à partir de la liste ici - [les étapes dans le SQL Server Assistant Importation et exportation](../../integration-services/import-export-data/steps-in-the-sql-server-import-and-export-wizard.md). Il existe également une page distincte de la documentation pour chaque page de l’Assistant.

-   **Découvrez comment se connecter à des destinations et des sources de données.** Si vous recherchez des informations sur la façon de se connecter à vos données, sélectionnez la page à partir de la liste ici - [se connecter aux sources de données avec le SQL Server Assistant Importation et exportation](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md). Il existe une page distincte de la documentation pour chacun de plusieurs sources de données couramment utilisées.



