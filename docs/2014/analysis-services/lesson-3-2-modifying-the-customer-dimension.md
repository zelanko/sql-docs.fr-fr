---
title: Modification de la dimension Customer | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5b5aed99-1760-4bc7-b248-52ecb0b97ebc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 63cfc1fc4b5bcc3e1c468bbb456a660587757f2b
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543441"
---
# <a name="modifying-the-customer-dimension"></a>Modification de la dimension Customer
  Il existe différents moyens de rendre les dimensions d'un cube plus conviviales et plus fonctionnelles. Dans les tâches dans cette rubrique, vous modifiez la dimension Customer.  
  
## <a name="renaming-attributes"></a>Affectation d'un nouveau nom aux attributs  
 Vous pouvez modifier les noms d’attributs avec l’onglet **Structure de dimension** du Concepteur de dimensions.  
  
#### <a name="to-rename-an-attribute"></a>Pour renommer un attribut  
  
1.  Basculez vers le **Concepteur de dimensions** pour la dimension Customer dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Pour cela, double-cliquez sur la dimension **Customer** du nœud **Dimensions** de l’Explorateur de solutions.  
  
2.  Dans le volet **Attributs** , cliquez avec le bouton droit sur **English Country Region Name**et cliquez sur **Renommer**. Remplacez le nom de l’attribut par `Country-Region` .  
  
3.  Modifiez les noms des attributs suivants de la même manière :  
  
    -   Attribut d' **éducation anglais** -changer en`Education`  
  
    -   Attribut d' **occupation en anglais** -changer en`Occupation`  
  
    -   **State Province Name** attribut-change to`State-Province`  
  
4.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="creating-a-hierarchy"></a>Création d'une hiérarchie  
 Vous pouvez créer une hiérarchie en faisant glisser un attribut du volet **Attributes** vers le volet **Hiérarchies** .  
  
#### <a name="to-create-a-hierarchy"></a>Pour créer une hiérarchie  
  
1.  Faites glisser l' `Country-Region` attribut du volet **attributs** vers le volet **hiérarchies** .  
  
2.  Faites glisser l' `State-Province` attribut du volet **attributs** vers la **\<new level>** cellule dans le volet **hiérarchies** , sous le `Country-Region` niveau.  
  
3.  Faites glisser l’attribut **City** du volet **attributs** vers la **\<new level>** cellule dans le **volet Hiérarchies** , sous le `State-Province` niveau.  
  
4.  Dans le volet **hiérarchies** de l’onglet **structure de dimension** , cliquez avec le bouton droit sur la barre de titre de la hiérarchie **hiérarchie** , sélectionnez **Renommer**, puis tapez `Customer Geography` .  
  
     Le nom de la hiérarchie est maintenant `Customer Geography` .  
  
5.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="adding-a-named-calculation"></a>Ajout d'un calcul nommé  
 Vous pouvez ajouter un calcul nommé, c'est-à-dire une expression SQL qui est représentée sous la forme d'une colonne calculée, dans la table d'une vue de source de données. L'expression apparaît et se comporte comme une colonne dans une table. Les calculs nommés permettent d'étendre le schéma relationnel des tables existantes dans une vue de source de données, sans avoir à modifier la table dans la source de données sous-jacente. Pour plus d’informations, consultez [définir des calculs nommés dans une vue de source de données &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
#### <a name="to-add-a-named-calculation"></a>Pour ajouter un calcul nommé  
  
