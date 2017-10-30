---
title: "Sélectionner les Tables sources et des vues (SQL Server Assistant Importation et exportation) | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.selectsourcetablesandviews.f1
ms.assetid: f60e1a19-2ea6-403c-89ab-3e60ac533ea0
caps.latest.revision: 96
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9a0c3c4fc8d41206ea077498dafb755e7b433a78
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="select-source-tables-and-views-sql-server-import-and-export-wizard"></a>Sélectionner les tables et les vues sources (Assistant Importation et Exportation SQL Server)
  Une fois que vous avez indiqué que vous voulez copier la totalité d’une table ou après avoir fourni une requête, l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche la page **Sélectionner les tables et les vues sources**. Dans cette page, vous sélectionnez les tables et les vues existantes à copier. Vous mappez ensuite les tables sources aux tables de destination nouvelles ou existantes. Si vous le souhaitez, vous pouvez aussi passer en revue le mappage des colonnes et afficher un aperçu des exemples de données.

> [!TIP]
> Si vous devez copier plusieurs bases de données SQL Server ou des objets de base de données SQL Server autres que des tables et des vues, utilisez l’Assistant copie de base de données au lieu de l’Assistant Importation et exportation. Pour plus d’informations, consultez [Utiliser l’Assistant Copie de base de données](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="screen-shot---if-youre-going-to-copy-tables"></a>Capture d’écran - si vous souhaitez copier des tables  
 La capture d’écran suivante montre un exemple de la **sélectionner des Tables Source et vues** page de l’Assistant lorsque vous avez sélectionné précédemment le **copier des données d’une ou plusieurs tables ou vues** option sur le **spécifier copie de la Table ou la requête** page. La liste indique toutes les tables et vues disponibles à partir de la source de données.
 
Dans cet exemple, le **Source** liste contient toutes les tables dans la base de données AdventureWorks. La ligne sélectionnée indique que l’utilisateur souhaite copier le **Sales.Customer** table à partir de la source vers la nouvelle **Sales.CustomerNew** table à la destination. 
   
 ![Page Sélectionner les tables de l’Assistant Importation et exportation](../../integration-services/import-export-data/media/select-tables1.png "page Sélectionner les tables de l’Assistant Importation et exportation")
  
## <a name="screen-shot---if-you-provided-a-query"></a>Capture d’écran - si vous avez fourni une requête  
 La capture d’écran suivante montre un exemple de la **sélectionner des Tables Source et vues** page de l’Assistant lorsque vous avez sélectionné précédemment le **écrire une requête pour spécifier les données à transférer** option sur le **spécifier copie de la Table ou la requête** page. Le **Source** liste contient une seule ligne, dans lequel l’élément nommé `[Query]` représente la requête que vous avez indiqué dans le **fournir une requête Source** page.
 
Dans cet exemple, l’utilisateur souhaite copier les résultats de la requête à partir de la source vers la table **Sales.CustomerNew** dans la destination.  
    
 ![Page Sélectionner les tables de l’Assistant Importation et exportation](../../integration-services/import-export-data/media/select-tables2.png "page Sélectionner les tables de l’Assistant Importation et exportation")  

## <a name="select-source-and-destination-tables"></a>Sélectionner des tables sources et de destination 
**Source**  
Activez les cases à cocher pour sélectionner dans la liste les tables et les vues à copier. Par défaut, les données de la source de données sont copiées sans modification. Si vous créez une nouvelle table de destination, le schéma pour la nouvelle table - autrement dit, la liste des colonnes et leurs propriétés - est également copié sans modification de la source de données.

Si vous avez fourni une requête, la liste contient uniquement un élément portant le nom `[Query]`. 

**Destination**  
 Sélectionnez une table de destination dans la liste pour chaque requête ou table source, ou entrez le nom d’une nouvelle table, que l’Assistant créera pour vous. Si vous sélectionnez une table de destination existante, la table doit avoir des colonnes contenant des types de données compatibles avec les données sources.  

> [!NOTE]
> Si vous faites une pause à ce stade de l’Assistant pour créer une table manuellement dans la base de données de destination à l’aide d’un outil externe (tel que  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]), la nouvelle table n’est pas visible immédiatement dans la liste des tables de destination disponibles. Pour actualiser la liste des tables de destination, revenez à la page **Choisir une destination** , resélectionnez la base de données de destination pour actualiser la liste des tables et vues disponibles, puis avancez de nouveau jusqu’à la page **Sélectionner les tables et les vues sources** .  

