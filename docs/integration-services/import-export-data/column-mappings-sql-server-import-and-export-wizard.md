---
title: Mappages de colonnes (SQL Server Assistant Importation et exportation) | Documents Microsoft
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
- sql13.dts.impexpwizard.columnmapandtransform.f1
ms.assetid: eadc54a6-f936-4ffc-91d7-fbfd2bdcab93
caps.latest.revision: 69
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b1ed879f21396c3c8d588307eaf087daea8c44c3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="column-mappings-sql-server-import-and-export-wizard"></a>Mappage de colonnes (Assistant Importation et exportation SQL Server)
  Une fois que vous avez sélectionné les tables et vues existantes pour copier ou vérifier la requête que vous avez fournie, l’Assistant Importation et Exportation **affiche la boîte de dialogue**Mappage de colonnes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si vous cliquez sur **Modifier les mappages** . Dans cette page, vous spécifiez et configurez des colonnes de destination pour recevoir les données copiées à partir des colonnes source. Fréquence à laquelle vous n’avez pas à apporter des modifications à cette page.
  
Si vous ne souhaitez copier toutes les colonnes dans la table sélectionnée, une chose à que faire dans cette page est l’exclure les colonnes que vous ne souhaitez pas. Sélectionnez **ignorer** dans les **Destination** colonne de la **mappages** liste pour les colonnes que vous ne voulez pas copier.
 
## <a name="screen-shot-of-the-column-mappings-page"></a>Capture d’écran de la page Mappages de colonnes 
 La capture d’écran suivante montre un exemple de la **mappages de colonnes** boîte de dialogue de l’Assistant. 
 
 Dans cet exemple, vous voyez que l’Assistant va créer une table de destination, car **Créer la table de destination** est sélectionnée. Par défaut, l’Assistant attribue chaque colonne dans la nouvelle table de destination le même nom, type de données et propriétés que la colonne source correspondante. 
  
 ![Page de mappages de colonne de l’Assistant Importation et exportation](../../integration-services/import-export-data/media/column-mappings.png "page Mappages de colonne de l’Assistant Importation et exportation")  
  
## <a name="review-the-source-and-destination"></a>Passez en revue la source et la destination 
![Section de page, source et destination de mappages de colonne](../../integration-services/import-export-data/media/column-mappings-page-source-and-destination-section.png)

 **Source**  
 La table source sélectionnée, l’affichage ou la requête.  
  
 **Destination**  
 La table de destination sélectionné ou la vue.  

## <a name="optionally-create-a-new-destination-table"></a>Si vous le souhaitez, créez une nouvelle table de destination
![Page de mappages de colonne, nouvelle section de la table](../../integration-services/import-export-data/media/column-mappings-page-new-table-section.png)

 **Créer la table/le fichier de destination**  
 Créer la table de destination si elle n’existe pas déjà.    
  
 **Modifier SQL**  
Cliquez sur **Modifier SQL** pour ouvrir la boîte de dialogue **Instruction SQL de création de table** . Utilisez l’instruction CREATE TABLE générée automatiquement, ou modifier en fonction de vos besoins. Si vous modifiez manuellement cette instruction, vous devez vérifier que la liste des mappages de colonnes reconnaît vos modifications. Pour plus d’informations, consultez [Instruction SQL Create Table](../../integration-services/import-export-data/create-table-sql-statement-sql-server-import-and-export-wizard.md).  

### <a name="sometimes-these-options-are-disabled"></a>Parfois, ces options sont désactivées.
Le **créer le fichier de la table destination** option et la **Modifier SQL** bouton sont automatiquement activées ou désactivées automatiquement.

-   **Activé.** Si vous avez spécifié un **nouveau** table de destination sur le **sélectionner des Tables Source et vues** page, le **créer la table de destination** option est sélectionnée automatiquement et la **Modifier SQL** bouton est activé.

-   **Désactivé.** Si vous avez sélectionné un **existant** table de destination sur le **sélectionner des Tables Source et vues** page, le **créer la table de destination** option et la **Modifier SQL** bouton sont désactivées. Si vous souhaitez créer une nouvelle table de destination, revenez à la **sélectionner des Tables Source et vues** page et entrez le nom d’un **nouveau** de table dans le **Destination** colonne.  