1.  Ouvrez la vue de source de données ** [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012** en double-cliquant dessus dans le dossier **vues des sources de données** de Explorateur de solutions.  
  
2.  Dans le volet **Tables** à gauche, cliquez avec le bouton droit sur **Customer**, puis cliquez sur **Nouveau calcul nommé**.  
  
3.  Dans la boîte de dialogue **créer un calcul nommé** , tapez `FullName` dans la zone **nom** de la colonne, puis tapez ou copiez-collez l' `CASE` instruction suivante dans la zone **expression** :  
  
    ```  
    CASE  
       WHEN MiddleName IS NULL THEN  
       FirstName + ' ' + LastName  
       ELSE  
       FirstName + ' ' + MiddleName + ' ' + LastName  
    END  
    ```  
  
     L' `CASE` instruction concatène les colonnes **FirstName**, **MiddleName**et **LastName** en une seule colonne que vous allez utiliser dans la dimension Customer comme nom affiché pour l’attribut **Customer** .  
  
4.  Cliquez sur **OK**, puis développez **Customer** dans le volet **Tables** .  
  
     Le `FullName` calcul nommé s’affiche dans la liste des colonnes de la table Customer, avec une icône qui indique qu’il s’agit d’un calcul nommé.  
  
5.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
6.  Dans le volet **Tables** , cliquez avec le bouton droit sur **Customer**, puis cliquez sur **Explorer les données**.  
  
7.  Vérifiez la dernière colonne de la vue **Explorer la table Customer** .  
  
     Notez que la `FullName` colonne apparaît dans la vue de source de données, et que les données sont correctement concaténées à partir de plusieurs colonnes de la source de données sous-jacente et sans modification de la source de données d’origine.  
  
8.  Fermez l'onglet **Explorer la table Customer** .  
  
## <a name="using-the-named-calculation-for-member-names"></a>Utilisation du calcul nommé pour les noms des membres  
 Après avoir créé un calcul nommé dans la vue de la source de données, vous pouvez utiliser le calcul nommé comme propriété d'un attribut.  
  
#### <a name="to-use-the-named-calculation-for-member-names"></a>Pour utiliser le calcul nommé pour les noms des membres  
  
1.  Affichez le Concepteur de dimensions pour la dimension Customer.  
  
2.  Dans le volet **Attributs** de l’onglet **Structure de dimension** , cliquez sur l’attribut **Customer Key** .  
  
3.  Ouvrez la fenêtre Propriétés et cliquez sur le bouton **Masquer automatiquement** de la barre de titre pour qu’elle reste ouverte.  
  
4.  Dans le champ **nom** de la propriété, tapez `Full Name` .  
  
5.  Cliquez dans le champ de propriété **NameColumn** en bas, puis cliquez sur le bouton Parcourir (**...**) pour ouvrir la boîte de dialogue **colonne de nom** .  
  
6.  Sélectionnez `FullName` au bas de la liste **colonne source** , puis cliquez sur **OK**.  
  
7.  Dans l’onglet structure de dimension, faites glisser l' `Full Name` attribut du volet **attributs** vers la **\<new level>** cellule dans le volet **hiérarchies** , sous le niveau **City** .  
  
8.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="defining-display-folders"></a>Définition de dossiers d'affichage  
 Vous pouvez utiliser les dossiers d'affichage pour grouper les hiérarchies d'utilisateur et d'attributs dans des arborescences afin d'augmenter la convivialité.  
  
#### <a name="to-define-display-folders"></a>Pour définir les dossiers d'affichage  
  
1.  Ouvrez l’onglet **Structure de dimension** pour la dimension Customer.  
  
2.  Dans le volet **Attributs** , sélectionnez les attributs suivants en maintenant la touche Ctrl enfoncée pendant que vous cliquez sur chacun d’eux :  
  
    -   **Ville**  
  
    -   `Country-Region`  
  
    -   **Code postal**  
  
    -   `State-Province`  
  
3.  Dans la Fenêtre Propriétés, cliquez sur le champ de propriété **AttributeHierarchyDisplayFolder** en haut (vous devrez peut-être pointer dessus pour afficher le nom complet), puis tapez `Location` .  
  
4.  Dans le volet **hiérarchies** , cliquez sur `Customer Geography` , puis dans le fenêtre Propriétés à droite, sélectionnez `Location` comme valeur de la propriété **DisplayFolder** .  
  
5.  Dans le volet **Attributs** , sélectionnez les attributs suivants en maintenant la touche Ctrl enfoncée pendant que vous cliquez sur chacun d’eux :  
  
    -   **Commute Distance**  
  
    -   `Education`  
  
    -   **Sexe**  
  
    -   **House Owner Flag**  
  
    -   **Marital Status**  
  
    -   **Number Cars Owned**  
  
    -   **Number Children At Home**  
  
    -   `Occupation`  
  
    -   **Total Children**  
  
    -   **Yearly Income**  
  
6.  Dans la Fenêtre Propriétés, cliquez sur le champ de propriété **AttributeHierarchyDisplayFolder** en haut, puis tapez `Demographic` .  
  
7.  Dans le volet **Attributs** , sélectionnez les attributs suivants en maintenant la touche Ctrl enfoncée pendant que vous cliquez sur chacun d’eux :  
  
    -   **Adresse e-mail**  
  
    -   **Téléphone**  
  
8.  Dans l’Fenêtre Propriétés, cliquez sur le champ de propriété **AttributeHierarchyDisplayFolder** et tapez `Contacts` .  
  
9. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="defining-composite-keycolumns"></a>Définition de KeyColumns composite  
 La propriété **KeyColumns** contient la colonne ou les colonnes qui représentent la clé pour l’attribut. Dans cette leçon, vous allez créer une clé composite pour la **ville** et les `State-Province` attributs. Les clés composites peuvent être utiles lorsque vous devez identifier un attribut de façon unique. Par exemple, lorsque vous définissez des relations d’attributs plus loin dans ce didacticiel, un attribut **City** doit identifier un attribut de façon unique `State-Province` . Toutefois, il peut y avoir plusieurs villes avec le même nom dans différents états. Pour cette raison, vous allez créer une clé composite composée des colonnes **StateProvinceName** et **City** pour l’attribut **City** . Pour plus d’informations, consultez [Modifier la propriété KeyColumn d’un attribut](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).  
  
#### <a name="to-define-composite-keycolumns-for-the-city-attribute"></a>Pour définir KeyColumns composite pour l'attribut Ville  
  
1.  Ouvrez l’onglet **Structure de dimension** pour la dimension Customer.  
  
2.  Dans le volet **Attributs** , cliquez sur l’attribut **City** .  
  
3.  Dans la fenêtre **Propriétés** , cliquez dans le champ **KeyColumns** en bas, puis cliquez sur le bouton de navigation (**...**).  
  
4.  Dans la boîte de dialogue **Colonnes clés** , dans la liste **Colonnes disponibles** , sélectionnez la colonne **StateProvinceName**, puis cliquez sur le bouton **>** .  
  
     Les colonnes **City** et **StateProvinceName** s’affichent maintenant dans la liste **Colonnes clés** .  
  
5.  Cliquez sur **OK**.  
  
6.  Pour définir la propriété **NameColumn** de l’attribut **City** , cliquez dans le champ **NameColumn** de la fenêtre Propriétés, puis cliquez sur le bouton de navigation (**...**).  
  
7.  Dans la boîte de dialogue **Colonne de nom** , dans la liste **Colonne source** , sélectionnez **City**, puis cliquez sur **OK**.  
  
8.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
#### <a name="to-define-composite-keycolumns-for-the-state-province-attribute"></a>Pour définir KeyColumns composite pour l'attribut État-Province  
  
1.  Vérifiez que l’onglet **Structure de dimension** de la dimension Customer est ouvert.  
  
2.  Dans le volet **attributs** , cliquez sur l' `State-Province` attribut.  
  
3.  Dans la fenêtre **Propriétés** , cliquez dans le champ **KeyColumns** , puis cliquez sur le bouton Parcourir (**...**).  
  
4.  Dans la boîte de dialogue **Colonnes clés** , dans la liste **Colonnes disponibles** , sélectionnez la colonne **EnglishCountryRegionName**, puis cliquez sur le bouton **>** .  
  
     Les colonnes **EnglishCountryRegionName** et **StateProvinceName** s’affichent maintenant dans la liste **Colonnes clés** .  
  
5.  Cliquez sur **OK**.  
  
6.  Pour définir la propriété **NameColumn** de l' `State-Province` attribut, cliquez sur le champ **NameColumn** dans la fenêtre Propriétés, puis cliquez sur le bouton de navigation (**...**).  
  
7.  Dans la boîte de dialogue **Colonne de nom** , dans la liste **Colonne source** , sélectionnez **StateProvinceName**, puis cliquez sur **OK**.  
  
8.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="defining-attribute-relationships"></a>Définition des relations d'attributs  
 Si les données sous-jacentes le prennent en charge, il est également conseillé de définir des relations d'attributs entre les attributs. La définition de relations d'attributs accélère le traitement des dimensions, des partitions et des requêtes. Pour plus d’informations, consultez [Définir des relations d’attributs](multidimensional-models/attribute-relationships-define.md) et [Relations d’attributs](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
#### <a name="to-define-attribute-relationships"></a>Pour définir les relations d'attributs  
  
1.  Dans le **Concepteur de dimensions** pour la dimension Customer, cliquez sur l’onglet **relations d’attributs** . Vous devrez peut-être attendre.  
  
2.  Dans le diagramme, cliquez avec le bouton droit sur l’attribut **City** , puis sélectionnez **Nouvelle relation d’attribut**.  
  
3.  Dans la boîte de dialogue **Créer une relation d’attribut** , **l’Attribut source** est **City**. Affectez à l' **attribut associé** la valeur `State-Province` .  
  
4.  Dans la liste **Type de relation** , définissez le type de relation sur **Rigide**.  
  
     Le type de relation est **Rigide** car les relations entre les membres ne changeront pas au fil du temps. Par exemple, il serait exceptionnel qu'une ville fasse partie d'un autre état ou d'une autre province.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Dans le diagramme, cliquez avec le bouton droit sur l' `State-Province` attribut, puis sélectionnez **nouvelle relation d’attribut**.  
  
7.  Dans la boîte de dialogue **créer une relation d’attribut** , l' **attribut source** est `State-Province` . Affectez à l' **attribut associé** la valeur `Country-Region` .  
  
8.  Dans la liste **Type de relation** , définissez le type de relation sur **Rigide**.  
  
9. Cliquez sur **OK**.  
  
10. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="deploying-changes-processing-the-objects-and-viewing-the-changes"></a>Déploiement des modifications, traitement des objets et affichage des modifications  
 Une fois les attributs et les hiérarchies modifiés, vous devez déployer les modifications et retraiter les objets associés avant de pouvoir visualiser ces modifications.  
  
#### <a name="to-deploy-the-changes-process-the-objects-and-view-the-changes"></a>Pour déployer les modifications, traiter les objets et visualiser les modifications  
  
1.  Dans le menu **Générer** de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur **Déployer Analysis Services Tutorial**.  
  
2.  Après avoir reçu le message **Le déploiement est terminé** , cliquez sur l’onglet **Navigateur** du Concepteur de dimensions pour la dimension Customer, puis cliquez sur le bouton Reconnecter, à gauche de la barre d’outils du Concepteur.  
  
3.  Vérifiez que `Customer Geography` est sélectionné dans la liste **hiérarchie** , puis dans le volet navigateur, développez **tout**, puis **Australie**, **Nouvelle Galles du Sud**, puis **Coffs**.  
  
     Le navigateur affiche les clients dans la ville.  
  
4.  Basculez vers le **Concepteur de cube** pour le cube [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial. Pour cela, double-cliquez sur le cube **Analysis Services Tutorial** dans le nœud **Cubes** de **l’Explorateur de solutions**.  
  
5.  Cliquez sur l’onglet **Navigateur** , puis cliquez sur le bouton Reconnecter dans la barre d’outils du Concepteur.  
  
6.  Dans le volet **Groupe de mesures** , développez **Customer**.  
  
     Notez que sous Customer n'apparaît plus une longue liste d'attributs, mais uniquement les dossiers d'affichage et les attributs pour lesquels aucune valeur n'a été affectée pour les dossiers d'affichage.  
  
7.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Modification de la dimension Product](lesson-3-3-modifying-the-product-dimension.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des propriétés d’attribut de dimension](multidimensional-models/dimension-attribute-properties-reference.md)   
 [Supprimer un attribut d’une dimension](multidimensional-models/attribute-properties-remove-an-attribute-from-a-dimension.md)   
 [Renommer un attribut](multidimensional-models/attribute-properties-rename-an-attribute.md)   
 [Définir des calculs nommés dans une vue de source de données &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
