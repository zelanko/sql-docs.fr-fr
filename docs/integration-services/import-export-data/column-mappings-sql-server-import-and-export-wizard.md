---
title: "Mappage de colonnes (Assistant Importation et exportation SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.columnmapandtransform.f1"
ms.assetid: eadc54a6-f936-4ffc-91d7-fbfd2bdcab93
caps.latest.revision: 69
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 58
---
# Mappage de colonnes (Assistant Importation et exportation SQL Server)
  Une fois que vous avez sélectionné les tables et vues existantes pour copier ou vérifier la requête que vous avez fournie, l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche la boîte de dialogue **Mappage de colonnes** si vous cliquez sur **Modifier les mappages**. Dans cette page, vous spécifiez et configurez des colonnes de destination pour recevoir les données copiées.  
 
## <a name="screen-shot-of-the-column-mappings-page"></a>Capture d’écran de la page Mappages de colonnes 
 La capture d’écran suivante montre la boîte de dialogue **Mappage de colonnes** de l’Assistant. 
 
 Dans cet exemple, vous voyez que l’Assistant va créer une table de destination, car **Créer la table de destination** est sélectionnée. Par défaut, chaque colonne de la nouvelle table de destination a le même nom, le même type de données et les mêmes propriétés que la colonne source correspondante. 
  
 ![Column mappings page of the Import and Export Wizard](../../integration-services/import-export-data/media/column-mappings.png "Column mappings page of the Import and Export Wizard")  
  
## <a name="confirm-the-source-and-destination"></a>Confirmer la source et la destination  
 **Source**  
 Identifie la table, la vue ou la requête source sélectionnée.  
  
 **Destination**  
 Identifie la table ou vue de destination sélectionnée.  

## <a name="create-a-new-destination-table"></a>Créer une table de destination
 **Créer la table/le fichier de destination**  
 Créez la table de destination si elle n’existe pas encore.    
  
 **Modifier SQL**  
Cliquez sur **Modifier SQL** pour ouvrir la boîte de dialogue **Instruction SQL de création de table**. Utilisez l’instruction CREATE TABLE par défaut ou modifiez-la en fonction de vos besoins. Si vous modifiez manuellement cette instruction, vous devez vérifier que la liste des mappages de colonnes reconnaît vos modifications. Pour plus d’informations, consultez [Instruction SQL Create Table](../../integration-services/import-export-data/create-table-sql-statement-sql-server-import-and-export-wizard.md).  
  
 > [!TIP] Si vous avez spécifié une nouvelle table de destination dans la page **Sélectionner les tables et les vues sources**, l’option **Créer la table de destination** est automatiquement sélectionnée et le bouton **Modifier SQL** est activé. Sinon, pour créer la table de destination, vous devez revenir à la page **Sélectionner les tables et les vues sources** et entrer le nom d’une **nouvelle** table dans la colonne **Destination**.
>
> Si l’option **Créer la table de destination** et le bouton **Modifier SQL** sont désactivés dans la page **Mappage de colonnes**, revenez à la page **Sélectionner les tables et les vues sources** et entrez le nom d’une **nouvelle** table dans la colonne **Destination**. Une fois que vous avez spécifié une ou plusieurs nouvelles tables de destination, cliquez sur **Suivant**. L’option **Créer la table de destination** est alors automatiquement sélectionnée et le bouton **Modifier SQL** est activé dans la page **Mappage de colonnes**. Sélectionnez **Modifier SQL** pour afficher la boîte de dialogue **Instruction SQL de création de table**.  

