---
title: Modification de la Dimension Customer | Documents Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5b5aed99-1760-4bc7-b248-52ecb0b97ebc
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.openlocfilehash: fef2880a71981b360d5ce124d6b5e2f0d8b24859
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140630"
---
# <a name="modifying-the-customer-dimension"></a>Modification de la dimension Customer
  Il existe différents moyens de rendre les dimensions d'un cube plus conviviales et plus fonctionnelles. Dans les tâches dans cette rubrique, vous modifiez la dimension Customer.  
  
## <a name="renaming-attributes"></a>Affectation d'un nouveau nom aux attributs  
 Vous pouvez modifier les noms d’attributs avec l’onglet **Structure de dimension** du Concepteur de dimensions.  
  
#### <a name="to-rename-an-attribute"></a>Pour renommer un attribut  
  
1.  Basculez vers le **Concepteur de dimensions** pour la dimension Customer dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Pour cela, double-cliquez sur la dimension **Customer** du nœud **Dimensions** de l’Explorateur de solutions.  
  
2.  Dans le volet **Attributs** , cliquez avec le bouton droit sur **English Country Region Name**et cliquez sur **Renommer**. Modifier le nom de l’attribut à `Country-Region`.  
  
3.  Modifiez les noms des attributs suivants de la même manière :  
  
    -   **English Education** attribut : remplacer par `Education`  
  
    -   **English Occupation** attribut : remplacer par `Occupation`  
  
    -   **State Province Name** attribut : remplacer par `State-Province`  
  
4.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="creating-a-hierarchy"></a>Création d'une hiérarchie  
 Vous pouvez créer une hiérarchie en faisant glisser un attribut du volet **Attributes** vers le volet **Hiérarchies** .  
  
#### <a name="to-create-a-hierarchy"></a>Pour créer une hiérarchie  
  
1.  Faites glisser le `Country-Region` attribut à partir de la **attributs** volet dans le **hiérarchies** volet.  
  
2.  Faites glisser le `State-Province` d’attribut du **attributs** volet dans le  **\<nouveau niveau >** dans la cellule la **hiérarchies** volet, sous la `Country-Region` niveau.  
  
3.  Faites glisser le **Ville** d’attribut du **attributs** volet dans le  **\<nouveau niveau >** de cellule dans le **hiérarchies** volet, sous le `State-Province` niveau.  
  
4.  Dans le **hiérarchies** volet de la **Structure de Dimension** onglet, avec le bouton droit de la barre de titre de la **hiérarchie** hiérarchie, sélectionnez **renommer**, puis tapez `Customer Geography`.  
  
     Le nom de la hiérarchie est désormais `Customer Geography`.  
  
5.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="adding-a-named-calculation"></a>Ajout d'un calcul nommé  
 Vous pouvez ajouter un calcul nommé, c'est-à-dire une expression SQL qui est représentée sous la forme d'une colonne calculée, dans la table d'une vue de source de données. L'expression apparaît et se comporte comme une colonne dans une table. Les calculs nommés permettent d'étendre le schéma relationnel des tables existantes dans une vue de source de données, sans avoir à modifier la table dans la source de données sous-jacente. Pour plus d’informations, consultez [Définir des calculs nommés dans une vue de source de données &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md).  
  
#### <a name="to-add-a-named-calculation"></a>Pour ajouter un calcul nommé  
  