## <a name="optionally-review-column-mappings-and-preview-data"></a>Si vous le souhaitez, passez en revue les mappages de colonnes et afficher un aperçu des données
**Modifier les mappages**   
Si vous le souhaitez, cliquez sur **modifier les mappages** pour afficher les **mappages de colonnes** boîte de dialogue pour la table sélectionnée. Utilisez la boîte de dialogue **Mappage de colonnes** pour effectuer les opérations suivantes.
-   Passer en revue le mappage des colonnes entre la source et la destination.
-   Vous pouvez copier uniquement un sous-ensemble de colonnes en sélectionnant **ignorer** pour les colonnes que vous souhaitez ignorer.

Pour plus d’informations, consultez [Mappages de colonnes](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).  

**Aperçu**  
Si vous le souhaitez, cliquez sur **aperçu** pour afficher un aperçu jusqu'à 200 lignes de données d’exemple dans le **aperçu des données** boîte de dialogue. Cela confirme que l’Assistant va copier les données que vous souhaitez copier. Pour plus d’informations, consultez [Aperçu des données](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md).  
  
Après avoir affiché un aperçu des données, vous souhaiterez peut-être modifier les options que vous avez sélectionnées dans les pages précédentes de l’Assistant. Pour effectuer ces modifications, retournez dans la page **Sélectionner les tables et les vues sources** , puis cliquez sur **Précédent** pour retourner aux pages précédentes où vous pouvez modifier vos sélections.  

## <a name="select-source-and-destination-tables-for-excel"></a>Sélectionner des tables sources et de destination pour Excel

### <a name="excel-source-tables"></a>Tables sources Excel
La liste des tables et des vues sources d’une source de données Excel comprend deux types d’objets Excel.
-   **Feuilles de calcul**. Les noms de feuille de calcul sont suivis du signe dollar ($) : par exemple, **« Sheet1$ »**.
-   **Plages nommées.** Les plages nommées, le cas échéant, sont répertoriées par nom.

Si vous souhaitez charger des données à partir d’une plage de cellules spécifique, sans nom ou vers celle-ci (par exemple, **[Sheet1$A1:B4]**), vous devez écrire une requête. Retournez dans la page **Spécifier la copie ou l’interrogation de table** et sélectionnez **Écrire une requête pour spécifier les données à transférer**.

#### <a name="prepare-the-excel-source-data"></a>Préparer les données de source Excel
Que vous spécifiez une feuille de calcul ou une plage comme table source, le pilote lit le bloc de cellules *contigu* à partir de la première cellule non vide en haut à gauche de la feuille de calcul ou de la plage. Par conséquent, vous ne pouvez pas avoir de ligne vide dans les données sources. Par exemple, vous ne pouvez pas avoir de ligne vide entre les en-têtes de colonne et les lignes de données. Si un titre est suivi de lignes vides en haut de la feuille de calcul au-dessus de vos données, vous ne pouvez pas interroger la feuille de calcul. Dans Excel, vous devez attribuer un nom à la plage de données et interroger la plage nommée au lieu de la feuille de calcul.

### <a name="excel-destination-tables"></a>Tables de destination Excel
Si vous exportez des données vers Excel, vous pouvez spécifier la destination par l’une des trois méthodes suivantes.
-   **Feuille de calcul.** Pour spécifier une feuille de calcul, ajouter le caractère $ à la fin du nom de la feuille et ajouter des délimiteurs autour de la chaîne. Par exemple, **[Sheet1$]**.
-   **Plage nommée.** Pour spécifier une plage nommée, utilisez simplement le nom de la plage. Par exemple, **MyDataRange**.
-   **Plage sans nom.** Pour spécifier une plage de cellules que vous n’avez pas nommée, ajoutez le caractère $ à la fin du nom de la feuille, ajoutez la spécification de plage ainsi que des délimiteurs autour de la chaîne. Par exemple, **[Sheet1$A1:B4]**.

## <a name="special-considerations-for-excel-sources-and-destinations"></a>Considérations spéciales pour les sources et les destinations Excel
Quand vous utilisez Excel comme source ou destination, cliquez sur **Modifier les mappages** et vérifiez les mappages de types de données dans la page **Mappages de colonnes** . 