## <a name="what-about-existing-data-in-the-destination"></a>Que se passe-t-il pour les données existantes dans la destination ?
![Page de mappages de colonne, section options](../../integration-services/import-export-data/media/column-mappings-page-options-section.png)

 **Supprimer des lignes dans la table/le fichier de destination**  
 Indiquez si les données d’une table existante doivent être effacées avant d’en charger de nouvelles.  
  
 **Ajouter des lignes à la table/au fichier de destination**  
 Indiquez si les nouvelles données doivent être ajoutées à la suite des données déjà présentes dans une table existante.  
  
 **Supprimer et recréer la table de destination**  
 Choisissez cette option pour remplacer la table de destination. Cette option est disponible uniquement lorsque vous avez utilisé l’Assistant pour créer la table de destination. La table de destination est uniquement supprimée et recréée si vous enregistrez le package créé par l’Assistant, puis que vous réexécutez le package. Il s’agit d’une option pratique si vous souhaitez tester vos paramètres plusieurs fois.
  
 **Activer l’insertion d’identité**  
 Permet d'insérer des valeurs d'identité des données source dans une colonne d'identité de la table de destination. Par défaut, la colonne d’identité de destination ne permet généralement pas cela.  
  
> [!TIP]
> En général, si vos clés primaires existantes sont dans une colonne d’identité, une colonne NuméroAuto ou son équivalent, vous devez sélectionner cette option pour conserver les valeurs de vos clés primaires existantes.  Sinon, la colonne d’identité de destination assigne de nouvelles valeurs.  

## <a name="keep-your-autonumber-or-identity-values"></a>Conserver les valeurs autonumber ou identity
Si vous exportez des données qui a une colonne NuméroAuto ou une colonne d’identité - par exemple, si vous exportez à partir de Microsoft Access - veillez à sélectionner **insertion d’identité activer** comme ci-dessus immédiatement.

## <a name="review-column-mappings"></a>Passez en revue les mappages de colonnes
![Page de mappages de colonne, section mappages](../../integration-services/import-export-data/media/column-mappings-page-mappings-section.png)

 **Mappages**  
 Affiche la manière dont chaque colonne dans la source de données est mappée à une colonne dans la destination.
 
La liste **Mappages** comprend les colonnes suivantes.  
  
-    **Source**  
     Permet d’afficher chaque colonne source.  
  
-   **Destination**  
    Affichez la colonne de destination mappée ou sélectionnez une autre colonne.
    
    Vous n’êtes pas obligé de copier toutes les colonnes de la table source. Sélectionnez **ignorer** dans cette colonne pour les colonnes que vous souhaitez ignorer. Avant de mapper les colonnes, vous devez ignorer toutes les colonnes qui ne seront pas mappées.  
  
-   **Type**  
    Affichez le type de données de la colonne de destination ou sélectionnez un autre type de données.
  
-   **Nullable**  
    Spécifiez si la colonne de destination autorise une valeur null.  
  
-   **Taille**  
    Spécifiez le nombre de caractères dans la colonne de destination, si applicable.  
  
-    **Précision**  
    Spécifiez la précision des données numériques dans la colonne de destination - autrement dit, le nombre de chiffres - le cas échéant.  
  
 -   **Échelle**  
    Spécifiez l’échelle des données numériques dans la colonne de destination - autrement dit, le nombre de décimales - le cas échéant.  
  
## <a name="whats-next"></a>Étape suivante  
 Après avoir examiné et configurer les colonnes de destination pour recevoir les données copiées à partir des colonnes source et cliquez sur **OK**, le **mappages de colonnes** boîte de dialogue vous renvoie à la **sélectionner des Tables Source et vues** page ou à la **configurer la Destination de fichier plat** page. Pour plus d’informations, consultez [Sélectionner les tables et les vues sources](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md) ou [Configurer la destination du fichier plat](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md).  
  
 Si vous avez spécifié un mappage qui risque d’échouer dans la liste **Mappages** , la boîte de dialogue **Mappage de colonnes** affiche la page **Vérifier le mappage de type de données** . Dans cette page, vous passez en revue les avertissements, vous spécifiez les options de conversion et vous indiquez aussi comment gérer les erreurs. Pour plus d’informations, consultez [Vérifier le mappage de type de données](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md).  
 
 ## <a name="see-also"></a>Voir aussi
[Mappage de type de données dans l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)  
[Bien démarrer avec cet exemple simple de l’Assistant Importation et Exportation](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)