1.  Ouvrez la vue de source de données **[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012** en double-cliquant dessus dans le dossier **Vues des sources de données** de l’Explorateur de solutions.  
  
2.  Dans le volet **Tables** à gauche, cliquez avec le bouton droit sur **Customer**, puis cliquez sur **Nouveau calcul nommé**.  
  
3.  Dans le **créer un calcul nommé** boîte de dialogue, tapez `FullName` dans les **nom de la colonne** zone, puis tapez ou copiez et collez le texte suivant `CASE` instruction dans le **Expression**  zone :  
  
    ```  
    CASE  
       WHEN MiddleName IS NULL THEN  
       FirstName + ' ' + LastName  
       ELSE  
       FirstName + ' ' + MiddleName + ' ' + LastName  
    END  
    ```  
  
     Le `CASE` instruction concatène le **FirstName**, **MiddleName**, et **LastName** de dimension en tant que colonnes dans une seule colonne que vous utiliserez dans le client le nom affiché pour le **client** attribut.  
  
4.  Cliquez sur **OK**, puis développez **Customer** dans le volet **Tables** .  
  
     La `FullName` calcul nommé apparaît dans la liste des colonnes de la table Customer, avec une icône qui indique qu’il est un calcul nommé.  
  
5.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
6.  Dans le volet **Tables** , cliquez avec le bouton droit sur **Customer**, puis cliquez sur **Explorer les données**.  
  
7.  Vérifiez la dernière colonne de la vue **Explorer la table Customer** .  
  
     Notez que la `FullName` colonne apparaît dans la vue de source de données sont correctement concaténées des données à partir de plusieurs colonnes de la source de données sous-jacente et sans modifier la source de données d’origine.  
  
8.  Fermez l'onglet **Explorer la table Customer** .  
  
## <a name="using-the-named-calculation-for-member-names"></a>Utilisation du calcul nommé pour les noms des membres  
 Après avoir créé un calcul nommé dans la vue de la source de données, vous pouvez utiliser le calcul nommé comme propriété d'un attribut.  
  
#### <a name="to-use-the-named-calculation-for-member-names"></a>Pour utiliser le calcul nommé pour les noms des membres  
  
1.  Affichez le Concepteur de dimensions pour la dimension Customer.  
  
2.  Dans le volet **Attributs** de l’onglet **Structure de dimension** , cliquez sur l’attribut **Customer Key** .  
  
3.  Ouvrez la fenêtre Propriétés et cliquez sur le bouton **Masquer automatiquement** de la barre de titre pour qu’elle reste ouverte.  
  
4.  Dans le **nom** champ de propriété, tapez `Full Name`.  
  
5.  Cliquez dans le champ de propriété **NameColumn** en bas, puis cliquez sur le bouton de navigation (**...**) pour ouvrir la boîte de dialogue **Colonne de nom** .  
  
6.  Sélectionnez `FullName` au bas de la **colonne Source** liste, puis cliquez sur **OK**.  
  
7.  Dans l’onglet Structure de Dimensions, faites glisser le `Full Name` attribut à partir de la **attributs** volet dans le  **\<nouveau niveau >** de cellule dans le **hiérarchies** volet, en dessous du **Ville** niveau.  
  
8.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="defining-display-folders"></a>Définition de dossiers d'affichage  
 Vous pouvez utiliser les dossiers d'affichage pour grouper les hiérarchies d'utilisateur et d'attributs dans des arborescences afin d'augmenter la convivialité.  
  
#### <a name="to-define-display-folders"></a>Pour définir les dossiers d'affichage  
  
1.  Ouvrez l’onglet **Structure de dimension** pour la dimension Customer.  
  
2.  Dans le volet **Attributs** , sélectionnez les attributs suivants en maintenant la touche Ctrl enfoncée pendant que vous cliquez sur chacun d’eux :  
  
    -   **Ville**  
  
    -   `Country-Region`  
  
    -   **Postal Code**  
  
    -   `State-Province`  
  
3.  Dans la fenêtre Propriétés, cliquez sur le **AttributeHierarchyDisplayFolder** champ de propriété en haut (vous devrez peut-être pointer dessus pour afficher le nom complet), puis tapez `Location`.  
  
4.  Dans le **hiérarchies** volet, cliquez sur `Customer Geography`, puis, dans la fenêtre Propriétés à droite, sélectionnez `Location` comme valeur de la **DisplayFolder** propriété.  
  
5.  Dans le volet **Attributs** , sélectionnez les attributs suivants en maintenant la touche Ctrl enfoncée pendant que vous cliquez sur chacun d’eux :  
  
    -   **Commute Distance**  
  
    -   `Education`  
  
    -   **Gender**  
  
    -   **House Owner Flag**  
  
    -   **Marital Status**  
  
    -   **Number Cars Owned**  
  
    -   **Number Children At Home**  
  
    -   `Occupation`  
  
    -   **Total Children**  
  
    -   **Yearly Income**  
  
6.  Dans la fenêtre Propriétés, cliquez sur le **AttributeHierarchyDisplayFolder** propriété de champ en haut et tapez `Demographic`.  
  
7.  Dans le volet **Attributs** , sélectionnez les attributs suivants en maintenant la touche Ctrl enfoncée pendant que vous cliquez sur chacun d’eux :  
  
    -   **Email Address**  
  
    -   **Téléphone**  
  
8.  Dans la fenêtre Propriétés, cliquez sur le **AttributeHierarchyDisplayFolder** champ de propriété et le type `Contacts`.  
  
9. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="defining-composite-keycolumns"></a>Définition de KeyColumns composite  
 La propriété **KeyColumns** contient la colonne ou les colonnes qui représentent la clé pour l’attribut. Dans cette leçon, vous créez une clé composite pour le **Ville** et `State-Province` attributs. Les clés composites peuvent être utiles lorsque vous devez identifier un attribut de façon unique. Par exemple, lorsque vous définissez des relations d’attributs plus loin dans ce didacticiel, un **Ville** attribut doit identifier de façon unique un `State-Province` attribut. Toutefois, il peut y avoir plusieurs villes avec le même nom dans différents états. Pour cette raison, vous allez créer une clé composite composée des colonnes **StateProvinceName** et **City** pour l’attribut **City** . Pour plus d’informations, consultez [Modifier la propriété KeyColumn d’un attribut](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).  
  
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
  
2.  Dans le **attributs** volet, cliquez sur le `State-Province` attribut.  
  
3.  Dans la fenêtre **Propriétés** , cliquez dans le champ **KeyColumns** , puis cliquez sur le bouton Parcourir (**...**).  
  
4.  Dans la boîte de dialogue **Colonnes clés** , dans la liste **Colonnes disponibles** , sélectionnez la colonne **EnglishCountryRegionName**, puis cliquez sur le bouton **>** .  
  
     Les colonnes **EnglishCountryRegionName** et **StateProvinceName** s’affichent maintenant dans la liste **Colonnes clés** .  
  
5.  Cliquez sur **OK**.  
  
6.  Pour définir le **NameColumn** propriété de la `State-Province` d’attribut, cliquez sur le **NameColumn** champ dans la fenêtre Propriétés, puis cliquez sur le bouton de navigation (**...** ) bouton.  
  
7.  Dans la boîte de dialogue **Colonne de nom** , dans la liste **Colonne source** , sélectionnez **StateProvinceName**, puis cliquez sur **OK**.  
  
8.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="defining-attribute-relationships"></a>Définition des relations d'attributs  
 Si les données sous-jacentes le prennent en charge, il est également conseillé de définir des relations d'attributs entre les attributs. La définition de relations d'attributs accélère le traitement des dimensions, des partitions et des requêtes. Pour plus d’informations, consultez [Définir des relations d’attributs](multidimensional-models/attribute-relationships-define.md) et [Relations d’attributs](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
#### <a name="to-define-attribute-relationships"></a>Pour définir les relations d'attributs  
  
1.  Dans le **Concepteur de dimensions** pour la dimension Customer, cliquez sur l’onglet **Relations d’attributs** . Cela peut prendre un certain temps.  
  
2.  Dans le diagramme, cliquez avec le bouton droit sur l’attribut **City** , puis sélectionnez **Nouvelle relation d’attribut**.  
  
3.  Dans la boîte de dialogue **Créer une relation d’attribut** , **l’Attribut source** est **City**. Définir le **attribut associé** à `State-Province`.  
  
4.  Dans la liste **Type de relation** , définissez le type de relation sur **Rigide**.  
  
     Le type de relation est **Rigide** car les relations entre les membres ne changeront pas au fil du temps. Par exemple, il serait exceptionnel qu'une ville fasse partie d'un autre état ou d'une autre province.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Dans le diagramme, cliquez sur le `State-Province` d’attribut, puis sélectionnez **nouvelle relation d’attribut**.  
  
7.  Dans le **créer une relation d’attribut** boîte de dialogue, la **attribut Source** est `State-Province`. Définir le **attribut associé** à `Country-Region`.  
  
8.  Dans la liste **Type de relation** , définissez le type de relation sur **Rigide**.  
  
9. Cliquez sur **OK**.  
  
10. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="deploying-changes-processing-the-objects-and-viewing-the-changes"></a>Déploiement des modifications, traitement des objets et affichage des modifications  
 Une fois les attributs et les hiérarchies modifiés, vous devez déployer les modifications et retraiter les objets associés avant de pouvoir visualiser ces modifications.  
  
#### <a name="to-deploy-the-changes-process-the-objects-and-view-the-changes"></a>Pour déployer les modifications, traiter les objets et visualiser les modifications  
  
1.  Dans le menu **Générer** de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur **Déployer Analysis Services Tutorial**.  
  
2.  Après avoir reçu le message **Le déploiement est terminé** , cliquez sur l’onglet **Navigateur** du Concepteur de dimensions pour la dimension Customer, puis cliquez sur le bouton Reconnecter, à gauche de la barre d’outils du Concepteur.  
  
3.  Vérifiez que `Customer Geography` est sélectionné dans le **hiérarchie** liste, puis, dans le volet de navigateur, développez **tous les**, développez **Australie**, développez **nouveau sud Wales**, puis développez **Coffs Harbour**.  
  
     Le navigateur affiche les clients dans la ville.  
  
4.  Basculez vers le **Concepteur de cube** pour le cube [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial. Pour cela, double-cliquez sur le cube **Analysis Services Tutorial** dans le nœud **Cubes** de **l’Explorateur de solutions**.  
  
5.  Cliquez sur l’onglet **Navigateur** , puis cliquez sur le bouton Reconnecter dans la barre d’outils du Concepteur.  
  
6.  Dans le volet **Groupe de mesures** , développez **Customer**.  
  
     Notez que sous Customer n'apparaît plus une longue liste d'attributs, mais uniquement les dossiers d'affichage et les attributs pour lesquels aucune valeur n'a été affectée pour les dossiers d'affichage.  
  
7.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Modification de la Dimension de produit](lesson-3-3-modifying-the-product-dimension.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Dimension Attribute Properties Reference](multidimensional-models/dimension-attribute-properties-reference.md)   
 [Supprimer un attribut d’une Dimension](multidimensional-models/attribute-properties-remove-an-attribute-from-a-dimension.md)   
 [Renommer un attribut](multidimensional-models/attribute-properties-rename-an-attribute.md)   
 [Définir des calculs nommés dans une vue de Source de données &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  