**Types de données dans les classeurs Excel**. Excel n’est pas une base de données classique. Ses colonnes n’ont pas de type de données fixe. L’Assistant reconnaît uniquement un ensemble limité de type de données dans Excel : numérique, devise, booléen, date/heure, chaîne (255 caractères maximum) et mémo (plus de 255 caractères). L’Assistant échantillonne un certain nombre de lignes (par défaut, les huit premières lignes) dans une source de données Excel existante afin de déterminer le type de données de chaque colonne.

Quand l’Assistant doit effectuer des conversions explicites de types de données à charger à partir d’Excel ou vers ce dernier, il affiche généralement la page **Vérifier le mappage de type de données** , dans laquelle vous pouvez vérifier ces conversions. Ces conversions peuvent être les suivantes.
-   conversion entre des colonnes numériques Excel à double précision et des colonnes numériques d'autres types.
-   conversion entre des colonnes Excel de type chaîne de 255 caractères et des colonnes de type chaîne de longueurs différentes ;
-   Conversion entre les colonnes de type chaîne Unicode Excel et les colonnes de chaîne non-Unicode qui utilisent des pages de codes spécifiques.

### <a name="special-considerations-for-excel-sources"></a>Considérations spéciales pour les sources Excel
**Valeurs Null ou manquantes dans les données importées**. Lorsqu’une colonne Excel semble contenir des types de données mixtes dans les huit premières lignes échantillonnées par l’Assistant - par exemple, des valeurs numériques mixtes avec des valeurs de texte - l’Assistant sélectionne le type de données majoritaire comme type de données de la colonne et retourne des valeurs null pour les cellules qui contiennent des données d’autres types. Il n’existe aucun moyen de modifier ce comportement de l’Assistant.

**Chaînes tronquées dans les données importées**. Quand l’Assistant détermine qu’une colonne Excel contient des données texte, il choisit le type de données de la colonne (chaîne ou mémo) en fonction de la valeur la plus longue qu’il échantillonne dans les 8 premières lignes. Si l’Assistant ne trouve aucune valeur avec plus de 255 caractères dans les lignes échantillonnées, il traite la colonne comme une colonne de type chaîne à 255 caractères et non comme une colonne de type mémo, et tronque les valeurs de longueur supérieure à 255 caractères. Pour importer des données à partir d’une colonne de type memo sans troncation, vous devez vous assurer que la colonne Mémo contient au moins une valeur supérieure à 255 caractères dans les huit premières lignes échantillonnées par l’Assistant.

### <a name="special-considerations-for-excel-destinations"></a>Considérations spéciales pour les destinations Excel
**Spécification d’une plage de données existante**. Lorsque vous spécifiez une plage existante comme destination, vous obtenez une erreur si la plage comporte moins *colonnes* que les données sources. Toutefois, si la plage que vous spécifiez comporte moins *lignes* que les données sources, l’Assistant continue d’écrire des lignes et étend la définition de la plage pour correspondre au nouveau nombre de lignes.

**Enregistrement des données mémo (ntext)**. Pour pouvoir enregistrer des chaînes de plus de 255 caractères dans une colonne Excel, l’Assistant doit reconnaître le type de données de la colonne de destination comme **mémo** et non comme **chaîne**.
-   Si la table de destination contient déjà des lignes de données, les huit premières lignes échantillonnées par l’Assistant doivent contenir au moins une ligne avec une valeur supérieure à 255 caractères dans la colonne Mémo.
-   Si la table de destination est créée par l’Assistant, le **CREATE TABLE** instruction doit utiliser **LONGTEXT** (ou un de ses synonymes) comme type de données de la la colonne Mémo. Vérifier le **CREATE TABLE** instruction et mettre à jour, si nécessaire, en cliquant sur **Modifier SQL** à côté du **créer la table de destination** option sur le **mappages de colonnes** page.

## <a name="whats-next"></a>Étape suivante  
 Une fois que vous avez sélectionné les tables et vues existantes à copier et que vous les avez mappées à leurs destinations, la page suivante est **Enregistrer et exécuter le package**. Dans cette page, vous spécifiez si vous souhaitez exécuter l’opération de copie immédiatement. Selon votre configuration, vous pouvez également être en mesure d’enregistrer le package [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] créé par l’Assistant pour le personnaliser et le réutiliser ultérieurement. Pour plus d’informations, consultez [Enregistrer et exécuter le package](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).
 
 ## <a name="see-also"></a>Voir aussi
[Bien démarrer avec cet exemple simple de l’Assistant Importation et Exportation](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)



