---
title: 'Didacticiel : Ajouter un paramètre à votre rapport (Générateur de rapports) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: eab34ec4-b3ad-4a76-95cc-07b2f75ee6d7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cf5f7a4bee10b58f644d98fe03ada0a9e8d0faa3
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018880"
---
# <a name="tutorial-add-a-parameter-to-your-report-report-builder"></a>Didacticiel : Ajouter un paramètre à un rapport (Générateur de rapports)
  Ajoutez un paramètre à votre rapport pour permettre aux utilisateurs de filtrer les données de rapport à partir de la source de données ou dans le rapport. Les paramètres de rapport sont créés automatiquement pour chaque paramètre de requête que vous incluez dans une requête de dataset. Le type de données du paramètre détermine son apparence dans la barre d'outils de l'affichage du rapport.  
  
 ![rs_tut_Parameter](../../2014/tutorials/media/rs-tut-parameter.gif "rs_tut_Parameter")  
  
##  <a name="BackToTop"></a> Ce que vous allez apprendre  
 Dans ce didacticiel, vous apprendrez à effectuer les tâches suivantes :  
  
1.  [Créer un rapport de matrice et un Dataset à partir de l’Assistant tableau ou matrice](#Setup)  
  
2.  [Organiser les données, choisissez la disposition et le Style à partir de l’Assistant tableau ou matrice](#CompleteWizard)  
  
3.  [Ajouter un paramètre de requête pour créer un paramètre de rapport](#Query)  
  
4.  [Modifier le Type de données par défaut et d’autres propriétés pour un paramètre de rapport](#ChangeDefaultProperties)  
  
    1.  [Ajouter un Dataset pour fournir des valeurs disponibles et les noms complets](#AddDataset)  
  
    2.  [Spécifier les valeurs disponibles pour créer une liste déroulante de valeurs](#AvailableValues)  
  
    3.  [Spécifier les valeurs par défaut afin que le rapport s’exécute automatiquement](#DefaultValues)  
  
    4.  [Rechercher une valeur à partir d’un Dataset qui contient des paires nom/valeur](#NameValue)  
  
5.  [Afficher la valeur du paramètre sélectionné dans le rapport](#Expression)  
  
6.  [Utiliser le paramètre de rapport dans un filtre](#Filter)  
  
7.  [Modifier le paramètre de rapport pour accepter plusieurs valeurs](#Multivalued)  
  
8.  [Ajouter un paramètre booléen pour la visibilité conditionnelle](#Boolean)  
  
9. [Ajouter un titre de rapport](#Title)  
  
10. [Enregistrer le rapport](#Save)  
  
> [!NOTE]  
>  Dans ce didacticiel, les étapes de l'Assistant sont consolidées en une seule procédure. Pour obtenir des instructions détaillées sur l’accès à un serveur de rapports, choisissez une source de données et créer un jeu de données, consultez le premier didacticiel de cette série : [Didacticiel : Création d’un rapport de tableau de base &#40;Générateur de rapports&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Durée estimée pour effectuer ce didacticiel : 25 minutes.  
  
## <a name="requirements"></a>Configuration requise  
 Pour plus d’informations sur les spécifications, consultez [Éléments requis pour les didacticiels &#40;Générateur de rapports&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="Setup"></a> 1. Créer un rapport de matrice et un dataset à partir de l'Assistant Tableau ou matrice  
 Créez un rapport de matrice, une source de données et un dataset.  
  
> [!NOTE]  
>  Dans ce didacticiel, la requête contient les valeurs de données, afin qu'il ne soit pas nécessaire de disposer d'une source de données externe. Cela rend la requête assez longue. Dans un environnement métier, une requête ne contient pas les données. Ceci est nécessaire à des fins de formation uniquement.  
  
#### <a name="to-create-a-new-matrix-report"></a>Pour créer un rapport de matrice  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **le Générateur de rapports**, puis cliquez sur **le Générateur de rapports**.  
  
     La boîte de dialogue **Mise en route** s'affiche.  
  
    > [!NOTE]  
    >  Si le **mise en route** boîte de dialogue n’apparaît pas, à partir de la **le Générateur de rapports** bouton, cliquez sur **New**.  
  
2.  Dans le volet gauche, assurez-vous que **Rapport** est sélectionné.  
  
3.  Dans le volet droit, cliquez sur **Assistant Tableau ou matrice**.  
  
4.  Cliquez sur **Créer**.  
  
5.  Dans la page **Choisir un dataset** , cliquez sur **Créer un dataset**.  
  
6.  Cliquer sur **Suivant**.  
  
7.  Dans la page **Choisir une connexion à une source de données**, sélectionnez une source de données de type **SQL Server**. Sélectionnez une source de données dans la liste ou naviguez jusqu'au serveur de rapports pour en sélectionner une.  
  
8.  Cliquer sur **Suivant**.  
  
9. Dans la page **Créer une requête** , cliquez sur **Modifier en tant que texte**.  
  
10. Collez la requête suivante dans le volet de requête :  
  
    ```  
    ;WITH CTE (StoreID, Subcategory, Quantity)   
    AS (  
    SELECT 200 AS StoreID, 'Digital SLR Cameras' AS Subcategory, 2002 AS Quantity  
    UNION SELECT  200 AS StoreID, 'Camcorders' AS Subcategory, 1954 AS Quantity  
    UNION SELECT  200 AS StoreID, 'Accessories' AS Subcategory, 1895 AS Quantity  
    UNION SELECT  199 AS StoreID, 'Digital Cameras' AS Subcategory, 1849 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Digital SLR Cameras' AS Subcategory, 1579 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Camcorders' AS Subcategory, 1561 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Digital Cameras' AS Subcategory, 1553 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Accessories' AS Subcategory, 1534 AS Quantity  
    UNION SELECT 307 AS StoreID, 'Accessories' AS Subcategory, 1755 AS Quantity  
    UNION SELECT 307 AS StoreID, 'Camcorders' AS Subcategory, 1631 AS Quantity  
    UNION SELECT 307 AS StoreID, 'Digital SLR Cameras' AS Subcategory, 1772 AS Quantity)  
    SELECT StoreID, Subcategory, Quantity  
    FROM CTE  
    ```  
  
     Cette requête combine les résultats de plusieurs instructions SELECT [!INCLUDE[tsql](../includes/tsql-md.md)] dans une expression de table commune pour spécifier des valeurs basées sur des données simplifiées de l'exemple de base de données Contoso. Les données de ventes de Contoso représentent les données de ventes internationales relatives aux biens de consommation. Ce didacticiel utilise les données de ventes spécifiques aux appareils photo. Les sous-catégories représentent les appareils photo numériques, les appareils photo numériques reflex à lentille unique (SLR), les caméscopes et les accessoires.  
  
     La requête spécifie des noms de colonnes comprenant un identificateur de magasin, une sous-catégorie d'éléments de ventes et le volume commandé pour les commandes client de trois magasins. Dans cette requête, le nom du magasin ne fait pas partie du jeu de résultats. Ultérieurement, dans ce didacticiel, vous rechercherez le nom du magasin qui correspond à l'identificateur de magasin d'un dataset distinct.  
  
     Cette requête ne contient pas de paramètres de requête. Vous ajouterez ultérieurement des paramètres de requête dans ce didacticiel.  
  
11. Dans la barre d’outils du Concepteur de requêtes, cliquez sur **Exécuter** (**!**). Le jeu de résultats affiche 11 lignes de données qui montrent la quantité d’articles vendus pour chaque sous-catégorie dans quatre magasins et inclut les colonnes suivantes : StoreID, Subcategory, Quantity.  
  
12. Cliquer sur **Suivant**.  
  
##  <a name="CompleteWizard"></a> 2. Organiser les données, choisir la mise en page et le style à partir de l'Assistant Tableau ou matrice  
 Utilisez l'Assistant pour obtenir une conception initiale dans laquelle afficher les données. Le volet de visualisation de l'Assistant vous aide à visualiser le résultat du regroupement des données avant de terminer la conception de la table ou de la matrice.  
  
#### <a name="to-organize-data-into-groups"></a>Pour organiser les données en groupes  
  
1.  Dans la page **Organiser les champs** , faites glisser Subcategory vers **Groupes de lignes**.  
  
2.  Faites glisser StoreID vers **Groupes de colonnes**.  
  
3.  Faites glisser Quantity vers **Valeurs**.  
  
     Vous avez organisé les valeurs des quantités vendues dans des lignes regroupées par sous-catégorie. Il y a une colonne pour chaque magasin.  
  
4.  Cliquer sur **Suivant**.  
  
5.  Sur le **choisir une disposition** page sous **Options**, vérifiez que **afficher les sous-totaux et les totaux généraux** est sélectionné.  
  
     Lorsque vous exécuterez le rapport, la dernière colonne affichera la quantité totale de chaque sous-catégorie pour tous les magasins, et la dernière ligne affichera la quantité totale pour toutes les sous-catégories pour chaque magasin.  
  
6.  Cliquer sur **Suivant**.  
  
7.  Sur le **choisir un Style** page, dans le volet Styles, sélectionnez un style.  
  
8.  Cliquez sur **Terminer**.  
  
     La matrice est ajoutée à l'aire de conception. La matrice affiche trois colonnes et trois lignes. Les cellules de la première ligne contiennent Subcategory, [StoreID] et Total. Les cellules de la deuxième ligne contiennent des expressions qui représentent la sous-catégorie, la quantité d'articles vendus pour chaque magasin, ainsi que la quantité totale de chaque sous-catégorie pour tous les magasins. Les cellules de la dernière ligne affichent le total global pour chaque magasin.  
  
9. Cliquez dans la matrice, pointez sur le bord de la première colonne, saisissez la poignée, puis augmentez la largeur de la colonne.  
  
10. Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 Le rapport s'exécute sur le serveur de rapports en présentant son titre et l'heure à laquelle il a été traité.  
  
 Dans ce scénario, les en-têtes de colonnes affichent l'identificateur du magasin mais pas le nom du magasin. Ultérieurement, vous ajouterez une expression pour rechercher le nom de magasin dans un dataset qui contient des paires nom d'identificateur/nom de magasin.  
  
##  <a name="Query"></a> 3. Ajouter un paramètre de requête pour créer un paramètre de rapport  
 Lorsque vous ajoutez un paramètre de requête à une requête, le Générateur de rapports crée automatiquement un paramètre de rapport à valeur unique avec des propriétés par défaut pour le nom, le texte affiché à l'invite et le type de données.  
  
#### <a name="to-add-a-query-parameter"></a>Pour ajouter un paramètre de requête  
  
1.  Basculez en mode Conception.  
  
2.  Dans le volet des données de rapport, développez le dossier **Datasets** , cliquez avec le bouton droit sur **DataSet1**, puis cliquez sur **Requête**.  
  
3.  Ajoutez le code suivant [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE` clause comme dernière ligne dans la requête :  
  
    ```  
    WHERE StoreID = (@StoreID)  
    ```  
  
     Le `WHERE` clause limite les données récupérées à l’identificateur de magasin spécifié par le paramètre de requête *@StoreID*.  
  
4.  Dans la barre d’outils du Concepteur de requêtes, cliquez sur **Exécuter** (**!**). La boîte de dialogue **Définir les paramètres de la requête** s’ouvre et vous êtes invité à définir une valeur pour le paramètre de requête *@StoreID*.  
  
5.  Dans **Valeur du paramètre**, tapez **200**.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Le jeu de résultats affiche les quantités vendues des articles « Accessories », « Camcorders » et « Digital SLR Cameras » pour l’identificateur de magasin **200**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  Dans le volet des données de rapport, développez le dossier **Paramètres** .  
  
 Notez qu’il existe désormais un paramètre de rapport nommé *@StoreID*. Par défaut, le paramètre a type de données **texte**. Dans la mesure où l'identificateur de magasin est un entier, vous devez remplacer le type de données par le type Entier dans la procédure suivante.  
  
##  <a name="ChangeDefaultProperties"></a> 4. Modifier le type de données par défaut et d'autres propriétés pour un paramètre de rapport  
 Après avoir créé un paramètre de rapport, vous pouvez ajuster les valeurs par défaut des propriétés.  
  
#### <a name="to-change-the-default-data-type-for-a-report-parameter"></a>Pour modifier le type de données par défaut d'un paramètre de rapport  
  
1.  Dans le volet données du rapport sous la **paramètres** nœud, avec le bouton droit *@StoreID*, puis cliquez sur **propriétés du paramètre**.  
  
2.  Dans l’invite de commandes, tapez **identificateur de Store ?** Ce texte s'affiche sur la barre d'outils de la visionneuse de rapports lorsque vous exécutez le rapport.  
  
3.  Dans **Type de données**, dans la liste déroulante, sélectionnez **Entier**.  
  
4.  Acceptez les valeurs par défaut restantes dans la boîte de dialogue.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Affichez l'aperçu du rapport. La visionneuse de rapports affiche l’invite pour *@StoreID*.  
  
7.  Dans la barre d’outils de la visionneuse de rapports, en regard de StoreID, tapez **200**, puis cliquez sur **Afficher le rapport**.  
  
##  <a name="AddDataset"></a> 4a. Ajouter un dataset pour fournir des valeurs disponibles et des noms d'affichage  
 Pour vous assurer qu'un utilisateur ne peut taper que des valeurs valides pour un paramètre, vous pouvez créer une liste déroulante de valeurs à choisir. Les valeurs peuvent provenir d'un dataset ou d'une liste que vous spécifiez. Les valeurs disponibles doivent être fournies à partir d'un dataset comportant une requête qui ne contient pas de référence au paramètre.  
  
#### <a name="to-create-a-dataset-for-valid-values-for-a-parameter"></a>Pour créer un dataset de valeurs valides pour un paramètre  
  
1.  Basculez en mode Conception.  
  
2.  Dans le volet des données de rapport, cliquez avec le bouton droit sur le dossier **Datasets** , puis cliquez sur **Ajouter un dataset**.  
  
3.  Dans **Nom**, tapez **Stores**.  
  
4.  Sélectionnez le **utiliser un dataset incorporé dans mon rapport** option.  
  
5.  Dans **source de données**, dans la liste déroulante, choisissez la source de données que vous avez créé dans la première procédure.  
  
6.  Dans **Type de requête**, assurez-vous que **Texte** est sélectionné.  
  
7.  Dans **Requête**, collez le texte suivant :  
  
    ```  
    SELECT 200 AS StoreID, 'Contoso Catalog Store' as StoreName  
    UNION SELECT 199 AS StoreID, 'Contoso North America Online Store' as StoreName  
    UNION SELECT 307 AS StoreID, 'Contoso Asia Online Store' as StoreName  
    UNION SELECT 306 AS StoreID, 'Contoso Europe Online Store' as StoreName  
    ```  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Le volet des données de rapport affiche les champs StoreID et StoreName sous le nœud du dataset **Stores** .  
  
##  <a name="AvailableValues"></a> 4b. Spécifier les valeurs disponibles pour la création d'une liste déroulante de valeurs  
 Après avoir créé un dataset pour fournir des valeurs disponibles, vous devez modifier les propriétés de rapport pour spécifier quel dataset et quel champ utiliser pour remplir la liste déroulante à l'aide de valeurs valides dans la barre d'outils de la visionneuse de rapports.  
  
#### <a name="to-provide-available-values-for-a-parameter-from-a-dataset"></a>Pour fournir des valeurs disponibles pour un paramètre à partir d'un dataset  
  
1.  Dans le volet données du rapport, cliquez sur le paramètre *@StoreID*, puis cliquez sur **propriétés du paramètre**.  
  
2.  Cliquez sur **Valeurs disponibles**, puis sur **Obtenir les valeurs à partir d’une requête**.  
  
3.  Dans la liste déroulante **Dataset**, cliquez sur **Stores**.  
  
4.  Dans la liste déroulante **Champ de valeur**, cliquez sur StoreID.  
  
5.  Dans la liste déroulante **Champ d’étiquette**, cliquez sur StoreName. Le champ d'étiquette spécifie le nom d'affichage de la valeur.  
  
6.  Cliquez sur **Général**.  
  
7.  Dans l’invite de commandes, tapez **nom de Store ?**  
  
     L'utilisateur sélectionnera désormais un nom dans une liste de noms de magasins au lieu d'identificateurs de magasin. Notez que le type de données du paramètre reste **Entier** , car le paramètre est basé sur l’identificateur de magasin au lieu du nom de magasin.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. Affichez l'aperçu du rapport.  
  
     Dans la barre d’outils de la visionneuse de rapports, la zone de texte de paramètre est maintenant une liste déroulante qui affiche  **\<sélectionner une valeur >**.  
  
10. Dans la liste déroulante, sélectionnez Contoso Catalog Store, puis cliquez sur **afficher le rapport**.  
  
 Le rapport affiche les quantités vendues des articles « Accessories », « Camcorders » et « Digital SLR Cameras » pour l’identificateur de magasin **200**.  
  
##  <a name="DefaultValues"></a> 4c. Spécifier des valeurs par défaut de sorte que le rapport s'exécute automatiquement  
 Vous pouvez spécifier une valeur par défaut pour chaque paramètre afin que le rapport s'exécute automatiquement.  
  
#### <a name="to-specify-a-default-value-from-a-dataset"></a>Pour spécifier une valeur par défaut à partir d'un dataset  
  
1.  Basculez en mode Conception.  
  
2.  Dans le volet des données de rapport, cliquez avec le bouton droit sur *@StoreID*, puis cliquez sur **Propriétés du paramètre**.  
  
3.  Cliquez sur **des valeurs par défaut**, puis cliquez sur **obtenir des valeurs à partir d’une requête**.  
  
4.  Dans la liste déroulante **Dataset**, cliquez sur **Stores**.  
  
5.  Dans la liste déroulante **Champ de valeur**, cliquez sur StoreID.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Affichez l'aperçu du rapport.  
  
 Pour *@StoreID*, la visionneuse de rapports affiche la valeur « Contoso North America Online Store ». Ceci est la première valeur du jeu de résultats pour le jeu de données **magasins**. Le rapport affiche la quantité vendue des articles « Digital Cameras » pour l’identificateur de magasin **199**.  
  
#### <a name="to-specify-a-custom-default-value"></a>Pour spécifier une valeur par défaut personnalisée  
  
1.  Basculez en mode Conception.  
  
2.  Dans le volet des données de rapport, cliquez avec le bouton droit sur *@StoreID*, puis cliquez sur **Propriétés du paramètre**.  
  
3.  Cliquez sur **des valeurs par défaut**, puis cliquez sur **spécifier des valeurs**, puis cliquez sur **ajouter**. Une nouvelle ligne de valeurs est ajoutée.  
  
4.  Dans **Valeur**, tapez **200**.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Affichez l'aperçu du rapport.  
  
 Pour *@StoreID*, la visionneuse de rapports affiche la valeur « Contoso Catalog Store ». C’est le nom d’affichage pour l’identificateur de magasin **200**. Le rapport affiche les quantités vendues des articles « Accessories », « Camcorders » et « Digital SLR Cameras » pour l’identificateur de magasin **200**.  
  
##  <a name="NameValue"></a> 4d. Rechercher une valeur à partir d'un dataset qui contient des paires nom/valeur  
 Un dataset peut contenir à la fois l'identificateur et le champ Nom correspondant. Lorsque vous avez seulement un identificateur, vous pouvez rechercher le nom correspondant dans un dataset que vous avez créé et qui inclut des paires nom/valeur.  
  
#### <a name="to-look-up-a-value-from-a-dataset"></a>Pour rechercher une valeur dans un dataset  
  
1.  Basculez en mode Conception.  
  
2.  Dans l’aire de conception, dans la matrice, dans le premier en-tête de ligne ou de colonne, cliquez avec le bouton droit sur `[StoreID]` , puis cliquez sur **Expression**.  
  
3.  Dans le volet Expression, supprimez tout le texte sauf le signe `equals` (=) de début.  
  
4.  Dans **Catégorie**, développez **Fonctions communes**, puis cliquez sur **Divers**. Le volet Élément affiche un ensemble de fonctions.  
  
5.  Dans Élément, double-cliquez sur **Recherche**. Le volet Expression affiche `=Lookup(`. Le volet d'exemple affiche un exemple de syntaxe de recherche.  
  
6.  Tapez l’expression suivante : `=Lookup(Fields!StoreID.Value,Fields!StoreID.Value,Fields!StoreName.Value,"Stores")`  
  
     La fonction de recherche prend la valeur de StoreID, la recherche dans le dataset « Stores », puis retourne la valeur StoreName.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     L’en-tête de colonne de magasin contient le texte affiché pour une expression complexe : **<\<Expr >>**.  
  
8.  Affichez l'aperçu du rapport.  
  
 La zone de texte en haut de chaque page affiche le nom de magasin au lieu de l'identificateur de magasin.  
  
##  <a name="Expression"></a> 5. Afficher la valeur de paramètre sélectionnée dans le rapport  
 Lorsqu'un utilisateur a des questions sur un rapport, il est utile de connaître les valeurs de paramètres qu'il a choisies. Vous pouvez conserver les valeurs sélectionnées par l'utilisateur pour chaque paramètre du rapport. L'une des solutions possibles consiste à afficher les paramètres dans une zone de texte au sein du pied de page.  
  
#### <a name="to-display-the-selected-parameter-value-and-label-on-a-page-footer"></a>Pour afficher la valeur du paramètre sélectionné et son étiquette dans un pied de page  
  
1.  Basculez en mode Conception.  
  
2.  Cliquez sur le pied de page, pointez sur **insérer**, puis cliquez sur **zone de texte**. Faites glisser la zone de texte en regard de la zone de texte comportant l'horodatage. Saisissez la poignée latérale de la zone de texte et augmentez la largeur de cette dernière.  
  
3.  Dans le volet des données de rapport, faites glisser le paramètre *@StoreID* vers la zone de texte. La zone de texte affiche `[@StoreID]`.  
  
4.  Pour afficher l'étiquette de paramètre, cliquez dans la zone de texte jusqu'à ce que le curseur d'insertion s'affiche après l'expression existante, tapez un espace, puis faites glisser une autre copie du paramètre du volet des données de rapport vers la zone de texte. La zone de texte affiche `[@StoreID] [@StoreID]`.  
  
5.  Avec le bouton droit de la première expression et cliquez sur **Expression**. La boîte de dialogue **Expression** s'affiche. Remplacez le texte `Value` par `Label`.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Le texte affiche : `[@StoreID.Label] [@StoreID]`.  
  
7.  Affichez l'aperçu du rapport.  
  
##  <a name="Filter"></a> 6. Utiliser le paramètre de rapport dans un filtre  
 Les filtres permettent de contrôler les données à utiliser dans un rapport une fois qu'il a été récupéré à partir d'une source de données externe. Pour fournir à un utilisateur la possibilité de contrôler les données qu'il souhaite afficher, vous pouvez inclure le paramètre de rapport dans un filtre pour la matrice.  
  
#### <a name="to-specify-a-parameter-in-a-matrix-filter"></a>Pour spécifier un paramètre dans un filtre de matrice  
  
1.  Basculez en mode Conception.  
  
2.  Cliquez avec le bouton droit sur une ligne ou un descripteur d’en-tête de colonne dans la matrice, puis cliquez sur **Propriétés du tableau matriciel**.  
  
3.  Cliquez sur **Filtres**, puis sur **Ajouter**. Une nouvelle ligne de filtres apparaît.  
  
4.  Dans la liste déroulante **Expression**,, sélectionnez le champ de dataset StoreID. Le type de données affiche **Entier**. Lorsque la valeur d'expression est un champ de dataset, le type de données est défini automatiquement.  
  
5.  Dans **opérateur**, vérifiez que `equals` (=) est sélectionné.  
  
6.  Dans **Valeur**, tapez `[@StoreID]`. `[@StoreID]` est la syntaxe d’expression simple qui représente `=Parameters!StoreID.Value`.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  Affichez l'aperçu du rapport.  
  
     La matrice affiche des données uniquement pour « Contoso Catalog Store ».  
  
9. Dans la barre d’outils de la visionneuse de rapports, pour **Nom du magasin ?**, sélectionnez **Contoso Asia Online Store**, puis cliquez sur **Afficher le rapport**.  
  
 La matrice affiche les données qui correspondent au magasin que vous avez sélectionné.  
  
##  <a name="Multivalued"></a> 7. Modifier le paramètre de rapport pour accepter plusieurs valeurs  
 Pour changer un paramètre à valeur unique en paramètre à valeurs multiples, vous devez modifier la requête, ainsi que toutes les expressions qui contiennent une référence au paramètre, notamment les filtres. Un paramètre à valeurs multiples est un tableau de valeurs. Dans une requête de dataset, la syntaxe de requête doit tester l'inclusion d'une valeur dans un ensemble de valeurs. Dans une expression de rapport, la syntaxe d'expression doit accéder à un tableau de valeurs au lieu d'une valeur individuelle.  
  
#### <a name="to-change-a-parameter-from-single-to-multivalued"></a>Pour changer un paramètre à valeur unique en paramètre à valeurs multiples  
  
1.  Basculez en mode Conception.  
  
2.  Dans le volet des données de rapport, cliquez avec le bouton droit sur *@StoreID*, puis cliquez sur **Propriétés du paramètre**.  
  
3.  Sélectionnez **Autoriser les valeurs multiples**.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  Dans le volet des données de rapport, développez le dossier **Datasets** , cliquez avec le bouton droit sur **DataSet1**, puis cliquez sur **Requête**.  
  
6.  Modification `equals` (=) à `IN` dans le [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE` clause dans la dernière ligne dans la requête :  
  
    ```  
    WHERE StoreID IN (@StoreID)  
    ```  
  
     L'opérateur `IN` teste l'inclusion d'une valeur dans un ensemble de valeurs.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  Cliquez avec le bouton droit sur une ligne ou un descripteur d’en-tête de colonne dans la matrice, puis cliquez sur **Propriétés du tableau matriciel**.  
  
9. Cliquez sur **Filtres**.  
  
10. Dans **Opérateur**, sélectionnez **In**.  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. Dans la zone de texte qui affiche le paramètre au sein du pied de page, supprimez l'ensemble du texte.  
  
13. Cliquez avec le bouton droit sur la zone de texte, puis cliquez sur **Expression**. Tapez l’expression suivante : `=Join(Parameters!StoreID.Label, ", ")`  
  
     Cette expression concatène tous les noms de magasins que l'utilisateur a sélectionnés.  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
15. Cliquez dans la zone de texte devant l'expression que vous venez de créer, puis tapez ce qui suit :  Valeurs de paramètres sélectionnées :.  
  
16. Affichez l'aperçu du rapport.  
  
17. Cliquez sur la liste déroulante en regard de Nom du magasin ?  
  
     Chaque valeur valide s'affiche en regard d'une case à cocher.  
  
18. Cliquez sur **Sélectionner tout**, puis sur **Afficher le rapport**.  
  
     Le rapport affiche les quantités vendues pour toutes les sous-catégories de tous les magasins.  
  
19. Dans la liste déroulante, cliquez sur **Sélectionner tout** afin d’effacer la liste, cliquez sur « Contoso Catalog Store » et sur « Contoso Asia Online Store », puis cliquez sur **Afficher le rapport**.  
  
##  <a name="Boolean"></a> 8. Ajouter un paramètre booléen pour la visibilité conditionnelle  
  
#### <a name="to-add-a-boolean-parameter"></a>Pour ajouter un paramètre booléen  
  
1.  Dans l’aire de conception, dans le volet des données de rapport, cliquez avec le bouton droit sur **Paramètres**, puis cliquez sur **Add Ajouter un paramètre**.  
  
2.  Dans la zone **Nom**, tapez ShowSelections.  
  
3.  Dans **Invite**, tapez Afficher les sélections ?  
  
4.  Dans **type de données**, dans la liste déroulante, cliquez sur **booléenne**.  
  
5.  Cliquez sur **Valeurs par défaut**.  
  
6.  Cliquez sur **Spécifier les valeurs**, puis sur **Ajouter**.  
  
7.  Dans la zone **Valeur**, tapez **False**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-set-visibility-based-on-a-boolean-parameter"></a>Pour définir la visibilité en fonction d'un paramètre booléen  
  
1.  Dans l’aire de conception, cliquez avec le bouton droit sur la zone de texte du pied de page qui affiche les valeurs de paramètres, puis cliquez sur **Propriétés de la zone de texte**.  
  
2.  Cliquez sur **Visibilité**.  
  
3.  Sélectionnez l’option **Afficher ou masquer en fonction d’une expression**, puis cliquez sur le bouton Expression **Fx**.  
  
4.  Tapez l’expression suivante : `=Not Parameters!ShowSelections.Value`  
  
     L'option de visibilité de la zone de texte est contrôlée par la propriété Hidden. Appliquez l'opérateur `Not` afin que lorsque le paramètre est sélectionné, la valeur False soit affectée à la propriété Hidden et que la zone de texte soit affichée.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Affichez l'aperçu du rapport.  
  
     La zone de texte qui affiche les choix de paramètre ne s'affiche pas.  
  
8.  Dans la barre d’outils de la visionneuse de rapports, à côté **afficher les sélections**, cliquez sur `True`.  
  
9. Affichez l'aperçu du rapport.  
  
 La zone de texte située dans le pied de page affiche tous les noms de magasins que vous avez sélectionnés.  
  
##  <a name="Title"></a> 9. Ajouter un titre de rapport  
  
#### <a name="to-add-a-report-title"></a>Pour ajouter un titre de rapport  
  
1.  Dans l'aire de conception, cliquez sur **Cliquez pour ajouter un titre**.  
  
2.  Tapez Ventes de produits paramétrables, puis cliquez en dehors de la zone de texte.  
  
##  <a name="Save"></a> 10. Enregistrer le rapport  
  
#### <a name="to-save-the-report-on-a-report-server"></a>Pour enregistrer le rapport sur un serveur de rapports  
  
1.  À partir du bouton **Générateur de rapports** , cliquez sur **Enregistrer sous**.  
  
2.  Cliquez sur **Sites et serveurs récents**.  
  
3.  Sélectionnez ou tapez le nom du serveur de rapports sur lequel vous êtes autorisé à enregistrer des rapports.  
  
     Le message **Connexion au serveur de rapports**s’affiche. Une fois la connexion établie, le contenu du dossier de rapports spécifié par l'administrateur du serveur de rapports s'affiche comme emplacement par défaut des rapports.  
  
4.  Dans la zone **Nom**, remplacez le nom par défaut par État des ventes paramétrable.  
  
5.  Cliquez sur **Enregistrer**.  
  
 Le rapport est enregistré sur le serveur de rapports. Le serveur de rapports auquel vous êtes connecté est indiqué dans la barre d'état située au bas de la fenêtre.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Ceci conclut la procédure pas à pas décrivant comment ajouter un paramètre à votre rapport. Pour en savoir plus sur les paramètres, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](report-design/report-parameters-report-builder-and-report-designer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels &#40;Générateur de rapports&#41;](report-builder-tutorials.md)   
 [Générateur de rapports dans SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