## <a name="specify-options-for-existing-data-in-the-destination"></a>Spécifier des options pour les données existantes dans la destination
 **Supprimer des lignes dans la table/le fichier de destination**  
 Indiquez si les données d’une table existante doivent être effacées avant d’en charger de nouvelles.  
  
 **Ajouter des lignes à la table/au fichier de destination**  
 Indiquez si les nouvelles données doivent être ajoutées à la suite des données déjà présentes dans une table existante.  
  
 **Supprimer et recréer la table de destination**  
 Choisissez cette option pour remplacer la table de destination. Cette option est disponible uniquement lorsque vous faites appel à l'Assistant pour créer la table de destination. La table de destination est uniquement supprimée et recréée si vous enregistrez le package créé par l’Assistant, puis que vous réexécutez le package. Il s’agit d’une option pratique si vous souhaitez tester vos paramètres plusieurs fois.
  
 **Activer l’insertion d’identité**  
 Permet d'insérer des valeurs d'identité des données source dans une colonne d'identité de la table de destination. Par défaut, la colonne d’identité de destination ne permet généralement pas cela.  
  
> [!TIP] En général, si vos clés primaires existantes sont dans une colonne d’identité, une colonne NuméroAuto ou son équivalent, vous devez sélectionner cette option pour conserver les valeurs de vos clés primaires existantes.  Sinon, la colonne d’identité de destination assigne de nouvelles valeurs.  

## <a name="review-column-mappings-and-destination-data-types"></a>Vérifier les mappages de colonnes et les types de données de destination 
 **Mappages**  
 Affiche la manière dont chaque colonne dans la source de données est mappée à une colonne dans la destination.
 
 Sélectionnez **ignorer** dans la colonne **Destination** de cette boîte de dialogue pour les colonnes que vous souhaitez ignorer. Vous n’êtes pas obligé de copier toutes les colonnes dans une table.  
 
 ![Mappage de colonnes - mappages](../../integration-services/import-export-data/media/column-mappings-mappings.png)
  
 La liste **Mappages** comprend les colonnes suivantes.  
  
-    **Source**  
     Affiche chaque colonne source pour laquelle vous pouvez spécifier des paramètres de conversion si nécessaire.  
  
-   **Destination**  
    Affichez la colonne de destination mappée ou sélectionnez une autre colonne.
    
    Spécifiez si vous voulez ignorer une colonne pendant la copie. Vous pouvez copier uniquement un sous-ensemble de colonnes en sélectionnant **ignorer** dans cette colonne pour les colonnes que vous souhaitez ignorer. Avant de mapper les colonnes, vous devez ignorer toutes les colonnes qui ne seront pas mappées.  
  
-   **Type**  
    Affichez le type de données de la colonne de destination ou sélectionnez un autre type de données.
  
-   **Nullable**  
    Spécifiez si la colonne de destination autorise une valeur null.  
  
-   **Taille**  
    Spécifiez le nombre de caractères dans la colonne de destination, si applicable.  
  
-    **Précision**  
    Spécifiez la précision des données numériques dans la colonne de destination en indiquant le nombre de chiffres, si applicable.  
  
 -   **Échelle**  
    Spécifiez l’échelle des données numériques dans la colonne de destination en indiquant le nombre de décimales, si applicable.  
  
## <a name="whats-next"></a>Étape suivante  
 Une fois que vous avez spécifié et configuré les colonnes de destination qui recevront les données copiées, cliquez sur **OK**. La boîte de dialogue **Mappage de colonnes** vous fait alors revenir à la page **Sélectionner les tables et les vues sources** ou **Configurer la destination du fichier plat**. Pour plus d’informations, consultez [Sélectionner les tables et les vues sources](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md) ou [Configurer la destination du fichier plat](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md).  
  
 Si vous avez spécifié un mappage qui risque d’échouer dans la liste **Mappages**, la boîte de dialogue **Mappage de colonnes** affiche la page **Vérifier le mappage de type de données**. Dans cette page, vous passez en revue les avertissements, vous spécifiez les options de conversion et vous indiquez aussi comment gérer les erreurs. Pour plus d’informations, consultez [Vérifier le mappage de type de données](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md).  
 
 ## <a name="see-also"></a>Voir aussi
[Mappage de type de données dans l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)
